# Planning paths — specification

[Requirements](planning-paths.md) · [Blocker index](README.md)

Draft acceptance slices for discussion. Each slice passes only when every listed boolean check is true. Prerequisites remain as declared in the requirements.

Unchecked means acceptance is pending, not that implementation is absent. Exercise relevant cases on isolated copies of current live data/configuration.

## Boolean acceptance slices

### S01 — Configured Fleet root

- [ ] **R01** The CLI shall accept `.fleet/docs` as its configured planning directory.
- [ ] **R04** Commands shall resolve project-owned planning artifacts beneath the selected planning root.

### S02 — Invocation from a subdirectory

- [ ] **R03** Commands invoked from a project subdirectory shall resolve the same planning root as commands invoked from the project root.

### S03 — Generated path references

- [ ] **R05** Generated agent instructions shall reference the selected planning directory.

### S04 — Global location isolation

- [ ] **R06** Changing the planning directory shall leave global XDG configuration and data locations unchanged.

## Pending work

Resolve the configuration entry point and live project/subdirectory cases. Coordinate root selection with schema resolution and generated instructions.

For each slice: enumerate acceptance cases, inspect the implementation, address verified gaps, and record acceptance evidence.

Report one total of passing checks, then enumerate each failure with its requirement, evidence and remedy pathway.
