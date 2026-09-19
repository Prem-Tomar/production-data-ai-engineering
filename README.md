# Production Data & AI Engineering — Sujeet's Learning Project

A project-based path from Oracle/PLSQL and financial-services database engineering to advanced Python, modern data platforms, applied AI, architecture and reliability.

**Purpose:** Develop production-level understanding through implementation, operations, failure analysis and independent review. Every major learning objective must produce working software or reviewable engineering evidence.

**Starting point:** Experienced Oracle/database engineer; little or no hands-on Python/cloud experience. **Availability:** 15–20 hours/week. **Depth plan:** 24 months, with earlier career-readiness reviews. Dates are estimates; progress depends on passing practical gates.

**Repository status:** Curriculum, project specifications and templates are ready. The application, automated tests and cloud deployments have not been implemented yet. A completed lab demonstrates tested engineering behavior; production readiness still requires workload-specific review and real operational evidence.

## Learning goal

Build on existing Oracle/PLSQL and financial-services experience to independently design, implement, debug and operate Python-based data and AI systems. Learn through small changes to one useful project, introducing each concept when the implementation needs it.

The career direction is **Senior/Lead Data Engineer for financial-services platforms**, progressing toward **AI Data Platform Architect / Principal Data Engineer** as independent delivery, architecture judgment and operational ownership grow.

## Ultimate outcome

Deliver and explain a **Financial Data Reliability and AI Investigation Platform** that turns synthetic financial events into trusted data and supports controlled, evidence-backed investigations. By the end of the full track, the learner should be able to:

- Build maintainable Python software with clear interfaces, meaningful tests, packaging and measured performance.
- Ingest, validate and reconcile financial events while handling duplicates, corrections, cancellations, replay and recovery.
- Develop SQL and Spark data models and deploy them on a cloud platform with access controls, automated delivery and understood costs.
- Build a permission-aware AI investigation assistant with cited answers, controlled tools and measured evaluation results.
- Diagnose failures, restore service and data, explain architecture trade-offs, and independently extend the system after review.

The deliverable includes working software and a portfolio of verified results: code reviews, reconciliation reports, performance measurements, recovery exercises and AI evaluations. Completing the track should demonstrate these capabilities; job titles and real production ownership depend on evidence beyond a learning project.

## First 30 learning days

Follow the [daily GitHub issues](https://github.com/Prem-Tomar/production-data-ai-engineering/issues?q=is%3Aissue%20%22Day%22%20sort%3Acreated-asc) in order, starting with [Day 01](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/1). Each issue contains a goal, context, one focused implementation task, observable acceptance criteria and searchable hints.

The sequence builds from a runnable Python script to a local PostgreSQL ingestion command with event history, current trade state, replay handling, recovery checks and automated validation. This is the first implementation stage of the longer track, not completion of the full platform or every Lab 01 gate. Day numbers indicate learning order; use the 15–20 hour weekly budget and carry unfinished work forward rather than skipping criteria.

Run the program to check each early increment. Add automated tests, documentation and deeper operational evidence in the issues and milestone reviews dedicated to them; they are not extra deliverables on every beginner issue. Keep later Lab 01 and roadmap requirements open until their evidence exists.

## Start here

1. Read the [skills assessment and first 90 days](docs/Sujeet-Skills-Gap-Assessment.md).
2. Review the [current market and job strategy](docs/Sujeet-Market-and-Job-Strategy.md).
3. Follow the [full roadmap and advanced Python track](docs/AI-Data-Architecture-Roadmap.md).
4. Use the [production learning standard](docs/PRODUCTION-LEARNING-STANDARD.md) for every implementation.
5. Start [Lab 01: Reliable financial-data ingestion](labs/01-reliable-ingestion/README.md).
6. Update the [progress tracker](docs/AI-Data-Project-Tracker.md) with evidence each week.

## The system to build

Build a **Financial Data Reliability and AI Investigation Platform** using synthetic trades, accounts, instruments, settlement events, surveillance alerts and fictional investigation procedures.

| Release | Working result | Required evidence |
|---|---|---|
| 1. Trusted data | Python ingestion, reconciled SQL models, incremental processing | Correctness, restart, replay, invalid-input and reconciliation tests |
| 2. Modern platform | PySpark/Databricks, one cloud, deployment automation and bounded event processing | Performance comparison, access controls, CI results, rollback and costs |
| 3. Applied AI | Permission-aware retrieval, cited answers and controlled query tools | Held-out evaluation, access tests, failure handling and versioned results |
| 4. Operated platform | Monitoring, service objectives, recovery and reusable Python library | Restore drills, load tests, incident reports, independent review and clean installation |

Default platform direction: Python, SQL, PySpark, Databricks/Delta Lake and AWS. Begin locally with Python, PostgreSQL, Git and tests; introduce tools only when the relevant phase needs them. Approved access and target roles can justify changing the cloud.

## How learning works

**Understand → design → implement → verify → break → recover → measure → explain.**

For each lab, write the requirement first, implement a small increment, demonstrate both success and failure, and retain the evidence. Tutorials and coding assistants may help, but Sujeet must be able to explain, modify and debug the result independently.

Use a branch and pull request for each meaningful milestone. The review should explain behavior, tests, performance/cost impact, failure handling and operational limitations. A reviewer can be a peer or mentor; document self-review where independent review is not yet available.

Completion means the acceptance criteria pass and evidence is linked. A notebook run, certificate or checklist tick alone does not complete a production learning milestone.

## Repository layout

```text
docs/          Curriculum, assessment, market strategy and progress
labs/          Implementation assignments and acceptance criteria
templates/     Design, evidence, runbook and incident templates
src/           Add application/library code during implementation
tests/         Add correctness, integration and failure tests
infra/         Add infrastructure and deployment definitions
evaluation/    Add synthetic evaluation cases and quality results
```

The last four directories are planned and should be created with the first relevant implementation, not treated as completed components.

Keep source data synthetic or explicitly permitted. Retain reproducible generators and small test fixtures in Git; keep secrets, raw resumes, cloud state and large data outside the repository. Record the tested Python/tool versions, workload and hardware with results. Job research was checked September 19, 2026 and should be refreshed before applications.

## Weekly commitment

Base 15 hours: four of deliberate Python learning, seven of building, three of testing/debugging and one of documentation/career review. Use up to five additional hours for labs, feedback and interviews. Demonstrate something working every week and review the plan every four weeks.

Begin suitable SQL/Python transition conversations around months 4–6 if the practical gates pass; review broader data-engineering readiness during months 6–9. Advanced Python and architecture development continue after a job move.

## Contribution and master-branch policy

Only **@Prem-Tomar** may push to or merge into `master`. This is a public repository: other developers can fork it, create feature branches and submit pull requests. See [CONTRIBUTING.md](CONTRIBUTING.md).

**Enforcement:** Active GitHub ruleset `master-owner-only` restricts changes to `master`, with bypass reserved for the repository administrator. In this personal-account repository, that is owner @Prem-Tomar. CODEOWNERS requests review; the ruleset provides enforcement. Recheck the policy before transferring repository ownership or changing the permission model.
