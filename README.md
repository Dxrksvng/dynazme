# Dynazme

> **Production-grade AI engineering for Thai SMEs.**
>
> Thai-language RAG, document intelligence, BI automation, and workflow tooling — built for the businesses foreign AI products price out and big consultancies overlook.

---

| | |
|---|---|
| **Status** | Pre-revenue · active development · solo founder |
| **Stage** | Phase 0 — customer discovery |
| **Founded** | 2026-04 |
| **Last updated** | 2026-05-07 |
| **Customers** | None yet — currently in problem-validation phase |
| **Funding** | Self-funded |
| **Location** | Thailand |

---

## ⚠️ Repository Scope

This repository contains public planning, product positioning, and development progress for Dynazme.

The implementation source — RAG pipelines, OCR models, automation engine, and customer-specific work — lives in a private repository. This is intentional, to:

- protect customer data and engagement-specific work
- prevent unmaintained code from being copy-pasted into production by people we never spoke to
- keep the founder's runway focused on customer conversations, not open-source maintenance

Code may be progressively published where it's genuinely reusable and not customer-coupled. Until then, public ≠ open source.

### What's public

- This README (positioning + status)
- [`PRODUCTS.md`](./PRODUCTS.md) — the four product lines
- [`ARCHITECTURE.md`](./ARCHITECTURE.md) — how the products fit together
- [`ROADMAP.md`](./ROADMAP.md) — phase plan + kill criteria
- [`PROGRESS.md`](./PROGRESS.md) — session-by-session build log
- [`VISION.md`](./VISION.md) — long-term ambition
- [`SAFETY.md`](./SAFETY.md) — anti-hallucination stance, self-imposed limits
- [`SECURITY.md`](./SECURITY.md) — vulnerability disclosure policy
- [`CONTRIBUTING.md`](./CONTRIBUTING.md) — how (and when) to contribute
- [`docs/compliance/thai-frameworks.md`](./docs/compliance/thai-frameworks.md) — PDPA / ก.ล.ต. / ธปท. mapping reference
- [`docs/DEFENSIBILITY.md`](./docs/DEFENSIBILITY.md) — what Dynazme still wins on when foreign incumbents ship the obvious feature

### What's not public

- Implementation source for all four product lines
- Customer-specific configurations, prompts, and datasets
- Pricing, proposal templates, and contract terms
- Customer-discovery toolkit, target lists, and call notes
- Internal financial targets and runway model

---

## What Dynazme is

Dynazme is a **boutique AI engineering firm** for Thai SMEs and mid-market enterprises.

Three things, only three things, well:

1. **Build** — production-grade AI systems for specific business problems, not generic chatbots.
2. **Localise** — Thai language, Thai documents, Thai compliance baked in, not bolted on.
3. **Stay accountable** — no AI demo theatre, no vapour pricing, no "we'll figure out PDPA later".

Everything else is intentionally out of scope. We don't sell licences for off-the-shelf AI tools, we don't run resold infrastructure, and we don't pretend to be a frontier-AI lab.

---

## Why this exists

Three groups of Thai businesses currently fall through the gaps:

- **SMEs** — priced out of foreign AI SaaS at $50/seat/month. Would adopt AI tooling if it spoke Thai and cost ฿20K/month, not ฿200K.
- **Mid-market enterprises** — under-served by big consultancies that quote ฿500K+ setup for any AI project, and over-sold by foreign vendors whose products silently fail on Thai documents.
- **Compliance officers** — answerable for AI behaviour their tools weren't designed to log, with PDPA obligations the foreign vendors don't take seriously.

Dynazme is being built to close those specific gaps — at a price that lets a 50-person Thai company adopt AI without writing the same cheque a 5000-person enterprise would.

---

## Where Dynazme sits in the AI delivery stack

```
Layer 5 — Frontier model labs (Anthropic, OpenAI, Google DeepMind)
Layer 4 — Foreign AI SaaS / global tools ($30–$200/seat/month)
Layer 3 — Big Thai consultancies (Bluebik, BCG Thailand)        ฿500K+ engagements
Layer 2 — Thai AI engineering boutiques               ◄── Dynazme  ฿80–400K engagements
Layer 1 — Freelancers / Fastwork                                  ฿20–80K projects
Layer 0 — In-house Thai engineering teams (Big-4 banks, telcos)
```

Dynazme **composes with** — never replaces — adjacent layers. We use Layer-5 models. We co-exist with Layer-4 tools where they already work. We do the work Layer-3 charges 4× as much for, and Layer-1 doesn't have the systems engineering for.

---

## Products

Four product lines. All are in active development; none has a paying customer yet.

| Product | What it does | Stage |
|---|---|---|
| **FahMai** | Thai-first RAG — search and Q&A over Thai documents | Reference implementation built (Super AI Hackathon ss6) · re-engineering in private repo |
| **BI Agent** | Data → executive presentation, automated | v2 prototype built · re-engineering in private repo |
| **DocuSense** | Thai document OCR — receipts, forms, exam papers | Senior-project foundation · productionising in private repo |
| **FlowForge** | End-to-end AI workflow automation, LINE OA / Email / Sheets / ERP | Skeleton scaffolded · awaiting first customer-driven scope |

