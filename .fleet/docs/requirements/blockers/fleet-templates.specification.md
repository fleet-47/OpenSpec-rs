# Fleet template adaptation — specification

[Requirements](fleet-templates.md) · [Blocker index](README.md)

Draft acceptance slices for discussion. Each slice passes only when every listed boolean check is true. Prerequisites remain as declared in the requirements.

Unchecked means acceptance is pending, not that implementation is absent. Exercise relevant cases on isolated copies of current live data/configuration.

## Boolean acceptance slices

### S01 — Fleet instructions from the chosen schema

- [ ] **R69** A Fleet workflow schema shall expose the adapted Fleet templates through artifact instruction responses.

### S02 — Parser-compatible spec output

- [ ] **R70** Fleet spec templates consumed by the OpenSpec spec parser shall emit OpenSpec Requirement/Scenario grammar.

### S03 — Stable Fleet identifiers

- [ ] **R71** Adapted Fleet templates shall preserve existing record and requirement identifiers.

## Pending work

Select actual Fleet templates and identifier examples for acceptance. Coordinate schema resolution; template prose does not establish runtime enforcement.

For each slice: enumerate acceptance cases, inspect the implementation, address verified gaps, and record acceptance evidence.

Report one total of passing checks, then enumerate each failure with its requirement, evidence and remedy pathway.
