# Defensibility

> What Dynazme still wins on when an obvious foreign incumbent ships an obvious feature.

---

## The honest framing

A Thai AI engineering boutique does not have a product moat in the textbook sense. Dynazme cannot out-research Anthropic, out-distribute Microsoft, or out-spend AWS. Anyone claiming otherwise is selling.

What Dynazme can do — and the only basis on which it builds — is be **specifically right** about a market that those incumbents are **generically wrong** about.

This document records what "specifically right" means here.

---

## Five things that compound

### 1. Thai-language depth, not Thai-language translation

Foreign vendors translate UI to Thai. They do not tune retrieval, classification, or generation for Thai legal phrasing, Thai institutional vocabulary, or the way a Thai SOP is actually written.

The gap is biggest where it matters most: legal documents, healthcare records, government forms, and multi-paragraph Thai narrative where word-level segmentation matters.

Dynazme's retrieval and OCR pipelines are tuned against Thai-domain corpora. The performance gap on real customer documents is large enough that a customer doing a side-by-side bake-off can see it without being told.

### 2. Thai institutional fluency

Selling AI to a Thai mid-market firm is not a product demo. It is a series of conversations involving the founder/MD, the operations director, the IT outsource partner, the existing accounting platform's account manager, and — eventually — a compliance officer who has to answer a PDPC inspection.

Foreign vendors run this conversation in English, by phone, with a Singapore-shifted overlap window. Dynazme runs it in Thai, in person where it matters, with someone who has read the actual ก.ล.ต. circular.

This is not a moat that scales to 10,000 customers. It is a moat that lets Dynazme close the first 30 customers a foreign vendor will never reach.

### 3. PDPA-as-default, not PDPA-as-bolt-on

A Thai customer's compliance officer will ask, in the first 20 minutes:

- Where does the data sit?
- What's logged, and for how long?
- What does cross-border transfer look like under Section 28?
- What happens to the data if the customer terminates?

Dynazme has answers built into the architecture from day one. ([`docs/compliance/thai-frameworks.md`](./compliance/thai-frameworks.md).)

Foreign vendors send the customer to a 40-page DPA, which the compliance officer reads, dislikes, and forwards to legal — at which point the procurement cycle adds three months.

### 4. Engagement model that removes vendor risk

Dynazme engagements start with a scoped pilot bound by a measurable success metric, with a clean walk-away clause if the metric is not hit. Customers pay only the agreed pilot fee for an engagement that doesn't convert.

Foreign vendors structure first engagements as annual licences with three-year auto-renew. The Thai mid-market does not buy that. They will, however, buy a 6-week pilot with a real exit door.

This is not a moat against the foreign vendor's product. It is a moat against the foreign vendor's **contract**.

### 5. Founder accountability

Dynazme is a small, named team. The founder reads every customer email. Engagements include direct access to the engineer who wrote the integration. Customers know who to call when something breaks.

This stops being a moat at scale. It is a moat at the scale Dynazme is being built for — and where Dynazme is competing in 2026, scale is not the question.

---

## What is not a moat

To stay honest, here is what Dynazme is **not** going to claim as defensible:

- **Proprietary models.** We do not train foundation models. We use Claude, GPT-class, and open-source. So does everyone else.
- **Proprietary algorithms.** Hybrid retrieval, OCR preprocessing, RAG verifiers — all are well-understood patterns. Our advantage is in the tuning, not the invention.
- **Network effects.** Dynazme's customer base does not benefit other customers in any technical sense.
- **Switching costs through lock-in.** We will not architect for proprietary data formats or contractual lock-in. Customers should be able to leave.
- **Brand strength.** No brand strength in 2026. Earned, slowly, by referenceable customers.
- **Patents.** Not pursuing.

---

## What happens when a foreign incumbent ships the feature

When (not if) Microsoft, Google, or AWS ships a Thai-localised AI tool that overlaps with a Dynazme product:

- **The tool will be 70% as good** on the Thai-language axis at the moment of launch.
- **The tool will not have a Thai-resident sales motion** for the mid-market segment Dynazme serves.
- **The tool's compliance posture will lag** the Thai regulatory floor by 12–18 months.
- **The tool will have an annual-licence contract** the Thai mid-market does not want to sign.

Dynazme's job, when this happens, is not to outclaim the incumbent. It is to:

1. Take the loss in segments where the incumbent is good enough
2. Hold the line in segments where Thai depth matters
3. Composability — make Dynazme tools work alongside the incumbent's where customers want both

If, at some milestone, the answer is "the incumbent has overtaken Dynazme on every axis at our price point" — that is a kill criterion. See [`ROADMAP.md`](../ROADMAP.md).

---

## Last revised

2026-05-07.
