# Fleet template adaptation

Scope: Fleet adaptation.

[Index](../README.md) · [Critical review](../../REVIEW.md)

## Requirements

- [ ] **R69** A Fleet workflow schema shall expose the adapted Fleet templates through artifact instruction responses.
- [ ] **R70** Fleet spec templates consumed by the OpenSpec spec parser shall emit OpenSpec Requirement/Scenario grammar.
- [ ] **R71** Adapted Fleet templates shall preserve existing record and requirement identifiers.

## Scope notes

Custom schemas can supply artifact order, templates and instructions. R70 applies only to parser-consumed spec output; it does not require rewriting every Fleet document. These requirements do not turn template instructions into runtime policy enforcement.

## Direct dependencies

| Requirement | Prerequisites |
|---|---|
| R69 | [R09](schema-resolution.md) |
| R70 | — |
| R71 | — |
