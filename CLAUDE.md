# Lapor Api — Project Instructions for Claude Code

## 1. Project identity
Lapor Api is an academic research prototype for community reporting of early indications and incidents of forest and land fires (karhutla), case study: Kabupaten Sekadau, Kalimantan Barat, Indonesia.

Research methodology: ICONIX Process integrated with Spec-Driven Development (SDD), from spec-first toward spec-anchored. This is a research implementation, not an operational emergency response deployment.

## 2. Priority of authority
1. Approved research scope and requirements in `docs/requirements/`.
2. Approved use-case specifications and business rules.
3. Reviewed ICONIX artifacts in `docs/iconix/` (domain model, robustness, sequence, class diagrams).
4. Spec Kit feature artifacts in `specs/`.
5. This file for coding and workflow conventions.

If these conflict, STOP and report the conflict. Do not invent rules or silently update approved requirements.

## 3. Fixed scope
- Citizen report with photo and automatically acquired GPS coordinates.
- Offline local draft and explicit retry; never claim successful remote submission without server confirmation.
- Emergency telephone shortcut to Call Center 110.
- Potential duplicate detection within 50 meters of a primary incident that is still open; no age limit while open. Compare unrounded computed distance.
- Parallel notification of relevant Polres and territorial Polsek operators.
- Admin Polres verification and disposition.
- Cross-agency information routing and operational updates by authorized personnel.
- Alternative emergency path: territorial Polsek may respond before verification is completed, subject to recorded authorization/workflow rules.
- Exactly six user-facing stages: Laporan Diterima; Laporan Ditriase; Petugas Ditugaskan; Petugas Menuju Lokasi; Penanganan Berlangsung; Penanganan Selesai.

Out of scope: real-time tracking of response personnel, live satellite hotspot feed, integrated equipment inventory, and claims of measured reduction in actual response times.

## 4. Technology constraints
- Frontend/mobile: SvelteKit + TypeScript + adapter-static + Capacitor for Android.
- Mobile code must run without a SvelteKit server runtime; do not depend on server actions or server-only modules in the APK.
- Native capabilities via maintained Capacitor plugins where practical (camera, geolocation, local storage as suitable).
- Backend technology, database, authentication provider, and hosting are NOT yet approved. Propose options with tradeoffs and ask for a documented architecture decision before implementation.
- Use an API abstraction to prevent UI components coupling to persistence and external services.
- Never embed server secrets, credentials, or privileged service keys in the mobile bundle.

## 5. Mandatory ICONIX + SDD gates per use case
G1 Requirements: establish requirement IDs (FR-xx), UC ID, use case main/alternate/error flows, acceptance criteria; human Requirements Review.
G2 Analysis: domain/entity alignment and robustness diagram (boundary/control/entity); human Preliminary Design Review.
G3 Detailed Design: sequence diagram and shared class diagram (or documented TypeScript module mapping); human Critical Design Review.
G4 SDD planning: review Spec Kit spec, plan, contracts, tasks against approved ICONIX artifacts; perform consistency analysis.
G5 Implementation: implement only approved tasks; small reviewable changes; tests at the boundary; log decisions.
G6 Validation: black-box scenarios including unauthorized transitions, failures, and 50 m boundary; complete traceability and evidence.

Do not start code changes for a new use case if G1–G3 are not approved. A user can explicitly request an infrastructure-only spike; label it as a spike, not as feature implementation evidence.

## 6. Traceability
Maintain `docs/traceability/matrix.csv` using these columns:
FR_ID,UC_ID,Spec_Path,Robustness_Ref,Sequence_Ref,Code_Ref,Test_ID,Result,Evidence_Ref

Each feature and test must refer to FR and UC IDs. Never mark a missing artifact as complete. Keep review log and evidence for each gate in `docs/experiments/`.

## 7. Coding standards
- TypeScript strict; avoid `any` without justification.
- Separate UI, domain logic, API clients, and native-device adapters.
- Validation on both client and server; server enforces roles, report ownership, and workflow transitions.
- Handle offline, timeouts, retries, duplicated requests, and permission denials explicitly.
- Do not silently broaden the thesis scope.
- Prefer pure functions for business rules with deterministic unit tests; use mock data only if clearly labeled.
- Before changing behavior: update the spec and relevant ICONIX design, then tests and code.
- For bugs that violate an approved spec: fix code and record the bug without changing the contract.

## 8. Working style
Before editing, respond with: (a) artifact references, (b) proposed files, (c) risks/assumptions, (d) validation plan. For research gates, request explicit human review. Report actual commands and test results; never claim unexecuted checks passed. Keep changes narrow and use meaningful commits.

## 9. Common commands (verify after project init)
- `npm run dev`
- `npm run check`
- `npm run build`
- `npx cap sync android`
- `npx cap open android`

## 10. Current milestone
Milestone 0: establish repository, tooling, Android shell, requirement catalog, use-case map, and review checklist. Do NOT implement UC-01 until the requirements and design gates have been approved.
