# Schema resolution

Scope: Upstream parity.

[Index](../README.md) · [Critical review](../../REVIEW.md)

## Requirements

- [ ] **R07** Every schema-consuming command shall resolve project schemas from `schemas/<name>/schema.yaml` beneath the planning root.
- [ ] **R08** Schema resolution shall prefer project schemas over user schemas over embedded schemas.
- [ ] **R09** Artifact instructions shall load templates from the selected custom schema.
- [ ] **R11** Creating a change with an unresolvable schema shall fail before creating files.
- [ ] **R21** Template resolution shall reject paths that escape the selected schema directory.

## Direct dependencies

| Requirement | Prerequisites |
|---|---|
| R07 | — |
| R08 | [R07](schema-resolution.md) |
| R09 | [R08](schema-resolution.md) |
| R11 | — |
| R21 | — |

## Upstream basis

- [src/core/artifact-graph/resolver.ts](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/src/core/artifact-graph/resolver.ts)
