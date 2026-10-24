# Change metadata

Scope: Upstream parity.

[Index](../README.md) · [Critical review](../../REVIEW.md)

## Requirements

- [ ] **R24** Metadata rewrites shall preserve top-level extension fields matching `^x-\S+$`.
- [ ] **R25** Validation shall report unrecognized metadata keys outside the supported extension namespace.

## Scope notes

The supported extension namespace is `^x-\S+$`: lowercase `x-` followed by a nonempty suffix without whitespace. Preservation applies to rewrites of existing metadata, not just creation.

## Direct dependencies

| Requirement | Prerequisites |
|---|---|
| R24 | — |
| R25 | — |

## Upstream basis

- [src/utils/change-metadata.ts](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/src/utils/change-metadata.ts)
- [src/core/change-metadata/schema.ts](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/src/core/change-metadata/schema.ts)
