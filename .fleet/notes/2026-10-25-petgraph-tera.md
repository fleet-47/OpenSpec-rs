# Petgraph and Tera integration research

Research date: 2026-10-25. INFERRED: “terra” means Rust Tera. Recommendations are proposals, not selected architecture. No implementation or build verification accompanies this note.

## Versions

The project declares Rust 1.75 and edition 2021 in [Cargo.toml](../../Cargo.toml).

| Library | Verified release metadata | Consequence |
|---|---|---|
| petgraph 0.8.3 | Declared Rust 1.64, edition 2021. [Published manifest](https://docs.rs/crate/petgraph/latest/source/Cargo.toml.orig) | Declared floor fits; dependency resolution still requires verification. |
| Tera 2.4.0 | Edition 2024, no explicit `rust-version`. [Release manifest](https://raw.githubusercontent.com/Keats/tera/v2.4.0/tera/Cargo.toml) | Requires at least Rust 1.85, which introduced edition 2024; exact minimum unknown. [Edition guide](https://doc.rust-lang.org/edition-guide/rust-2024/index.html) |
| Tera 1.20.0 / 1.20.1 | Rust 1.70 / 1.85 respectively. [1.20.0](https://raw.githubusercontent.com/Keats/tera/v1.20.0/Cargo.toml), [1.20.1](https://raw.githubusercontent.com/Keats/tera/v1.20.1/Cargo.toml) | Keeping Rust 1.75 requires deliberate older-version selection and dependency verification; `tera = "1"` does not preserve that floor. |

Tera 2 provides optional `glob_fs`, `fast`, `unicode`, and `preserve_order` capabilities. Use versioned release APIs when designing integration. [Tera manifest](https://raw.githubusercontent.com/Keats/tera/v2.4.0/tera/Cargo.toml)

## Petgraph APIs and benefits

- `DiGraph<Artifact, Dependency>` supplies `add_node`, `add_edge`, and `neighbors_directed`. `NodeIndex` is a collection handle; removing a node can move another index. INFERRED: preserve schema IDs as domain identities and map them internally. [Graph API](https://docs.rs/petgraph/0.8.3/petgraph/graph/struct.Graph.html)
- `StableDiGraph` preserves unrelated indices during removal. INFERRED: useful for structural edits; a graph rebuilt from each resolved schema can use `DiGraph`. `GraphMap` uses `Copy + Eq + Hash + Ord` node values as identifiers, so owned strings do not fit directly. [StableGraph](https://docs.rs/petgraph/0.8.3/petgraph/stable_graph/struct.StableGraph.html), [GraphMap](https://docs.rs/petgraph/0.8.3/petgraph/graphmap/struct.GraphMap.html)
- `toposort(&graph, None)` returns dependency order or a cycle error in O(V+E). `Cycle::node_id()` gives one participant, not the complete cycle. Strongly connected component algorithms identify cyclic groups for richer diagnostics. [toposort](https://docs.rs/petgraph/latest/petgraph/algo/fn.toposort.html), [Cycle](https://docs.rs/petgraph/0.8.3/petgraph/algo/struct.Cycle.html), [algorithms](https://docs.rs/petgraph/latest/petgraph/algo/index.html)
- `Topo::new/with_initials/next` provide incremental traversal; exhaustion does not prove acyclicity without comparing visited and total nodes. Its implementation uses a LIFO vector. Neither `Topo` nor `toposort` promises declaration-order ties. INFERRED: select by declaration rank among currently eligible nodes when required; sorting the completed order can break dependencies. [Topo](https://docs.rs/petgraph/latest/petgraph/visit/struct.Topo.html), [implementation](https://docs.rs/petgraph/latest/src/petgraph/visit/traversal.rs.html)
- `Dfs`, `Bfs`, and `Reversed(&graph)` support prerequisite and downstream traversal. INFERRED: prerequisite → dependent edges allow reversed traversal for blockers. These APIs understand supplied edges, not source-code call relationships. [Traversal API](https://docs.rs/petgraph/latest/petgraph/visit/index.html)
- `Acyclic::try_add_edge` rejects cycle-forming edits. Optional `serde-1` serializes graph structures but provides no storage or transaction semantics. INFERRED: rebuild from authoritative files; no workflow macro DSL or graph database is needed. [Acyclic](https://docs.rs/crate/petgraph/latest/source/src/acyclic.rs), [features](https://docs.rs/crate/petgraph/latest/features)

## Tera 2 APIs and benefits

`Tera::new()` creates an empty engine. Register helpers, then batch-load using `add_raw_templates`; `add_template_files` loads explicit paths and `load_from_glob` requires `glob_fs`. `render` returns text; `render_to` writes through `std::io::Write`. `register_from` shares helpers, not template sets. `render_block` and `render_component` target portions of output. `get_template_variables` is best-effort, not a full contract checker. [Tera API](https://docs.rs/tera/2.4.0/tera/struct.Tera.html)

`Context::from_serialize(&model)` is a fallible boundary from typed Rust data. `Context::insert` can panic on serialization failure. Rust's `context!` macro is construction shorthand; it does not compile templates into the binary. INFERRED: serialize a small instruction model containing resolved paths, context, rules, readiness and task summaries. [Context API](https://docs.rs/tera/2.4.0/tera/struct.Context.html), [crate API](https://docs.rs/tera/2.4.0/tera/)

Templates support variables, conditions, loops, static `include`, `extends`, blocks and `super()`. Tera 2 replaces Tera 1's template macros/imports with components: reusable parameterized text, optional argument types/defaults, nesting and namespacing. Components register globally without imports. They emit Markdown despite HTML-like invocation syntax. [Template language](https://keats.github.io/tera/), [migration guide](https://raw.githubusercontent.com/Keats/tera/v2.4.0/MIGRATION.md)

Custom Rust `Function`, `Filter`, and `Test` implementations or compatible functions register through `register_function`, `register_filter`, and `register_test`. `Kwargs` checks argument presence/types; `State` exposes context. Register before adding templates: Tera 2 checks referenced helpers/components during template compilation. This happens at runtime: external template edits need reload, not binary recompilation. New Rust helpers require rebuilding. [Tera API](https://docs.rs/tera/2.4.0/tera/struct.Tera.html), [migration guide](https://raw.githubusercontent.com/Keats/tera/v2.4.0/MIGRATION.md)

Autoescaping defaults to HTML/XML suffixes, not Markdown. Undefined rendered variables error; conditional branches can remain unevaluated. Raw blocks preserve literal syntax. INFERRED: adopt syntax explicitly so literal `{{...}}` examples do not silently become executable templates. Parsing does not prove all contexts render or that output meets OpenSpec's grammar. [Template language](https://keats.github.io/tera/)

Tera 1's `new(glob)`, `parse`, `build_inheritance_chains`, `check_macro_files`, and `extend` are older APIs. `parse` leaves inheritance unfinished; `extend` preserves names already present. Do not carry these APIs into a Tera 2 design. [Tera 1 source](https://raw.githubusercontent.com/Keats/tera/v1.20.1/src/tera.rs)

## Architectural boundary

INFERRED: petgraph can centralize dependency/readiness calculations; Tera can centralize instruction composition and reusable Fleet text. Keep workflow decisions in Rust and pass results into templates. Components reduce source duplication; rendered tokens only decrease when output deliberately excludes irrelevant material. Partial rendering can help provide just the active artifact, failure details, and remedy guidance.

INFERRED: neither library resolves project-root precedence, glob completeness, checkbox semantics, spec merging, containment, locks, concurrent edits, or rollback. `render_to` accepts a writer without providing a transaction. Render to a buffer or staging destination before mutation; writing directly to canonical files retains partial-write risk. [Rendering API](https://docs.rs/tera/2.4.0/tera/struct.Tera.html)

## Local architecture assessment

Verified against the working tree on 2026-10-25; no build or runtime acceptance is claimed.

| Existing seam | Direct evidence | Implication |
|---|---|---|
| Schema resolution | [`resolve_schema`](../../src/core/schema.rs), line 271, already selects project/user/embedded schemas using `<name>/schema.yaml`. [`status`](../../src/cli/status.rs), line 187, and [`instructions`](../../src/cli/instructions.rs), line 706, instead load `<name>.yaml`. | Consolidate callers onto one resolver before introducing template composition. |
| Dependency/status computation | [`SchemaYaml::topological_order`](../../src/core/schema.rs), line 138, and [`ArtifactGraph::get_build_order`](../../src/core/artifact.rs), line 119, implement separate ordering. Status is calculated in both core and CLI; ordering helpers have only test callers within `src`. | Replacing an unused helper alone cannot repair command behaviour. Move actual status/apply callers together. |
| Instruction context | [`ArtifactInstructions`](../../src/cli/instructions.rs), line 38, is serializable, but construction at line 161 assigns `context: None` and `rules: None`. | A typed instruction result is an existing integration seam. Populate it from actual configuration before rendering. |
| Template loading | [`load_template`](../../src/cli/instructions.rs), line 410, returns embedded Markdown only and rejects other schemas. | Custom template loading is necessary independently of choosing Tera. Rendering is an additional capability. |
| Tracking | [`generate_apply_instructions`](../../src/cli/instructions.rs), line 237, reads a literal tracking path. [`list`](../../src/cli/list.rs), line 255, and [`archive`](../../src/cli/archive.rs), line 199, separately read `tasks.md`. | Share file discovery/accounting while preserving the required command-specific fallback semantics. Petgraph does not parse checkboxes. |
| Spec preservation | [`spec_parser`](../../src/core/spec_parser.rs) already contains parsing, delta planning, merging and dedicated tests. | Preserve and correct this domain implementation; a graph or template engine does not replace it. |
| Archive | [`run_archive`](../../src/cli/archive.rs) applies spec updates before checking the final archive destination. | The confirmed collision defect and R41–R45 recovery obligations remain a separate safety gate. |

The installed compiler reports Rust 1.99.1; [`Cargo.toml`](../../Cargo.toml) declares Rust 1.75 and edition 2021. Dependency adoption must reconcile that declared support promise; this research has not established a complete dependency-resolution MSRV or cross-device build result.

## Recommendation — inferred, not an approved architecture

Use stacked architectural patches within this codebase. Design the shared internal workflow core cleanly, then replace duplicated command logic at the existing CLI boundary. This captures the principal design benefit of starting fresh while retaining the parser/merge implementation, command surface, configuration behaviours, tool adapters and compatibility work.

| Approach | Benefit | Cost and fit |
|---|---|---|
| Independent local fixes | Small individual changes. | Repeats the same path/schema/state fixes across divergent command implementations. Poor fit for the demonstrated duplication. |
| Shared core introduced through stacked patches | Central ownership, incremental CLI acceptance and reuse of existing domain behaviour. | Requires coherent routing of each affected command and deletion of its obsolete duplicate. Recommended. |
| Separate greenfield implementation | Unconstrained internal/public model. | Must re-establish compatible records, deltas, CLI behaviour, tool delivery and safe archive. Justified only if replacing those contracts becomes the goal; petgraph/Tera adoption alone does not require it. |

Proposed integration sequence, with observable CLI slices rather than library-only milestones:

1. **Shared project/schema context:** make status and instructions agree on the configured root and selected schema; validate schema selection before new-change writes. Extend the same resolution to other affected commands.
2. **Graph and observed state:** use petgraph beneath shared readiness/status/apply computations. Keep artifact IDs and schema ordinals explicit, discover actual outputs, and centralize task accounting. Graph nodes describe artifacts; checkbox tasks do not automatically become graph nodes.
3. **Template rendering:** feed the typed instruction result into Tera, with current context/rules and only the relevant dependencies/tasks. Load helper registrations before templates. Keep machine JSON on Serde. Runtime templates can change without recompilation; new Rust helpers cannot.
4. **Safe mutation:** retain the spec parser and implement the archive reservation/recovery obligations. This may be an independent patch branch, but must pass before a complete writing dogfood cycle. Graph ordering is not transaction safety.

This is a design sequence, not a claim that archive safety has ceased to be a blocker. Initial shared-core specification work can cover planning paths, schema resolution, configuration, artifact state and Fleet rendering as a cluster. Task discovery and archive safety retain their own acceptance obligations.

An internal context object does not select the held external embedded-library architecture R63–R68. Neither a new database, scheduler, action DSL nor full upstream contract adoption follows from using these libraries.

## Scope and token efficiency

Petgraph reduces bespoke dependency algorithms. Tera reduces repeated formatting and enables reusable template components. Root containment, metadata preservation, task semantics, merge correctness, JSON errors, migration preservation and archive recovery still require application code.

Render only the active artifact or requested report section. A result view can supply one passing count plus individual failures and remedy paths. Components reduce template duplication; they do not inherently reduce output tokens. Keep workflow acceptance decisions in typed Rust results and let templates present them.

Tera renders supplied data. It does not invent a completed specification from a skeleton or verify that an agent followed the instructions. Defining a new structured record-authoring workflow would be additional product scope.
