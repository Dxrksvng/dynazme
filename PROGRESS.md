# Progress

> Session-by-session build log. Public, terse, dated. Detail goes in private notes; only the headline lands here.
>
> The cadence is what matters. Detail is deliberately kept high-level.

---

## 2026-05-07 — Public placeholder repository upgraded

- Reframed public repo from minimal placeholder to SENTINEL-style positioning artefact.
- Added: [README](./README.md) with status table, scope, stack-layer position, compliance overview, honest-disclosure list, doc map.
- Added: [VISION](./VISION.md), [ARCHITECTURE](./ARCHITECTURE.md), [ROADMAP](./ROADMAP.md), [SAFETY](./SAFETY.md), [SECURITY](./SECURITY.md), [CONTRIBUTING](./CONTRIBUTING.md).
- Added: [`docs/compliance/thai-frameworks.md`](./docs/compliance/thai-frameworks.md), [`docs/DEFENSIBILITY.md`](./docs/DEFENSIBILITY.md).
- Added: GitHub PR template and link-check workflow.
- Goal: a prospect arriving cold can, in 5 minutes, understand who Dynazme is for and how to start a conversation — without seeing source code.

## 2026-05-07 — Repository structure separated, public/private split

- Created two repositories: `Dxrksvng/dynazme` (public, planning docs only) and `Dxrksvng/dynazme-impl` (private, implementation).
- Moved Next.js website source, four product reference codebases, and preview HTML into `dynazme-impl/`.
- Established `.gitignore` rules so an accidental `git add -A` in the public repo cannot publish private content.

## 2026-05-07 — Reference codebases curated

- Curated four product reference folders: `01-rag/` (Super AI Hackathon ss6), `02-bi-agent/`, `03-ocr/` (KMITL Senior Project), `04-automation/` (Healthcare ss5).
- Excluded: virtual environments (~2.4 GB), `node_modules/` (~270 MB), model weights (~95 MB), generated indexes, screenshots, `.env` files with real secrets.
- Total reference asset size reduced from ~5 GB to ~120 MB.
- Goal: pattern reuse, not copy-paste; new product code will be written fresh.

## 2026-04 — Foundation

- Founder positioning solidified: AI Engineering boutique, Thai SMEs, accessible pricing.
- Four product lines named: FahMai (RAG), BI Agent (Data → Slide), DocuSense (OCR), FlowForge (Automation).
- Initial Next.js marketing site scaffolded.
- Brand identity (logo, typography, color system) drafted.

---

## How this log is maintained

- One entry per substantive session. Skipped days are not padded.
- Past entries are not edited; corrections are appended as new entries.
- Customer-specific work is referenced abstractly ("first design partner conversation") — never named.
- Internal failures are recorded in the private repo, not here.
