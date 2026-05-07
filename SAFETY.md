# Safety

> Anti-hallucination posture, self-imposed limits, and the things Dynazme refuses to ship even if a customer asks.

---

## Why this document exists

The most common AI-product failure mode in 2026 is not a malicious prompt. It is a confident wrong answer in a context where the operator was not equipped to recognise it as wrong.

This document records, publicly, the things Dynazme will and will not do — so a customer (or a future Dynazme team member) can hold the founder accountable if a future shortcut tempts otherwise.

---

## What Dynazme builds towards

### 1. Retrieval-grounded answers, not free-form generation

Customer-facing Q&A products produce answers grounded in retrieved evidence. Every answer is accompanied by a citation set the operator can inspect.

When retrieval confidence is below threshold, the system **refuses** or **escalates** rather than generates a plausible-sounding fabrication. Refusing is not a failure mode; confabulating is.

### 2. Compute-in-code, narrate-with-LLM

Numbers, dates, statistics, and any quantity an executive or auditor would act on are computed in deterministic code. The LLM is responsible for narrative structure and style only.

This rule applies most strictly to BI Agent, but extends to every product that surfaces a number to a customer.

### 3. Verifier passes before release

Customer-affecting outputs pass through a verifier before they are surfaced. The verifier checks specific failure modes: numerical hallucination, citation drift, date/period mismatch, and unsupported claims.

A verifier failure halts the output. It does not paper over it.

### 4. Audit trail by default

Every customer-affecting decision (retrieval, classification, automated action) is logged with inputs, outputs, model identifier, and timestamp. The trail is exportable for PDPA, regulatory, or customer-internal review.

### 5. Refusal as a first-class capability

Where a question falls outside scope, contradicts the customer's own policy, or requires judgement Dynazme is not authorised to make, the system refuses and routes the conversation to a human.

---

## What Dynazme will not build

These are not "we'll build it later if asked" — these are bright lines.

### 1. We will not auto-classify legal or financial risk

Risk-tier classification is a single point of catastrophic miscategorisation. Dynazme tools surface evidence and flag candidate tiers; the final classification is made by a human with authority to be wrong.

### 2. We will not auto-execute financial transactions

No trading bot. No auto-debit. No "AI agent that books the order on the customer's behalf" without an explicit human confirm step.

### 3. We will not produce marketing claims about ourselves the system cannot verify

If Dynazme claims a benchmark, a customer count, or a compliance certification, the artefact backing the claim must exist and be reproducible by an auditor. "Look credible enough to close" is not a goal that justifies overclaim.

### 4. We will not train on customer data without explicit consent

Customer documents, prompts, and conversations are processed for inference and audit only. They do not enter any training pipeline — Dynazme's, the foundation-model vendor's, or a third party's — unless the customer has explicitly opted in for a defined purpose.

### 5. We will not deploy to production without an evaluation harness

Every customer-facing feature ships with regression tests against a held-out evaluation set. Untested-in-the-wild deployments are not how Dynazme delivers.

### 6. We will not skip refusal logic to "improve user experience"

Refusing a low-confidence answer feels worse than confabulating one. We will never optimise for the feel-good metric here.

### 7. We will not accept engagements that require us to hide capability limits from end-users

If a system is going to make decisions that affect a person's money, employment, or healthcare, that person has the right to know an AI was involved and to ask for human review. Engagements that require us to hide this are declined.

---

## What Dynazme is not

Equally important — the things Dynazme is **not** trying to be:

- **Not a frontier-AI alignment lab.** Existential AI safety is a real field with serious researchers; we are not them. We make production AI more governable, not safe in the existential sense.
- **Not a safety auditor.** Dynazme builds and deploys AI; it is not a third-party assurance body. Customers needing third-party assurance should engage one.
- **Not a guarantor.** The operator deploying Dynazme tooling makes the final call on whether the system is safe enough for their use case. We provide the tools, evidence, and posture to make that call well; we do not absorb it.

---

## Reporting safety concerns

If a Dynazme product produced an output that you believe is unsafe, hallucinated, or violated one of the principles in this document:

- **Customer-context findings** — contact the engagement owner directly (the person who delivered the engagement).
- **Public-context findings** — open a GitHub issue on this repository describing the failure mode, the input that triggered it, and the output produced. Do not include personal data or customer-identifiable information.
- **Security-sensitive findings** (data leakage, prompt injection enabling unauthorised access) — see [`SECURITY.md`](./SECURITY.md). Do not use the public issue tracker.

Reports that surface a real failure mode will be acknowledged within one business day and addressed.
