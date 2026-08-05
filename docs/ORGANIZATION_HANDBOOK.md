# claritas-viz organization handbook

> Shared operating defaults for repositories maintained under **claritas-viz**. Repository-local policy may strengthen these rules but should not silently weaken them.

## Mission

claritas-viz maintains analytics, reporting, and data-visualization software. This `.github` repository is the canonical home for organization-wide community health files, reusable templates, engineering policy, and planning links.

## Repository contract

Each active repository must document purpose, ownership, maturity, supported environments, development and test commands, authoritative schemas and transformations, release and rollback procedures, compatibility policy, and GitHub Project/Linear links. Visualization components should also document data provenance, aggregation semantics, units, missing-data behavior, accessibility, privacy boundaries, performance limits, and interpretation caveats.

## Change and review workflow

1. Anchor work in an issue, Linear item, or documented maintenance objective.
2. Keep branches and pull requests focused.
3. Explain motivation, scope, data and user impact, validation, compatibility, migration, and rollback.
4. Test empty, missing, extreme, malformed, high-volume, responsive, and accessible states as relevant.
5. Resolve conflicts semantically by reconstructing both sides' intent.
6. Prefer squash merges for focused work unless commit structure materially improves auditability.

## Evidence and quality

Pull requests should include reproducible commands, sanitized fixtures, expected and observed results, visual or snapshot evidence where useful, negative-path coverage, documentation updates, and CI or local-equivalent evidence. Metric or aggregation changes require comparison against trusted baselines and clear interpretation of changed outputs.

## Security and data

Never commit credentials, private datasets, customer reports, production identities, or sensitive logs. Use synthetic or irreversibly sanitized fixtures. Follow `SECURITY.md` for private vulnerability reporting and pin dependencies and actions where reproducibility or supply-chain integrity matters.

## Documentation and decisions

Keep examples executable and sanitized, links current, assumptions explicit, units consistent, and interpretation boundaries clear. Record architectural, metric, privacy, accessibility, compatibility, and operational decisions that future maintainers would otherwise have to rediscover.

## Planning ownership

GitHub owns code, reviews, checks, releases, and delivery evidence. Linear owns priority, dependencies, sequencing, and cross-project planning. The organization GitHub Project is the cross-repository execution view; see `PROJECTS.md` for routing details.

## Organization health

- [ ] Profiles, descriptions, topics, and READMEs are current.
- [ ] Contribution, security, support, governance, issue, and PR guidance is present.
- [ ] Metrics, transformations, units, provenance, and interpretation limits are documented.
- [ ] Required checks reflect correctness, accessibility, privacy, performance, and supply-chain risk.
- [ ] Stale repositories are archived or clearly marked.
- [ ] Project links resolve and completed work is reflected in GitHub and Linear.
