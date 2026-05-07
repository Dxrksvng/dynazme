# Thai Compliance Frameworks — Mapping Reference

> Advisory, not legal opinion. Final regulatory determinations rest with the customer's counsel.
>
> การ map ข้างต้นเป็นเพียงคำแนะนำ การตีความข้อกฎหมายขั้นสุดท้ายอยู่ในดุลพินิจของที่ปรึกษากฎหมายของท่าน.

---

## Why this document exists

Dynazme builds AI systems for Thai businesses. Thai businesses operate under specific regulatory regimes that foreign vendors do not always take seriously. This document records — publicly — which frameworks Dynazme designs against, and where in the product the obligations land.

This is a planning artefact. It does not certify compliance.

---

## Personal Data Protection Act (PDPA) — พระราชบัญญัติคุ้มครองข้อมูลส่วนบุคคล พ.ศ. 2562

In force since 1 June 2022 (full enforcement). Administered by the Personal Data Protection Committee (PDPC) and supported by the Office of the Personal Data Protection Committee.

### Sections most directly applicable to Dynazme products

| Section | Subject | Where it lands in Dynazme products |
|---|---|---|
| 24 | Lawful basis for collection of personal data | Customer-side configuration: customer is data controller; Dynazme is data processor |
| 26 | Sensitive personal data (race, religion, biometric, health, etc.) | Refusal logic in DocuSense and FahMai when sensitive categories are detected without an explicit lawful basis flag |
| 27 | Use and disclosure of personal data | Audit trail records every disclosure pathway; default policy is no cross-purpose use |
| 28 | Cross-border transfer | Default deployment is Thai-region; cross-border processing is opt-in with documented adequacy basis |
| 30–37 | Data-subject rights (access, rectification, erasure, restriction, portability, objection, withdrawal of consent) | Operator surface exposes per-subject data export and deletion; retention windows are configurable per engagement |
| 39 | Record of processing activities | Audit trail is the system of record; logs are exportable in PDPC-acceptable format |
| 41 | Data Protection Officer | Customer's responsibility; Dynazme provides processing-record artefacts the DPO can use |

### What Dynazme does in practice

- Customer data is stored in Thai-region cloud or on customer infrastructure by default.
- Logs distinguish "operational" data (system telemetry) from "personal" data (subject-identifiable). Operational logs are retained longer; personal-data logs are retained only for the engagement-specific retention window.
- Cross-border processing (e.g. routing a query to a foreign LLM provider) is documented in the engagement contract with the lawful-basis declaration.
- A data-subject deletion request, when received from the customer-controller, propagates through Dynazme storage and triggers re-anonymisation of any derived artefacts where technically feasible.

### Known limits

- Foundation-model providers (Anthropic, OpenAI) do not give Dynazme byte-level guarantees about their training-data isolation. Customers with the strictest data-residency requirements should run with self-hosted open-source models — supported, with reduced capability.

---

## ก.ล.ต. — Securities and Exchange Commission Thailand

Applicable when a Dynazme product is used in:

- Robo-advisory or model-portfolio recommendation flows
- Suitability assessment or KYC enrichment
- AI-driven trading or trade-surveillance pipelines

### Where Dynazme designs against ก.ล.ต. expectations

- Robo-advisor disclosure: BI Agent and FahMai outputs delivered into a regulated advisory context carry an "AI-generated, model identifier, evidence trail" disclosure block by default.
- Suitability assessment: any use of a Dynazme tool to score suitability is rule-based and human-reviewed; auto-classification is refused.
- Trade execution: Dynazme will not auto-execute trades. See [`SAFETY.md`](../../SAFETY.md).

### What Dynazme does not claim

- We do not hold a ก.ล.ต. licence and we do not claim regulatory approval for our outputs.
- A regulated firm using Dynazme tooling remains the regulated entity; ก.ล.ต. compliance is the firm's responsibility.

---

## ธปท. — Bank of Thailand

Applicable when a Dynazme product is used in:

- A licensed financial institution's customer authentication flow
- Cloud / outsourcing arrangements requiring BOT notification (per IT-risk-management notifications)
- Suspicious-transaction detection or AML triage

### Where Dynazme designs against BOT expectations

- IT risk management: deployment artefacts carry an inventory of dependencies (foundation-model vendors, vector stores, observability stack) suitable for BOT cloud-outsourcing notification.
- Customer authentication: Dynazme will not be a primary authentication factor; it composes with a financial institution's existing authentication stack.
- Suspicious-transaction trail: every customer-affecting decision carries a tamper-evident audit log. Hash-chained log export is available for engagements that require it.

### What Dynazme does not claim

- We are not a BOT-supervised institution. Engagements with BOT-supervised customers run as a vendor relationship under that customer's IT-risk framework.

---

## OWASP LLM Top 10 (v1.1, 2024)

The OWASP LLM Top 10 names ten classes of failure mode common to LLM applications. Dynazme designs against each:

| Category | Dynazme posture |
|---|---|
| LLM01 — Prompt Injection | Untrusted-content boundaries enforced; retrieved documents treated as data, not instructions |
| LLM02 — Insecure Output Handling | LLM outputs are validated against expected schemas before being acted on |
| LLM03 — Training Data Poisoning | We do not train foundation models; reference vector stores are sourced and hashed |
| LLM04 — Model Denial of Service | Per-customer rate limits, query-cost ceilings, fallback to cheaper models on overload |
| LLM05 — Supply Chain Vulnerabilities | Pinned dependencies; secret and dependency scans on every push |
| LLM06 — Sensitive Information Disclosure | Refusal logic when retrieval would expose sensitive categories without lawful basis |
| LLM07 — Insecure Plugin Design | We do not ship community plugin marketplaces; integrations are first-party and reviewed |
| LLM08 — Excessive Agency | No auto-execution of consequential actions without explicit human confirm |
| LLM09 — Overreliance | Disclosure block on AI-generated outputs makes the operator's review obligation explicit |
| LLM10 — Model Theft | Customer prompts and embeddings are not exposed beyond the engagement boundary |

---

## ISO/IEC 27001 — Information Security Management

Targeted post-Phase-3. Not claimed today. Engagements that require ISO 27001 attestation today should engage an attested vendor.

When Dynazme pursues attestation, the controls vocabulary will be back-mapped here.

---

## ISO/IEC 42001 — AI Management System

Not pursued in 2026. Will be reconsidered when:

- Dynazme has ≥3 customers requesting AI-management-system evidence
- Annex III obligations of the EU AI Act create market demand for a 42001 line item
- Dynazme has the operational maturity to make the attestation cost-effective

---

## EU AI Act — Regulation (EU) 2024/1689

Out of scope for the Thai-domestic engagement model. Customers with EU subsidiaries or extraterritorial exposure should engage a vendor with explicit EU AI Act readiness.

Dynazme will reconsider when:

- A Thai mid-market customer with EU exposure asks specifically for AI-Act readiness
- The Annex III enforcement window (2026-08-02) has been in force long enough that real procurement language exists

---

## Last revised

2026-05-07.
