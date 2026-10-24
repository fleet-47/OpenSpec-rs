# Blockers

[Priority index](../README.md)

| Document | IDs | Description |
|---|---|---|
| [Planning paths](planning-paths.md) | R01, R03, R04, R05, R06 | Resolve Fleet planning artifacts and generated instructions consistently without changing global locations. |
| [Schema resolution](schema-resolution.md) | R07, R08, R09, R11, R21 | Select the correct schema and custom templates; reject unresolved schemas and escaping template paths. |
| [Fleet template adaptation](fleet-templates.md) | R69, R70, R71 | Expose Fleet templates, emit parser-compatible specs and retain existing identifiers. |
| [Project configuration](project-configuration.md) | R13, R14, R15, R16, R72, R73 | Deliver current project context and rules while reporting discarded configuration and retaining valid fields. |
| [Artifact state and readiness](artifact-state.md) | R17, R19, R20, R32, R78 | Report prerequisite order, output files and planning completion accurately while containing artifact paths. |
| [Change metadata](change-metadata.md) | R24, R25 | Preserve extension fields during rewrites and report unsupported metadata keys. |
| [Task tracking](task-tracking.md) | R26, R27, R28, R30, R74, R75, R76, R77 | Discover and aggregate tracking files correctly, recognize task markers and preserve each command’s fallback behaviour. |
| [Spec validation and merging](spec-validation.md) | R34, R35, R36, R37, R38, R40 | Interpret deltas consistently and prevent lost scenarios, duplicate requirements or discarded authored content. |
| [Archive integrity](archive-integrity.md) | R41, R42, R43, R44, R45, R46, R47, R48, R49, R79 | Reserve archive destinations safely, recover failures without overwriting concurrent edits and protect canonical specs. |
| [Machine-readable interfaces](machine-interface.md) | R51, R52, R53, R54 | Emit one JSON document, separate human messages and expose operational failures reliably. |

## Specification sidecars

- [planning-paths.specification.md](planning-paths.specification.md): Boolean acceptance slices and pending work for this blocker.
- [schema-resolution.specification.md](schema-resolution.specification.md): Boolean acceptance slices and pending work for this blocker.
- [fleet-templates.specification.md](fleet-templates.specification.md): Boolean acceptance slices and pending work for this blocker.
- [project-configuration.specification.md](project-configuration.specification.md): Boolean acceptance slices and pending work for this blocker.
- [artifact-state.specification.md](artifact-state.specification.md): Boolean acceptance slices and pending work for this blocker.
- [change-metadata.specification.md](change-metadata.specification.md): Boolean acceptance slices and pending work for this blocker.
- [task-tracking.specification.md](task-tracking.specification.md): Boolean acceptance slices and pending work for this blocker.
- [spec-validation.specification.md](spec-validation.specification.md): Boolean acceptance slices and pending work for this blocker.
- [archive-integrity.specification.md](archive-integrity.specification.md): Boolean acceptance slices and pending work for this blocker.
- [machine-interface.specification.md](machine-interface.specification.md): Boolean acceptance slices and pending work for this blocker.

## First discussion

Start with [archive integrity](archive-integrity.specification.md), S01–S04: collision protection and recovery form one safety cluster.

