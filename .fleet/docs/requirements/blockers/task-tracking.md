# Task tracking

Scope: Upstream parity; one held policy.

[Index](../README.md) · [Critical review](../../REVIEW.md)

## Requirements

- [ ] **R26** Apply instructions shall resolve task files from the selected schema’s `apply.tracks` value.
- [ ] **R27** Apply task-progress calculations shall aggregate every file matched by an `apply.tracks` glob.
- [ ] **R28** Each task returned by apply instructions shall identify its source file.
- [ ] **R30** Task parsing shall recognize checkbox list items using `-`, `*`, `+`, or one-to-nine-digit ordered markers ending in `.` or `)`.
- [ ] **R74** Task accounting shall mark a recognized checkbox complete if and only if its marker is `x` or `X`.
- [ ] **R75** List and archive task accounting shall use the schema artifact whose output pattern equals `apply.tracks`, or the `tasks` artifact when `apply.tracks` is absent.
- [ ] **R76** List and archive task accounting shall fall back to the change’s top-level `tasks.md` when schema resolution yields no tracking files.
- [ ] **R77** Apply instructions shall report no tracked tasks when the schema omits `apply.tracks`.

## Scope notes

For R74, recognized boxes have an empty marker or one non-whitespace character; non-`x`/`X` markers count as unfinished. Multi-character labels such as `[WIP]` are not task boxes. R31 would add a diagnostic absent from upstream. R75–R77 replace the original assertion that all progress surfaces always use `apply.tracks`; upstream deliberately retains fallback behaviour for list and archive.

## Direct dependencies

| Requirement | Prerequisites |
|---|---|
| R26 | — |
| R27 | [R26](task-tracking.md) |
| R28 | — |
| R30 | — |
| R74 | — |
| R75 | — |
| R76 | — |
| R77 | — |

## Upstream basis

- [src/utils/task-progress.ts](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/src/utils/task-progress.ts)
- [src/commands/workflow/instructions.ts](https://github.com/Fission-AI/OpenSpec/blob/v1.14.3/src/commands/workflow/instructions.ts)
