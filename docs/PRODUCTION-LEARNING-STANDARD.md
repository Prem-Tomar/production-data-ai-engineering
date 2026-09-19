# Production Learning Standard

This standard defines the work required to complete each project milestone. Apply the relevant sections progressively; do not turn Lab 01 into a full cloud platform.

Use the [learning rules](LEARNING-RULES.md) for daily issue scope. Technology depth, ETL/ELT, production deployability and independent interview practice are cumulative project requirements. Daily implementation tasks build toward these gates; they do not each require a complete milestone report.

## 1. Understand the problem

Explain the consumer, business outcome, input contracts, expected output and correctness rules. State what is known and what is assumed. Translate terms such as reliable, fast and scalable into measurable requirements.

For financial data, explicitly define identifiers, trade versions, cancellations, decimal precision, currencies, time zones, late arrivals and reconciliation rules. Avoid inventing production banking requirements: declare the synthetic scenario's assumptions.

## 2. Design before adding complexity

Draw the components, data flow, trust boundaries and dependencies. Compare at least two credible approaches for consequential decisions. State transaction boundaries, retry behavior, ownership and resource limits. Save a short [architecture decision](../templates/architecture-decision.md).

Prefer the simplest design that satisfies the declared workload. Introduce distributed processing, streaming or agents because a requirement needs them, then measure the result.

## 3. Implement reproducibly

Version code and dependencies. Provide clear setup/run instructions, example configuration without credentials, and repeatable small synthetic fixtures. Separate application logic from infrastructure and external-service adapters. Use meaningful types, explicit errors and clear resource ownership.

Python knowledge must be visible in the implementation: correct data structures, testable interfaces, generators when useful, deliberate concurrency, safe cleanup and measured optimization. Advanced language features need a reason.

## 4. Verify correctness

Test business invariants, boundary cases and integrations. Test duplicates, missing values, out-of-order updates, invalid records and relevant schema changes. Compare results against a known reference. Explain what each test protects and what remains untested.

Automate repeatable checks in CI as the code appears. Do not write empty tests or claim coverage before an implementation exists. Keep environment-dependent integration tests distinguishable from fast local tests.

## 5. Exercise failure and recovery

Inject realistic failures in the lab: terminate a worker, time out a source, reject credentials, interrupt a write, make a dependency unavailable or deploy a bad version. Observe whether the system retries safely, avoids silent data loss and exposes actionable information.

Perform restart, replay, rollback and eventually clean-environment restore. Measure recovery time and recovered data. Use the [runbook template](../templates/runbook.md) and [incident template](../templates/incident-review.md). A successful backup job alone is not evidence that restoration works.

## 6. Measure service behavior

Record workload size, distribution, hardware, software versions and relevant configuration. Report correctness alongside latency, throughput, peak memory and cost. Compare before/after under equivalent conditions and retain unsuccessful experiments when they explain a decision.

Introduce service objectives and monitoring once the service exists. Define request/event populations and observation windows. Distinguish a short lab run from evidence of long-term production availability.

## 7. Apply AI-specific checks

Before adding AI, define a baseline that does not need a model. Version evaluation questions, document sources, prompts, model settings and retrieval configuration. Keep tuning and held-out evaluation separate.

Evaluate retrieval, answer correctness, source support, abstention, access isolation and task completion separately. Test document changes, model timeouts, prompt injection in retrieved material and bad tool calls. Enforce permissions in code/services independently of model instructions. Bound retries, tool steps, token use and cost; make failure visible to the user.

## 8. Review and explain

Demonstrate an unfamiliar variation, explain a failed design and describe what would change at higher scale. Have another engineer review the key milestone or explicitly record that independent review remains open.

Use the [evidence template](../templates/milestone-evidence.md). Each required item should link to code, a command/result, a measured report or a review record. Replace vague claims such as enterprise-grade with observable behavior and known limits.

## Progressive gates

Apply the [technology depth requirements](TECHNOLOGY-DEPTH.md) progressively: explain the selected technology's behavior, expose a relevant edge case and demonstrate its handling. At milestone review, record version-specific limits, an unfamiliar variation and justified trade-offs. Do not add every depth experiment or a documentation deliverable to each beginner issue.

Production deployability is a required final outcome. The [deployment acceptance gates](PRODUCTION-DEPLOYMENT.md) require working infrastructure and release automation, secure configuration, migrations, monitoring, rollback and measured restore evidence. A successful local command or a written architecture does not pass that gate.

| Gate | What must exist |
|---|---|
| Foundation | Reproducible local program, correct results, meaningful tests and explained error handling |
| Data pipeline | Contracts, reconciliation, replay/backfill and documented recovery |
| Cloud/platform | Repeatable deployment, identity controls, operational visibility and cost evidence |
| AI solution | Evaluated behavior, source/permission handling, controlled tools and release checks |
| Reliability | Service objectives, observed operation, failure drills and measured restore |
| Production deployment | Reviewed deployment gates, identified release artifact, tested staging promotion and recovery, and concrete production configuration; actual production deployment recorded separately |
| Expert practice | Independent extension/debugging, peer review, reusable software and defensible architecture |

Record milestones as planned, implementing, evidence-ready, reviewed or complete. Use complete only after the applicable criteria pass. Real production ownership remains a separate evidence field.
