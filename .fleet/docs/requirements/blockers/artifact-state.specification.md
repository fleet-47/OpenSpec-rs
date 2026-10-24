# Artifact state and readiness — specification

[Requirements](artifact-state.md) · [Blocker index](README.md)

Draft acceptance slices for discussion. Each slice passes only when every listed boolean check is true. Prerequisites remain as declared in the requirements.

Unchecked means acceptance is pending, not that implementation is absent. Exercise relevant cases on isolated copies of current live data/configuration.

## Boolean acceptance slices

### S01 — Prerequisite-first status

- [ ] **R17** Artifact status results shall list each prerequisite before its dependants.

### S02 — Complete output discovery

- [ ] **R19** Artifact instruction responses shall identify every existing file matching the artifact output pattern.

### S03 — Artifact path containment

- [ ] **R20** Artifact output resolution shall reject paths that escape the change directory.

### S04 — Planning completion and compatibility alias

- [ ] **R32** Status `isPlanningComplete` shall be true exactly when every non-skipped artifact exists.
- [ ] **R78** Status `isComplete` shall equal `isPlanningComplete`.

## Pending work

Reconcile R32’s preserved “non-skipped” wording with removal of the explicit skip option before implementation. Assess graph-library fit with task tracking; no graph tool is selected.

For each slice: enumerate acceptance cases, inspect the implementation, address verified gaps, and record acceptance evidence.

Report one total of passing checks, then enumerate each failure with its requirement, evidence and remedy pathway.
