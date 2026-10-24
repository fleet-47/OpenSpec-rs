# Planning paths

Scope: Fleet adaptation.

[Index](../README.md) · [Critical review](../../REVIEW.md)

## Requirements

- [ ] **R01** The CLI shall accept `.fleet/docs` as its configured planning directory.
- [ ] **R03** Commands invoked from a project subdirectory shall resolve the same planning root as commands invoked from the project root.
- [ ] **R04** Commands shall resolve project-owned planning artifacts beneath the selected planning root.
- [ ] **R05** Generated agent instructions shall reference the selected planning directory.
- [ ] **R06** Changing the planning directory shall leave global XDG configuration and data locations unchanged.

## Scope notes

Project-owned planning artifacts include project configuration, project schemas, changes, main specs and archives. Tool installations and user-level schemas retain their separate locations.

## Direct dependencies

| Requirement | Prerequisites |
|---|---|
| R01 | — |
| R03 | — |
| R04 | — |
| R05 | [R01](planning-paths.md) |
| R06 | — |
