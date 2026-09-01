## Purpose

Describe the problem, intended behavior, user-visible impact, and why this repository owns the change. Link the Linear issue and cross-repository dependencies.

## Review path

- [ ] All commits are on a topic branch and this pull request is the only proposed path into the protected default branch.
- [ ] No generated tool, bot, migration runner, or deployment process writes directly to `main`, `dev`, `master`, or another protected branch.
- [ ] The change is focused enough to review, or its staged rollout and follow-up pull requests are identified.
- [ ] Cross-repository dependencies are pinned by immutable commit, lockfile, or released Zed package.

## Scope and ownership boundaries

- [ ] The change does not silently cross repository ownership boundaries.
- [ ] No `*-infra` repository is introduced as a Git submodule under `*-monorepo/apps`.
- [ ] Shared functionality is imported from its owning repository rather than copied into a new local implementation.
- [ ] Public contracts, compatibility, rollback, telemetry, and fail-closed behavior are documented.

## Contracts, SQL, and migrations

- [ ] TypeSpec, Protobuf, JSON Schema, generated Rust/Dart/TypeScript interfaces, Diesel models, SeaORM entities, fixtures, and migrations were updated and checked together where applicable.
- [ ] SQL declarations use the registered logical namespace `<organization>.<domain>` and stable `<domain>_` object prefixes when a shared PostgreSQL schema is required.
- [ ] Domain SQL may remain in its owning repository, while identity, ordering, checksums, drift detection, and promotion are registered through `declarative-migrations`.
- [ ] Application startup validates schema compatibility and does not apply production DDL.
- [ ] Destructive changes include compatibility, backfill, rollback, tenant-isolation, row-level-security, and state-machine evidence.

## Infrastructure and security

- [ ] Application manifests remain app-owned; shared cluster composition stays with `oresoftware/k8s-cluster` and reusable cluster components with `oresoftware/k8s-libs-and-shared-defs`.
- [ ] Workload identity, restricted Pod Security, default-deny networking, explicit egress, probes, bounded resources, non-root execution, and immutable images were considered where applicable.
- [ ] Secrets, credentials, customer data, personal data, private-repository inventory, and user content are excluded from source, logs, fixtures, telemetry, and build artifacts.
- [ ] Authentication and authorization fail closed; sensitive operations preserve tenant boundaries and auditable correlation.

## Verification and observability

- [ ] Zed lifecycle hooks run deterministic format, lint, build, contract, test, and publish checks without replacing language-native validation.
- [ ] Unit, integration, adversarial, migration, accessibility, performance, and end-to-end tests cover the changed behavior in the corresponding `*-test` organization or an isolated environment.
- [ ] Destructive or cross-runtime tests include bounded setup and teardown evidence.
- [ ] ORES OTEL trace and correlation propagation is present where applicable, with secret and user-content capture disabled by default.

List exact commands, workflow runs, fixtures, migration or drift results, manual verification, residual risks, and every check that could not run.

## Conflict and delivery safety

- [ ] Conflicts were resolved semantically after reading both complete sides, relevant history, tests, schemas, generated artifacts, and cross-repository contracts.
- [ ] No force push, rebase, destructive reset, history rewrite, branch deletion, review bypass, or required-check bypass was used.
- [ ] The working change contains no unresolved conflict markers or unrelated edits.
- [ ] Roll-forward and rollback expectations are explicit, and intentionally deferred work is linked.