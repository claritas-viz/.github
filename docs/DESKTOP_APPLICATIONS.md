# Desktop application allocation

Verified **2026-08-06**.

Claritas Viz is allocated a paired desktop visualization workbench:

- Rust: [`claritas-viz/claritas-desktop.rs`](https://github.com/claritas-viz/claritas-desktop.rs) — **planned**, not yet verified as a published repository.
- Flutter: [`claritas-viz/claritas-flutter`](https://github.com/claritas-viz/claritas-flutter) — **planned**, not yet verified as a published repository.

The planned URLs are allocation targets, not proof that either remote exists.

## Why both Rust and Flutter remain active

The two workbenches will be first-class side-by-side implementations so the project can compare rendering and large-data performance, accessibility, desktop ergonomics, mobile reuse, developer velocity, packaging, platform integration, and long-term maintenance with the same visualization features.

Every desktop-facing feature must be planned against both repositories, share acceptance criteria and datasets, and normally update both. A one-sided change requires a documented no-change rationale and parity gap.

## Rust desktop kit: Dioxus Desktop

**Selected strategy:** Dioxus Desktop.

**WebView policy:** allowed and explicitly acknowledged. The mature Dioxus Desktop renderer uses the system WebView while Rust logic runs natively.

**Frontend policy:** Dioxus RSX and Rust components only. Do not add React, JSX, a JavaScript SPA, or a second frontend framework. Rust owns data loading, transformation, validation, local persistence, permissions, deep-link parsing, and privileged operations.

Claritas is dominated by data tables, filters, dashboards, SVG/HTML visualization, saved workspaces, and query/result navigation. Dioxus provides a productive Rust component model for these surfaces. Native GPU overlays or a Dioxus Native/Blitz migration require a separate ADR and performance evidence.

The Rust repository must contain `docs/DESKTOP_TOOLKIT.md` covering Dioxus version/renderer policy, CSP/WebView threat model, large-data strategy, deep links, accessibility, tests, packaging, and Flutter companion.

## HTTPS-first deep linking

Canonical form:

```text
https://<verified-claritas-owned-host>/open/<route>?<bounded-query>
```

Fallback scheme:

```text
claritas://<route>?<bounded-query>
```

Routes must be defined in the Claritas interfaces package and shared by Rust, Flutter, clients, and browser fallback pages.

Required behavior:

- receive OS/Wry events in Rust and parse them before updating Dioxus component state;
- support cold-start and already-running/single-instance delivery;
- validate the exact host, route, workspace/dataset/view identifiers, action, and bounded query parameters;
- never place datasets, query results, credentials, bearer tokens, or private dashboard contents in URLs;
- use short-lived, one-time, audience-bound codes for invitations, shares, imports, and authentication;
- require confirmation before importing external datasets or applying write actions; and
- test macOS, Windows, Linux, Android, and iOS app/universal links plus browser fallback.

## Product boundary

Both implementations should support semantic parity for local dataset import, query/transform workflows, chart/dashboard authoring, keyboard-heavy analysis, multi-window inspection, exports, saved workspaces, offline operation, recovery, and deep links.

Stable schemas, query/result formats, visualization specs, route fixtures, sample datasets, performance baselines, and conformance tests must be shared deliberately.

## Repository creation requirements

Both repositories must begin as buildable scaffolds, not placeholders. The Rust repo must include `docs/DESKTOP_TOOLKIT.md`, reciprocal README/AGENTS/PR guidance, native CI/package skeletons, smoke tests, accessibility checks, and shared contract fixtures.

Central toolkit assignments are maintained in the approved private registry at `private-registry://canonical/registry/rust-desktop-strategies.md`; public repositories must not expose its backing repository locator.

## Project routing

- GitHub Project: [`claritas-viz-project` — Project 1](https://github.com/orgs/claritas-viz/projects/1)
- Linear project: `github.com/claritas-viz`
- Central registry: [`approved-private-registry`](private-registry://canonical/registry/desktop-applications.json)
- Portfolio rollout: [`DEN-2469`](https://linear.app/denman/issue/DEN-2469/roll-out-paired-rust-flutter-desktop-repositories-across-the-portfolio)

Repository creation, toolkit/renderer changes, deep-link changes, renames, transfers, archival, or platform-status changes must update this document, the central registry/strategy, Linear, and both companion repositories in the same delivery.
