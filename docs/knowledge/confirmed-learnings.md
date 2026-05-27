# Confirmed Learnings

> **Promoted from `learning: confirmed` issues.**
> A learning lands here only after it has been independently confirmed (≥2 signals or 1 experiment).
> These are treated as facts until a future signal forces a revisit.

## Format

Each entry:
- **Learning:** one sentence
- **Confirmed by:** issues #_, #_
- **Implications:** what this means for product / strategy
- **Date promoted:** YYYY-MM-DD

---

## L-001 — Audit trails must store IDs, not names

- **Learning:** Embedding display names in audit messages is a GDPR + accuracy
  trap; store user IDs and resolve at read time.
- **Confirmed by:** ADR-0003, internal review of `OrderActivity` prototype.
- **Implications:** All new domain events follow the ID-only pattern. BFFs own
  batch name resolution; domain services never know about display strings.
- **Date promoted:** 2025-12-10

## L-002 — BFF aggregation beats frontend orchestration

- **Learning:** Putting per-screen aggregation in a thin BFF beats letting the
  Vue app fan out to 3–4 services per view, both for latency and for keeping
  auth logic in one place.
- **Confirmed by:** ADR-0002; observed in Collector "Company Orders" screen
  where pre-BFF prototype paid 4 round-trips per render.
- **Implications:** Any new role-specific surface (e.g., dispatcher portal)
  gets its own BFF rather than richer endpoints in a shared service.
- **Date promoted:** 2025-12-15

## L-003 — Sequence belongs to the aggregate, not the leaf

- **Learning:** Route stop sequence on the Route (ordered ID array) is
  dramatically simpler than a sequence field on the Order — 1 write vs. N,
  and integrity is intrinsic.
- **Confirmed by:** ADR-0004; drag-and-drop UX in Collector app.
- **Implications:** Apply the same lens to future N-position aggregates
  (e.g., delivery manifests, inspection checklists).
- **Date promoted:** 2026-01-08

## L-004 — `Money` as a value object pays off across services

- **Learning:** A shared `Money` value object (Currency + Amount, with safe
  arithmetic) avoids decimal drift and floating-point bugs that plagued the
  early Product Service.
- **Confirmed by:** Cross-service order totalling now matches to the øre;
  zero rounding bugs reported since adoption.
- **Implications:** Codify as a tiny shared kernel; resist the urge to
  re-implement per service.
- **Date promoted:** 2026-02-02

## L-005 — JIT provisioning on every request, not just on login

- **Learning:** Running the JIT-provisioning filter on every BFF request
  (not just first login) keeps the Wastr user record in sync with AAD group
  changes (company moves, role grants) without an out-of-band sync job.
- **Confirmed by:** Three observed cases where a user's company changed in
  AAD and was reflected on the next API call.
- **Implications:** User Service is on the hot path; must stay fast and
  highly available. In-memory short-TTL cache acceptable.
- **Date promoted:** 2026-02-18

## L-006 — Service-to-service auth via client credentials > shared API key

- **Learning:** Azure AD client-credential tokens (`AcquireTokenForClient`)
  give per-service identity, audit, and rotation for free; shared API keys
  conflated services and were a security review smell.
- **Confirmed by:** Security review pre-pilot, no incidents since switch.
- **Implications:** Every new service-to-service call uses client credentials.
  Basic Auth allowed only for legacy / on-prem integrations.
- **Date promoted:** 2026-03-05

