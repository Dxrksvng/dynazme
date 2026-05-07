# Security

> Vulnerability disclosure policy for Dynazme — public-repository scope.

---

## Scope

This policy covers:

- The public repository at `github.com/Dxrksvng/dynazme`.
- Public-facing properties operated by Dynazme (`dynazme.com` and subdomains, where deployed).
- Issues affecting Dynazme products that arise from the public planning artefacts in this repository (e.g. a documented architecture pattern that has a fundamental flaw).

This policy does **not** cover:

- Customer engagements. Findings affecting a customer engagement should be reported through the customer's own channel — the engagement owner will route appropriately.
- Third-party services Dynazme integrates with (Anthropic, OpenAI, GCP, AWS, etc.) — report to the relevant vendor.
- Findings that require an active customer environment to reproduce — those go through the customer's incident channel.

---

## Reporting a vulnerability

For findings in scope:

- **Email**: `dxrksvng@gmail.com` with subject prefix `SECURITY:`
- **Encryption**: PGP key available on request

Please include:

- A description of the issue and its potential impact.
- Steps to reproduce, or a proof-of-concept where appropriate.
- Any draft remediation suggestion (optional but appreciated).
- Whether you intend to publish the finding, and on what timeline.

---

## What to expect

- **Acknowledgement** within one business day.
- **Initial triage** within five business days. We will tell you whether we accept the finding as a vulnerability, whether more information is needed, or whether the finding is out of scope.
- **Remediation timeline** depends on severity. We aim for:
  - Critical (active exploitation possible, customer-impact severe) — 24–72 hours.
  - High — within 14 days.
  - Medium — within 30 days.
  - Low / informational — addressed in the next planning cycle, or accepted as known.
- **Coordinated disclosure** — we will agree a disclosure date with the reporter. Default is 90 days from acknowledgement, or sooner if the issue is resolved earlier.
- **Credit** — reporters who follow this policy and request credit will be acknowledged in the resolution notes (handle, GitHub username, or anonymous, per your preference).

---

## What we ask

- Do not access, modify, or destroy data that is not yours during research.
- Do not run automated scanning that would degrade availability.
- Do not pivot from a finding into customer environments — engagements live in private infrastructure that is not in scope for this policy.
- Do not publicly disclose a finding before the agreed coordinated-disclosure date.

Researchers who follow this policy will not have legal action initiated against them by Dynazme for the activity described here. We will treat reports in good faith.

---

## Out-of-scope findings

The following are explicitly out of scope and will be closed without action:

- Missing security headers on documentation domains where no authentication or sensitive data is involved.
- "Email spoofing is possible" reports against a domain that does not send authenticated email.
- Theoretical findings that depend on a user being phished or otherwise socially engineered before any Dynazme system is exposed.
- Self-XSS that requires the user to paste an attacker-supplied payload into their own browser console.
- Volumetric / DoS findings without a working proof of impact.

---

## Hardware, model-vendor, and AI-specific findings

For AI-specific findings (prompt injection that bypasses a Dynazme-defined refusal, retrieval-time data exfiltration, model-vendor disclosure), include:

- The Dynazme product affected (FahMai / DocuSense / BI Agent / FlowForge).
- Whether the issue is in Dynazme's design, in our prompt layer, or in a downstream model vendor.
- A failure mode expressed in terms a non-AI-specialist auditor can recognise.

If the underlying failure is in the foundation model, we will help coordinate disclosure with the model vendor — but the vendor's own coordinated-disclosure policy will apply to that part.

---

## Last revised

2026-05-07.
