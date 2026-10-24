# OpenSpec-rs patch requirements

Scope: repo-local OpenSpec workflow parity with TypeScript v1.14.3, plus the requested Fleet planning path and template adaptations. This is a bounded patch plan, not a claim of complete upstream feature parity. Store/workset migration remains outside this plan.

[Critical review and held decisions](REVIEW.md)

## Functional groups

| Group | Active | Held |
|---|---:|---:|
| [Planning paths](requirements/blockers/planning-paths.md) | 6 | 0 |
| [Schema resolution](requirements/blockers/schema-resolution.md) | 6 | 0 |
| [Project configuration](requirements/blockers/project-configuration.md) | 6 | 1 |
| [Artifact state and readiness](requirements/blockers/artifact-state.md) | 8 | 0 |
| [Change metadata](requirements/blockers/change-metadata.md) | 3 | 0 |
| [Task tracking](requirements/blockers/task-tracking.md) | 9 | 1 |
| [Spec validation and merging](requirements/blockers/spec-validation.md) | 7 | 0 |
| [Archive integrity](requirements/blockers/archive-integrity.md) | 10 | 0 |
| [Machine-readable interfaces](requirements/blockers/machine-interface.md) | 5 | 1 |
| [Agent workflow delivery](requirements/fast-followers/agent-workflows.md) | 7 | 0 |
| [Rust frontend integration](requirements/backlog/rust-frontend.md) | 0 | 6 |
| [Fleet template adaptation](requirements/blockers/fleet-templates.md) | 3 | 0 |

70 active requirements; 9 held proposals. Original IDs R01–R71 are retained; R72–R79 specify corrections identified during review. Held proposals are excluded from implementation and have no acceptance checkboxes.

## Reading the requirements

- Each active checkbox describes an independently assessable obligation. An unchecked box means acceptance has not been recorded; it does not prove the feature is absent.
- Direct dependencies identify integration prerequisites, not a mandatory patch sequence. A dash means no dependency on another listed requirement; shared code alone is not a dependency.
- No active requirement depends on a held proposal. Held library requirements retain their conditional dependencies within that group.
- Upstream parity items require Rust implementation where behaviour is missing. Fleet template content and artifact workflow definitions belong in a custom schema; parser and runtime behaviour cannot be supplied by schema prose.