Detail in [`PRODUCTS.md`](./PRODUCTS.md). Architecture overview in [`ARCHITECTURE.md`](./ARCHITECTURE.md).

---

## Compliance frameworks targeted

| Framework | Coverage |
|---|---|
| Thailand PDPA — พระราชบัญญัติคุ้มครองข้อมูลส่วนบุคคล พ.ศ. 2562 | Sections 24, 26, 27, 28, 30–37, 39, 41 |
| ก.ล.ต. (SEC Thailand) | Robo-advisor disclosure, suitability assessment — applies to BI Agent if used in regulated finance |
| ธปท. (Bank of Thailand) | IT risk management, cloud / outsourcing, customer authentication — applies to FlowForge integrations with banking customers |
| OWASP LLM Top 10 (v1.1, 2024) | LLM01 – LLM10 (prompt injection, training data poisoning, etc.) |
| ISO/IEC 27001 | Targeted post-Phase-3, not claimed today |

Mappings are advisory. Final regulatory determinations rest with your counsel — การ map ข้างต้นเป็นเพียงคำแนะนำ; การตีความข้อกฎหมายขั้นสุดท้ายอยู่ในดุลพินิจของที่ปรึกษากฎหมายของท่าน.

Detailed mapping reference in [`docs/compliance/thai-frameworks.md`](./docs/compliance/thai-frameworks.md).

---

## Engineering progress

- **Phase 0** (foundation) — ongoing. Public planning docs, private implementation repo, four product reference codebases curated and version-controlled.
- **Phase 1** (first paying customer) — gated on customer discovery. No code work begins on Phase 1 until ≥5 substantive customer-discovery conversations have surfaced consistent pain.

Session-by-session in [`PROGRESS.md`](./PROGRESS.md). Phase definitions and gates in [`ROADMAP.md`](./ROADMAP.md).

---

## Honest disclosures

Read this section. It is the difference between Dynazme and AI consulting theatre.

- We do **not** have paying customers. Dynazme is in customer-validation phase.
- We do **not** train our own foundation models. We integrate Claude, GPT-class, and open-source Thai models — we are an integration and product company, not a frontier lab.
- We do **not** claim "zero hallucination". We design for retrieval-grounded answers and evidence trails; final correctness is the operator's responsibility.
- We do **not** auto-classify legal or financial risk. Rule-based and human-reviewed risk tiers only.
- We do **not** hold SOC 2, ISO 27001, or ISO 42001 certifications. Those follow customer traction; claiming them pre-attestation would be fraud.
- We do **not** run customer data through training pipelines. Customer data is processed for inference and audit only.
- We are **not** Microsoft and we are **not** Bluebik. We don't have distribution; we have to win on depth in a niche, not breadth.
- We have **no** investors. Self-funded by the founder, runway-bounded.

Overclaiming AI capability is itself a safety failure — it leads operators to under-invest in real defences and over-invest in unproven tools. We will not.

---

## Documentation map

| Document | What it answers |
|---|---|
| [`PRODUCTS.md`](./PRODUCTS.md) | Four product lines and the problems each addresses |
| [`VISION.md`](./VISION.md) | What Dynazme is trying to become over 5 years |
| [`ARCHITECTURE.md`](./ARCHITECTURE.md) | High-level architecture: how the four products compose |
| [`ROADMAP.md`](./ROADMAP.md) | Phase-by-phase plan, definitions of done, kill criteria |
| [`PROGRESS.md`](./PROGRESS.md) | Session-by-session build log |
| [`SAFETY.md`](./SAFETY.md) | Anti-hallucination stance, self-imposed limits |
| [`SECURITY.md`](./SECURITY.md) | Vulnerability disclosure policy |
| [`CONTRIBUTING.md`](./CONTRIBUTING.md) | How (and when) to contribute |
| [`docs/compliance/thai-frameworks.md`](./docs/compliance/thai-frameworks.md) | PDPA / ก.ล.ต. / ธปท. mapping reference |
| [`docs/DEFENSIBILITY.md`](./docs/DEFENSIBILITY.md) | Why Dynazme still wins when foreign incumbents ship the obvious feature |

---

## License

All Rights Reserved. See [`LICENSE`](./LICENSE).

Examples and reference implementations published under different terms will be marked individually.

---

## Contact

### Who Dynazme is built for first

The first conversations are deliberately scoped. Dynazme is most useful, fastest, for organisations that fit this profile:

- **Geography**: Thailand (Bangkok / EEC / major provincial cities)
- **Size**: 30–500 employees
- **Sector**: SMEs and mid-market — equipment distributors, professional services, e-commerce, healthcare, finance back-office
- **Trigger**: a workflow taking >10 hours/week of repetitive document, Q&A, or reporting work — and a budget conversation that's already been had internally
- **Buyer**: founder, MD, ops director, or a department head with budget authority — not a procurement gatekeeper

If the situation broadly fits, ส่งมาคุยกันได้ครับ. If it doesn't, the implementation may still help, but the conversation is slower and the fit later.

### Channels

- **Email** — `dxrksvng@gmail.com` (Thai or English; respond within one business day)
- **GitHub Discussions** — coming soon (Phase 0 → 1 transition)
- **Security findings** — see [`SECURITY.md`](./SECURITY.md), do not use email or Discussions

External code contributions are not being accepted yet — focus is on customer validation.
