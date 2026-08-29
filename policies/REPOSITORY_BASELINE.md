# Repository hardening baseline

<!-- ore-org-baseline:begin -->
The public `.github` repository supplies only GitHub-supported fallback files. It does not inject arbitrary agent instructions or workflow files into sibling repositories.

Each active repository should therefore maintain:

- a local lowercase `agents.md` derived from this policy plus repository-specific constraints;
- provider mirrors or pointers as required by the tools used in that repository;
- explicit least-privilege workflow permissions and job timeouts;
- full commit-SHA pins for external Actions;
- checkout with `persist-credentials: false` unless a reviewed write step proves it is necessary;
- tests appropriate to the repository's language and risk;
- branch/ruleset controls that prevent force pushes and branch deletion;
- vulnerability alerts and automated security fixes where supported;
- a linked GitHub issue or pull request for material Linear architecture or policy changes.

The selectable workflow template is standalone and uses immutable external Action pins. A repository that calls `.github/workflows/reusable-policy.yml` directly must pin the call to a reviewed full commit SHA of `claritas-viz/.github`; do not use a mutable branch or tag for enforcement.

Account administrators should separately review organization-wide Actions policy, default `GITHUB_TOKEN` permissions, approval of forked workflows, repository creation permissions, rulesets, GitHub App scopes, secret scanning and push protection, private vulnerability reporting, audit-log access, and emergency break-glass procedures. Those settings cannot be enforced merely by committing files to this repository.

## Operator constraints (GitHub Free, 2026-08-28)

These cannot be enforced by files in this repository and must be kept in the GitHub org UI/API:

- Organization rulesets and classic branch protection on **private** repositories require GitHub Team/Pro. Public `main` branches are protected (no force-push, no deletion, `enforce_admins`).
- `members_can_create_public_repositories=false` is rejected on Free organizations. Keep new product work private by convention.
- Organization 2FA requirement did not persist via the REST API; enable it in the org security settings UI.
- SHA pinning for Actions (`sha_pinning_required`) should be turned on only after every workflow on `main` uses a 40-character commit SHA. Mutable tags (`@v4`) will fail closed once that org flag is enabled.
- Rebase merges are disabled; merge commits remain the default so history stays append-only.
<!-- ore-org-baseline:end -->
