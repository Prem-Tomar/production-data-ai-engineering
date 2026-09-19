# Production deployment target and release gates

## Required outcome

The completed platform must be deployable to an approved production environment from version-controlled code and configuration. A release must have an identifiable artifact, repeatable deployment, controlled access, observable operation, a safe upgrade path and tested recovery. Documentation alone does not satisfy this target.

Current status: the repository contains a learning plan and assignments. Application code, infrastructure, deployment workflows and production evidence remain to be implemented. The first 30 issues establish a local ingestion foundation; they do not complete these release gates.

Production deployability and a live production deployment are separate evidence fields. Build and test the deployment path in development and staging, then use it for production only when the environment, budget, data access and operational ownership are approved. Real production operation is not inferred from a staging demonstration.

## Deployment design to implement

Use AWS as the default cloud and Databricks/Delta Lake for the planned distributed data platform. Choose the specific application compute, database, network, orchestration and infrastructure tools during the cloud design milestone. The decision must name where each component runs, its identity, persistent data, dependencies, scaling bounds and monthly cost assumptions. Use one cloud; an approved alternative must meet the same release gates.

Promote an identified release through development, staging and production with separate identities, secrets and data. Staging must exercise the production deployment mechanism, database migrations and dependency integrations at a declared test scale. Record differences that can affect behavior or recovery.

Build once and promote the same versioned application artifact. Keep environment settings outside that artifact. Version data transformations, database migrations, prompts, model settings and retrieval-index configuration with the release as applicable. Every deployment must identify both the software and configuration being operated.

## Acceptance gates

| Gate | Required implementation | Observable acceptance evidence |
|---|---|---|
| Reproducible build | Declared runtime/dependencies, built package or container, versioned artifact and source revision | Clean CI runner builds and checks the release; staging runs the identified artifact rather than an ad hoc source checkout |
| Environment provisioning | Versioned infrastructure with separate environments, reviewed plans and explicit persistent resources | Recreate a clean staging environment; list remaining approved manual bootstrap steps; inspect teardown before executing it |
| Identity and secrets | Service identities with required permissions only, managed secrets, network restrictions and encryption settings | Denied-access cases fail correctly; rotate a credential; show that source, artifacts and logs contain no secrets |
| Database evolution | Ordered schema migrations, compatible rollout sequencing and data reconciliation | Upgrade a populated staging database; interrupt a migration; recover without unexplained loss or corruption |
| Deployment workflow | Automated deployment of the chosen artifact, health/readiness validation and an explicit production promotion step | A bad release cannot be reported as healthy; the workflow identifies the deployed revision and records success or failure |
| Safe execution | Graceful shutdown, bounded retries/timeouts/concurrency, resource limits and source ownership | Stop or overload a worker; it releases resources and resumes without silently skipping required events; overlapping workers have a defined policy |
| Data correctness | Event contracts, duplicate/conflict handling, replay, quarantine and reconciliation | Release checks demonstrate expected state and per-currency totals after normal processing, replay and interruption |
| Monitoring and support | Run/job metrics, actionable errors, freshness/lag visibility, alerts and an owner/runbook | Inject a failure, observe the signal, verify alert routing and follow the recovery procedure |
| Backup and restore | Declared backup scope/retention, protected backups and restoration automation | Restore data and required configuration into a clean environment, reconcile results and measure recovery time/data loss against chosen targets |
| Rollback and forward repair | Previous artifact retained; compatible schema and configuration strategy; explicit irreversible-change handling | Rehearse a bad application/configuration release and recover; explain why application rollback alone cannot undo every data migration |
| Security and dependencies | Dependency/image checks, access tests, patch/upgrade policy and tracked findings | Review findings for the exact release, resolve release-blocking findings or record an approved bounded exception; verify authorization outside model prompts |
| Capacity and cost | Workload assumptions, load results, service quotas, scaling limits and a budget owner | Meet chosen latency/freshness targets under declared load, handle overload, compare observed costs with estimates and define stop/scale thresholds |
| AI release checks — when AI is added | Versioned held-out evaluation, permission/source checks, bounded tools and fallback behavior | Model/prompt/index changes pass declared quality gates; unavailable models and unauthorized retrieval fail safely without bypassing controls |
| Operational handover | Named service/data owner, release procedure, incident route and outstanding risks | Another engineer can deploy and recover the release in staging using the supplied instructions; production approval and support ownership are recorded separately |

Choose concrete service objectives, recovery targets and acceptance thresholds from the declared workload before assessing a release. The roadmap's suggested lab measurements are starting hypotheses. Use the [technology depth requirements](TECHNOLOGY-DEPTH.md) to expose assumptions in each component's guarantees.

## Delivery sequence

1. **Foundations, months 1–2:** Implement the runnable ingestion program, local database behavior, tests, packaging and CI. Keep initial learning increments small.
2. **Reliable pipeline, months 3–5:** Add recoverable processing, schema evolution, reconciliation and runbooks. Identify the persistent state and transaction boundaries that deployment must protect.
3. **Cloud/platform, months 6–8:** Implement infrastructure, artifact promotion, identity, database migration and deployment/rollback workflows. Deploy the data release to staging and assess every applicable gate above. Gaps remain open with a concrete follow-up issue.
4. **Applied AI, months 9–11:** Extend that same deployment path to the retrieval and AI components, including their quality, permission and dependency-failure checks.
5. **Reliability, months 12–14:** Exercise restoration, overload, alerts and bad-release recovery; collect the planned observation evidence and close remaining operational gaps.
6. **Production transfer, months 15–18:** Independently reproduce deployment and recovery, review the release gates, and deploy to an approved production environment when access and ownership exist. Without that access, retain a reproducible production deployment package and mark live deployment/operation as pending.
7. **Sustained ownership, months 19–24:** Repeat the gates for upgrades, breaking changes and workload growth; preserve the ability to build, deploy and recover after maintenance changes.

These are progression targets, not permission to defer safety-critical controls for a deployed release. Any earlier production deployment must pass all gates applicable to its components and workload. A component that is not yet shipped can be marked not applicable with a reason, never silently omitted.

## Release evidence record

Use the [milestone template](../templates/milestone-evidence.md) to record release ID, source revision, artifact identifier, environment, configuration/migration versions, gate outcomes and links to actual deployment and recovery runs. Each gate is pass, fail, not run or not applicable with a reason. Record who reviewed release readiness and which risks remain.

Mark a release **production-deployable** only after the applicable gates pass with reviewed staging evidence and a concrete production configuration. Mark it **deployed to production** only after the approved deployment succeeds and post-deployment checks pass. Record observed production operation separately, with its actual workload and duration.
