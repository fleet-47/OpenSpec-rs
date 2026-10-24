# Critical review of the patch requirements

## Findings

The checklist mixed runtime parity, Fleet adaptations and undecided architecture. Several dependencies expressed a suggested coding order rather than a real prerequisite. The functional files now separate those scopes; all original IDs remain accounted for.

| Original item | Finding | Disposition |
|---|---|---|
| R02 | “Support existing projects” did not identify a pass/fail condition. | Defined the default planning directory when no override is configured. |
| R04 | “Every planning command” beneath one directory wrongly includes user schemas and generated tool files. | Limited to project-owned planning artifacts. |
| R12 | “Produce an error” does not distinguish a diagnostic from termination; upstream warns and keeps usable configuration. | Termination policy held; warning and partial recovery specified by R72–R73. |
| R22 | Spec skipping depends on output paths, not a hard-coded artifact ID. | Defined by outputs under `specs/`. |
| R24 | `x-*` was imprecise; existing-file writers must explicitly retain extension data. | Defined the upstream `^x-\S+$` namespace. |
| R26 | Apply, list and archive do not have identical fallback semantics. | Restricted to apply; R75–R77 describe the other cases. |
| R31 | Upstream counts recognized non-`x`/`X` markers as unfinished without a marker diagnostic. | Diagnostic policy held; accounting specified by R74. |
| R32 | “Implementation verification” implied an additional engine. | Replaced with the artifact-completion predicate and compatibility alias R78. |
| R43 | Unconditional restoration promises success even when recovery I/O fails. | Qualified recovery; retained concurrent-edit protection and recovery reporting. |
| R47 | Retirement consent alone omitted upstream’s validation condition. | Added R79: disabling validation prevents automatic file deletion. |
| R50 | Blanket contract conformance is neither atomic nor bounded away from stores/context. | Held until command and field compatibility scope is selected. |
| R61 | Preserving custom files during migration is narrower than preserving edits during every update. | Explicitly limited to migration. |
| R63–R68 | A Rust router does not imply an embedded library interface. | Held as one architecture choice. |
| R69–R71 | Template portability does not imply migrating every source document or enforcing prose at runtime. | Kept as Fleet adaptations, bounded to template output and retained identifiers. |

The configuration finding follows [upstream configuration loading](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/src/core/project-config.ts). Task semantics follow [task accounting](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/src/utils/task-progress.ts) and [apply instructions](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/src/commands/workflow/instructions.ts). Recovery and retirement conditions follow [archive implementation](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/src/core/archive.ts). The [agent contract](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/docs/agent-contract.md) explains why full JSON compatibility also reaches into root/store context.

## Held decisions

| Decision | Choices and consequences | IDs |
|---|---|---|
| Backend interface | Invoke the CLI through structured JSON, keeping backend process boundaries; or embed its Rust library, requiring explicit context and caller-controlled rendering/lifetime. Either can serve a Rust router. | R63–R68 |
| Invalid configuration | Keep upstream warning/partial recovery; or stop the operation on invalid input, trading upstream compatibility for strict enforcement. | R12 |
| Unfamiliar checkbox markers | Keep upstream unfinished-task accounting; or add diagnostics for markers outside the accepted completion convention. | R31 |
| JSON compatibility boundary | Choose the repo-local command/field contract explicitly; or adopt the complete upstream contract together with its root/store context. The active envelope requirements do not settle this choice. | R50 |

These are review candidates, not approved changes. No active dependency requires adopting them.

## Dependency corrections

Removed false prerequisites such as legacy `openspec/` support depending on the new path option, configuration rules depending on project context, task parsing depending on schema resolution, and read-only archive guidance depending on configured guidance text. No context/rules requirement depends on strict configuration failure, and archive task warnings no longer depend on the held marker-diagnostic policy.

The remaining edges capture integration needs: generated path references use the configured path; custom templates use schema resolution; task aggregation uses tracking resolution; archive warnings use task accounting; generated handoffs use selected/delivered workflows. They do not prescribe a shared implementation or require a library refactor.

## Implementation boundary

Custom schema authoring covers Fleet artifact definitions, dependency order, templates and contextual instructions. Rust changes are needed for missing path resolution, schema loading, metadata behaviour, task accounting, spec merging, archive recovery, machine output and tool delivery. Schema prose alone cannot provide runtime enforcement for those behaviours.

The previous local exercise identified archive-destination collision as a data-integrity defect: canonical specs changed before the collision was reported. R41–R45 therefore have higher corrective priority than interface refactoring. This documentation review does not claim that the binary now satisfies them or that every upstream feature has been audited.
