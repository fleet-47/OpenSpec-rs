# Artifact state and readiness

Scope: Upstream parity.

[Index](../README.md) · [Critical review](../../REVIEW.md)

## Requirements

- [ ] **R18** Artifact status results shall preserve schema declaration order between equally eligible artifacts.
- [ ] **R33** Blocked apply instructions shall report all missing transitive prerequisites in dependency order.

## Direct dependencies

| Requirement | Prerequisites |
|---|---|
| R18 | [R17](../blockers/artifact-state.md) |
| R33 | [R17](../blockers/artifact-state.md), [R22](../backlog/withdrawn/artifact-state.md) |


[Scope notes and upstream basis](../blockers/artifact-state.md)
