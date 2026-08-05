# Desktop application allocation

Verified **2026-08-05**.

Claritas Viz is allocated a paired native desktop visualization workbench:

- Rust: [`claritas-viz/claritas-desktop.rs`](https://github.com/claritas-viz/claritas-desktop.rs) — **planned**, not yet verified as a published repository.
- Flutter: [`claritas-viz/claritas-flutter`](https://github.com/claritas-viz/claritas-flutter) — **planned**, not yet verified as a published repository.

The planned URLs are allocation targets, not proof that either remote exists. Do not mark an implementation live until the repository, native targets, tests, packaging, and supported-platform matrix are verified.

## Product boundary

Both implementations should support semantic parity for local dataset import, query and transform workflows, chart and dashboard authoring, keyboard-heavy analysis, multi-window inspection, exports, saved workspaces, offline operation, and recovery. Stable schemas, query/result formats, visualization specs, fixtures, sample datasets, and conformance tests should be shared deliberately.

The Rust and Flutter implementations remain independently buildable, testable, releasable applications. Framework-native architecture and platform behavior may differ.

## Feature-delivery rule

For every desktop-facing feature:

1. inspect both allocated repositories before deciding scope;
2. define shared acceptance criteria and identify affected contracts and fixtures;
3. create or update work for both implementations, or record an explicit no-change rationale;
4. test and report Rust and Flutter status separately; and
5. keep reciprocal repository references and platform matrices current.

## Project routing

- GitHub Project: [`claritas-viz-project` — Project 1](https://github.com/orgs/claritas-viz/projects/1)
- Linear project: `github.com/claritas-viz`
- Central registry: [`ORESoftware/project-registry`](https://github.com/ORESoftware/project-registry/blob/main/registry/desktop-applications.json)
- Portfolio rollout: [`DEN-2469`](https://linear.app/denman/issue/DEN-2469/roll-out-paired-rust-flutter-desktop-repositories-across-the-portfolio)

Repository creation, renames, transfers, archival, or platform-status changes must update this document, the central registry, the Linear project, and both companion repositories in the same delivery.
