# ICONIX + SDD review checklist (copy per UC)

## Requirements Review
- [ ] FR IDs and UC ID documented
- [ ] Primary actor and system boundary clear
- [ ] Preconditions, main flow, alternatives, exceptions, postconditions defined
- [ ] Acceptance criteria measurable and unambiguous
- [ ] No behavior beyond Chapter I scope
- [ ] Review approved, reviewer/date/evidence recorded

## Preliminary Design Review
- [ ] Domain entities/relationships checked
- [ ] Robustness diagram includes boundary/control/entity roles
- [ ] All use case steps represented, including alternative flow
- [ ] Review approved, reviewer/date/evidence recorded

## Critical Design Review
- [ ] Sequence messages match accepted use case and robustness
- [ ] Shared class model / module mapping consistent
- [ ] Interfaces, responsibilities, and permissions clear
- [ ] Review approved, reviewer/date/evidence recorded

## Implementation and validation
- [ ] Spec Kit spec, plan, tasks match approved designs
- [ ] API contracts approved, no fabricated third-party dependencies
- [ ] Tests include positive, negative, edge, authorization, and offline cases
- [ ] Traceability matrix complete and evidence attached
- [ ] Actual test result recorded; not inferred
