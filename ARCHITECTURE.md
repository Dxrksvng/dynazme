# Architecture

> Public, high-level. Implementation-level architecture lives in the private repository.

---

## How the four products compose

Dynazme's four product lines are not four standalone products. They are four building blocks that share a common foundation and can be assembled into customer-specific solutions.

```
┌──────────────────────────────────────────────────────────────────────────┐
│                          CUSTOMER SURFACE                                │
│  LINE OA · Web chat · Email · Sheets · ERP · Custom front-end            │
└──────────────────────────────┬───────────────────────────────────────────┘
                               │
┌──────────────────────────────▼───────────────────────────────────────────┐
│                       FLOWFORGE — Workflow Runtime                       │
│  Composes the building blocks below into a customer-specific workflow.   │
└──────────┬──────────────┬──────────────┬─────────────────────────────────┘
           │              │              │
   ┌───────▼─────┐  ┌─────▼──────┐  ┌────▼──────────┐
   │  FahMai     │  │ DocuSense  │  │  BI Agent     │
   │  Thai RAG   │  │ Thai OCR   │  │  Data → Slide │
   └───────┬─────┘  └─────┬──────┘  └────┬──────────┘
           │              │              │
┌──────────▼──────────────▼──────────────▼─────────────────────────────────┐
│                       SHARED FOUNDATION                                  │
│                                                                          │
│  · LLM gateway (Claude / GPT / open-source Thai models, provider-agnostic)│
│  · Retrieval primitives (BM25 + dense + RRF + reranker)                  │
│  · Document-aware preprocessing (rotation, unwarping, segmentation)      │
│  · Evaluation harness (RAGAS-style, golden tests, regression suite)      │
│  · Audit + observability (structured logs, evidence export, PDPA trail)  │
└──────────────────────────────────────────────────────────────────────────┘
```

A customer rarely buys all four. The most common shapes are:

- **FahMai-only** — internal knowledge Q&A bot.
- **DocuSense → FahMai** — digitise legacy documents, then make them searchable.
- **DocuSense → FlowForge** — receipts in, accounting entries out.
- **FahMai → BI Agent** — Q&A over data, then formal monthly review.
- **All four via FlowForge** — full operations workflow (the long tail of customer-specific shapes).

---

## Design principles

### 1. Provider-agnostic, not provider-locked

Every LLM call goes through an internal gateway. We use Claude as the default, with fallbacks to GPT-class and open-source Thai models depending on the task and the customer's data-residency requirements. No Dynazme product is hard-coded to one model vendor.

### 2. Retrieval-grounded by default

Every customer-facing answer is grounded in retrieved evidence with citations. When retrieval confidence is below threshold, the system refuses or escalates rather than confabulates. "It looked plausible" is not a sufficient correctness bar.

### 3. Compute-in-code, narrate-with-LLM

Numbers, dates, and statistics are computed in deterministic code. The LLM is responsible for narrative and structure. This is the BI Agent pattern; it is also the rule for any product surfacing a number.

### 4. Audit trail is non-optional

Every customer-affecting decision (retrieval, classification, automated action) is logged with inputs, outputs, model identifier, and timestamp. PDPA Section 39 obligations are not retrofitted.

### 5. Observability before scale

Before a workflow goes to production, we wire structured logging, latency metrics, and an evidence export. Before adding capacity, we read the logs.

### 6. Customer data does not leave Thailand without explicit consent

Default deployment is Thai-region cloud (GCP `asia-southeast1`, AWS `ap-southeast-7`, or self-hosted on customer infrastructure). Cross-border processing is opt-in per Section 28 of PDPA.

---

## Stack choices (current defaults)

| Layer | Default | Why |
|---|---|---|
| Language (services) | Python 3.12 | LLM ecosystem, Thai NLP libraries |
| Web framework | FastAPI | Async-first, type-safe, Pydantic-native |
| Front-end | Next.js 15 / Vue 3 | Customer choice; both are supported |
| Vector DB (dev) | ChromaDB / Qdrant local | Zero-config for prototyping |
| Vector DB (prod) | Qdrant Cloud / pgvector | Managed for small teams; Postgres-native for teams that already operate Postgres |
| Object store | S3-compatible | Customer-cloud-resident |
| LLM provider | Anthropic Claude (default), OpenAI, open-source via Ollama | Per-task selection |
| Thai NLP | PyThaiNLP, Typhoon-LLM | Thai-tuned where it matters |
| Observability | structlog → Grafana Loki, Sentry, Langfuse | Logs / errors / LLM traces |
| Deployment | Docker → GCP Cloud Run / Fly.io / customer self-host | Per engagement |

These are defaults, not religion. Customer constraints override.

---

## What is intentionally not in this document

- Specific prompts, retrieval parameters, and reranking weights — those are the result of customer-specific tuning and the meaningful intellectual property.
- Wire-level schemas — those are versioned in the private repository.
- Customer-named architectures — never published.
- Performance benchmarks — published only when reproducible against an open dataset.

---

## How this document is maintained

- Public architecture changes are committed here as the position changes.
- Private architecture changes are not back-ported.
- A change in this document is a signal that customer reality moved.
