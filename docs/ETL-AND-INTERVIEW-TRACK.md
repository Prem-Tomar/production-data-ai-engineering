# ETL, ELT and interview preparation

## Working outcome

Build and explain a complete financial-data pipeline from source extraction to reconciled analytical tables. ETL means extract, transform, then load; ELT loads source data first and performs transformations in the target platform. Implement both patterns on a bounded synthetic workload and justify the chosen placement of each transformation.

This extends the [30-day coached Python and local ETL foundation](PYTHON-COACHING.md) through the preserved pipeline backlog and months 3–8; it is not an extra 30-day promise. The requirements are informed by the [job-opening analysis](JOB-REQUIREMENTS-2026-09.md) and remain part of the existing weekly budget.

## Implementation sequence after the foundations

Split each row into small issues using the [learning rules](LEARNING-RULES.md). The row is a capability and can take several issues; it is not one oversized daily assignment.

| Capability | Small changes to build in order | Nuance to demonstrate | Interview exercise |
|---|---|---|---|
| Extraction | File/API source; relational snapshot; incremental source reader | Consistent snapshot, cursor stability, ties in watermark values, source deletes and unavailable sources | Design an extract when updates share timestamps and the job fails halfway |
| Transformation | Normalize values; enrich trades with instrument/account data; calculate agreed measures | NULL handling, invalid joins, duplicate lookup keys, rounding and event/business time | Find why a join doubled a monetary total |
| ETL versus ELT | Transform before loading one result; reproduce it from raw staging with SQL | Reprocessing cost, auditability, pushdown, sensitive fields and source/target load | Choose where to transform under different volume and governance constraints |
| Loading | Append history; merge current records; load fact/dimension tables | Keys, transaction boundaries, partial batches, deletes and repeat runs | Explain how retrying a load avoids changing correct results |
| CDC and incremental state | Watermark prototype; log/change-feed exercise where available; delete handling | Change data capture (CDC), ordering, commit position, missed updates and schema drift | Compare polling with log-based capture and identify each failure boundary |
| Warehouse modelling | Declare fact grain; build dimensions; add type-1 and type-2 changes | Surrogate/business keys, validity intervals, late facts and historically correct joins | Model a trade whose account classification changes after booking |
| Quality and reconciliation | Source/target counts; currency totals; rejected-record accounting; correction replay | A matching row count can hide incorrect amounts or duplicated identities | Diagnose balanced counts with wrong exposure totals |
| Orchestration | Dependency graph; retries; backfill; overlapping-run control | Scheduled interval versus wall clock, timezone boundaries and retry side effects | Recover one failed date without rerunning or corrupting unrelated dates |
| Storage and performance | Parquet conversion; partition/file-size experiment; Spark version of one SQL model | Compression, predicate/column pruning, skew, small files and driver memory | Diagnose a slow join from a plan and measurements |
| Governance | Source-to-target mapping; dataset ownership; lineage; permission checks | Meaning of a metric, provenance of one result, row/column access and retention | Explain a disputed metric and locate its source/version |
| Migration | Synthetic PL/SQL-style reference; shadow run; reconciled cutover rehearsal | Vendor semantics, compatibility, rollback and dual-run disagreements | Defend cutover criteria and a recovery path |
| Delivery | Package jobs; deploy to staging; validate release and restore | Source configuration, secrets, migrations, immutable artifacts and safe recovery | Walk through a bad release and identify what rollback can and cannot undo |

Required completion evidence: known-input outputs, repeat/replay correctness, incremental-versus-full comparison, historically correct dimension joins, invalid-record handling, measured performance and a recoverable deployment. Add these at their dedicated test and milestone reviews.

## Interview practice without replacing learning

During the first month, spend most practice time writing and debugging the project. Finish each increment by running a changed-input or failure case with a concrete expected result. Use brief spoken discussion only to resolve what the code revealed; no theory answers are required. Revisit a completed concept through an unseen coding variation during the weekly review. This requires no extra document or automated test on every issue.

From month 4, use two sessions within the 15–20 weekly hours: one timed coding/SQL exercise and one design/debugging or behavioral mock. Reduce other planned work by the same time. The durations below are practice targets chosen for this track, not claimed employer interview formats.

| Practice area | Exercise | Readiness signal |
|---|---|---|
| Python and useful algorithms | 30–45 minutes: parse, group, deduplicate or merge an unseen event stream; explain time/memory complexity | Correct handling of boundary cases and a reasoned data-structure choice without copied code |
| SQL | 30–45 minutes: windows, joins, NULLs, top-N, interval/as-of joins and reconciliation | Correct results on counterexamples and an execution-plan discussion |
| ETL incident | 30 minutes: late updates, failed checkpoint, changed schema or duplicate batch | Reproduce the fault, protect invariants and propose a safe correction/backfill |
| Spark | Inspect a plan and diagnose shuffle, skew or memory pressure | Explain a measured fix and why it preserves results |
| System/cloud design | 45–60 minutes: requirements, scale, architecture, failure paths and cost | Defend two viable approaches, identity boundaries and recovery targets |
| Applied AI | Design retrieval/evaluation and a restricted data-query workflow | Distinguish retrieval from answer quality and explain permission enforcement and fallback |
| Leadership and domain | Explain a migration, incident, disagreement or mentoring decision | Truthful personal ownership, stakeholder impact, alternatives and verified results |

Build a rotating question bank from observed gaps. Do not memorize fixed answers or present project work as professional tenure. Once a learner can solve an exercise, change the constraints, input distribution or failure point.

## Readiness gate for a target role

Map the specific posting's required skills to evidence before applying. Use the roadmap's proficiency rubric; leave scores blank until assessed. Separate hard experience/education constraints from trainable skills and identify role-specific tool gaps.

Pass two independent mock interviews using different exercises. Record correctness, explanation, debugging, trade-offs and remaining gaps, then repeat weak areas with new problems. If no reviewer is available, label the session self-assessed and keep independent review open. This is a preparation standard, not a hiring guarantee.

## Initial backlog and later coverage

Days 1–10 coach execution, basic types, decisions, collections and loops. Days 11–20 develop functions/scope, shared state, debugging, errors, modules, decimal/time handling and file/JSON input. Days 21–30 add generators, dataclasses, late-bound closures, testing, a configurable local ETL command and an independent check. The original database, replay, recovery, API, packaging and CI assignments remain in [PIPELINE-BACKLOG.md](PIPELINE-BACKLOG.md) as subsequent implementation work. Analytical modelling, CDC, orchestration, cloud deployment and interview readiness retain their later gates.
