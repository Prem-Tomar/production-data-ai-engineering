# Contributing

## Ownership

Only @Prem-Tomar may push to or merge into `master`. Developers can fork this public repository, create a feature branch in their fork and open a pull request targeting `master`; the owner reviews and performs the merge. Invited collaborators can also use feature branches in this repository.

**Enforcement status:** The repository is public at the owner's request. GitHub ruleset `master-owner-only` is active. No collaborator, team, application or deploy key was added to its bypass list.

## Server-side rule

An active branch ruleset targets `refs/heads/master`, restricts creation, updates and deletion, and blocks non-fast-forward changes. Only the repository-admin role has bypass rights. In this personal-account repository, the owner is the administrator and ordinary collaborators do not have that role. Reassess this configuration before any transfer to an organization or change in ownership/access model.

The update restriction applies to both direct pushes and PR merges. Feature branches remain available to invited collaborators, and other developers can submit fork-based PRs. No developer accounts have been invited during initial setup.

## Pull-request contents

Use neutral topic-based branch names such as `docs/learning-conventions` or `feature/trade-validation`. Use project terminology in commit messages, issue links and pull requests; omit assistant/tool branding and attribution trailers. Link to merged documentation on `master` or an appropriate stable revision rather than a temporary branch.

- State the learning objective and behavior change.
- Link acceptance criteria and evidence.
- Describe tests actually run and failures investigated.
- Include relevant design, recovery and performance/cost findings.
- State unresolved limitations and whether evidence is from a lab or real operations.

Keep PRs small enough to review. Use synthetic data and example configuration without credentials. Do not commit raw resumes, real banking data, cloud credentials or machine-local state.

For code changes, demonstrate understanding by explaining the design and handling a reviewer-requested variation. Leave merge and master updates to the owner.
