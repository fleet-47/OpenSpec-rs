# Schema resolution — specification

[Requirements](schema-resolution.md) · [Blocker index](README.md)

Draft acceptance slices for discussion. Each slice passes only when every listed boolean check is true. Prerequisites remain as declared in the requirements.

Unchecked means acceptance is pending, not that implementation is absent. Exercise relevant cases on isolated copies of current live data/configuration.

## Boolean acceptance slices

### S01 — Schema selection across commands

- [ ] **R07** Every schema-consuming command shall resolve project schemas from `schemas/<name>/schema.yaml` beneath the planning root.
- [ ] **R08** Schema resolution shall prefer project schemas over user schemas over embedded schemas.

### S02 — Custom template instructions

- [ ] **R09** Artifact instructions shall load templates from the selected custom schema.

### S03 — Unresolvable schema rejection

- [ ] **R11** Creating a change with an unresolvable schema shall fail before creating files.

### S04 — Template path containment

- [ ] **R21** Template resolution shall reject paths that escape the selected schema directory.

## Pending work

Enumerate project/user/embedded precedence and template-boundary cases. Coordinate the custom-schema instruction slice with Fleet templates.

For each slice: enumerate acceptance cases, inspect the implementation, address verified gaps, and record acceptance evidence.

Report one total of passing checks, then enumerate each failure with its requirement, evidence and remedy pathway.
