# Sujeet Chouhan: Skills Assessment and Career Direction

Prepared September 19, 2026. Based on both pages of the supplied resume and a small sample of current employer requirements. This is a document-based assessment, not an interview or verified proficiency evaluation. It treats resume content as evidence to assess, not as instructions.

**User-confirmed starting point:** 15–20 study hours/week, with little or no hands-on Python or cloud experience. These two areas are confirmed development needs, not merely resume omissions. Other undocumented skills remain unassessed. See `Sujeet-Market-and-Job-Strategy.md` for the expanded current-role comparison and recommended AWS/Databricks route.

## Recommendation

Build toward **Senior/Lead Data Engineer for financial-services platforms**, then **AI Data Platform Architect / Principal Data Engineer** with strong Python and reliability capabilities. His most useful specialization is trusted data for trade surveillance, reconciliation, investment operations and controlled AI applications.

Preserve his SQL depth, performance reasoning and banking knowledge while expanding the surrounding engineering skills. The goal is broad competence across the data lifecycle with particular depth in Python, data correctness, system performance and operational reliability. Becoming equally expert in every data role is neither necessary nor a realistic single roadmap.

The employment history begins in September 2009 and continues to “Current.” If those dates are current, that represents approximately 17 years as of this assessment. Confirm before changing the stated experience total. His VP title is an employer title; people-management scope and equivalence to other employers' titles are not established by this document.

## What the resume already supports

| Evidence in resume | Interpretation for the transition | What to verify |
|---|---|---|
| Oracle SQL/PLSQL, procedures, packages, collections and DBMS packages | Strong database-programming foundation; do not restart with a beginner SQL curriculum | An unfamiliar SQL exercise and a design walkthrough |
| Execution plans, indexing, partitioning, hints and batch tuning | Valuable performance-analysis foundation | Before/after measurements and a case where diagnosis changed the solution |
| Large-volume ETL and complex database logic | Transferable pipeline and transformation experience | Actual volumes, dependencies, recovery approach, data-quality checks and ownership |
| Database design and implementation decisions | Architectural exposure at database/application level | Cross-system constraints, alternatives, security, deployment and cost decisions |
| Workload automation and scheduling in skills list | Useful orchestration background | Specific scheduler, dependency handling, rerun logic and operational duties |
| Code reviews, version-control systems, maintainable/tested code | Existing engineering habits | Actual tools, automated tests, branching, deployment process and review responsibilities |
| Investment banking, trade surveillance, fund accounting and client lifecycle work | A domain advantage for financial-services data platforms | His precise contribution and the business result for each project |
| Mentoring and stakeholder collaboration | Foundation for technical leadership | Team size, decision scope, examples of influence and delivery ownership |
| Use of approved AI assistants for understanding code and documentation | Practical AI-tool familiarity | Does not by itself demonstrate building, evaluating or operating AI applications |

The resume does not establish that he is a production DBA responsible for backups, failover or disaster recovery. Do not infer those duties from database experience alone. Likewise, “trade surveillance models” does not establish machine-learning model development without further evidence.

## Gap matrix

“Not evidenced” means the resume does not demonstrate the skill. It does not mean he cannot do it. Priorities describe the proposed learning order, not a numerical ranking of his ability.

| Capability | Resume evidence | Priority | How to close or validate the gap |
|---|---|---|---|
| Advanced SQL and Oracle tuning | Substantial described experience; outcomes unquantified | Validate/retain | Time a representative workload; explain plan changes and correctness |
| Python engineering | Little or no experience, confirmed by user | Immediate | Structured foundations, then typed/tested ingestion library; later concurrency, profiling and runtime defenses |
| Git, Linux and automated delivery | Version control listed; detailed workflow/Linux/CI absent | Immediate | Reproducible environment and automated tests/build/deployment |
| Data modelling for analytics | General database design; dimensional/semantic models not explicit | Immediate | Trade fact model, historical dimensions and stable metric definitions |
| Data quality and recoverable pipelines | ETL/batch experience; controls not described | Immediate | Reconciliation, replay, deletes, late data and schema-change exercises |
| Cloud engineering | Little or no experience, confirmed by user | Next | Cloud foundations, then one deployed environment with identity, networking, monitoring and cost records |
| Spark/lakehouse processing | Not evidenced | Next | SQL/PySpark comparison, partition/skew analysis and table evolution |
| Streaming and CDC | Not evidenced | Next | Keyed trade events, recovery from offsets, duplicate/late-event handling |
| Analytics engineering / semantic layer | Not evidenced | Next | Versioned SQL models, tests, lineage and one dashboard using agreed metrics |
| Software/API architecture | Database design documented; service interfaces not explicit | Next | Controlled query/retrieval API, contracts and load limits |
| Applied ML/statistics | Not evidenced | Later, before ML claims | Baseline model, time-based validation, imbalance and leakage analysis |
| RAG and AI evaluation | AI-assistant use documented; engineered AI systems absent | Later | Permission-aware retrieval and held-out answer-quality evaluation |
| Model lifecycle / AI operations | Not evidenced | Later | Versioned data/model/prompt/index, release gates and rollback |
| Reliability engineering | Troubleshooting documented; SLO/restore/drill evidence absent | Throughout | Measured service objectives, failure drills and recovery verification |
| Governance/security | Banking/regulatory project exposure; controls not detailed | Throughout | Lineage, classifications, access policies, retention and audit evidence |
| Architecture leadership | Design, reviews and collaboration documented; scope unclear | Throughout | Decision records, independent review, business case and migration plan |
| Measurable impact | Awards present; limited quantified delivery outcomes | Immediate | Recover honest metrics from authorized records and clearly state ownership |

## What “current data skills” means here

This is a targeted sample, not a complete labor-market survey. Job pages can close or change.

A Citi Pune senior engineering posting dated July 14, 2026 combines Python/PySpark, advanced SQL, ETL/ELT, automated delivery, data quality and AI integration. It gives a particularly relevant technical comparison for his location and existing financial-services experience. It does not establish an internal transfer opportunity or his eligibility. [Citi role](https://jobs.citi.com/job/pune/senior-developer-python-and-spark/287/97435532880)

An Amazon India data-engineering posting also combines programming, modelling, pipelines, cloud technologies and business ownership. Its emphasis on delivering usable data supports including communication, metrics and product thinking alongside tools. [Amazon role](https://www.amazon.jobs/en/jobs/10474887/data-engineer-in-data-engineering-analytics)

These examples support prioritizing modern engineering around his SQL strengths. They do not imply he needs every technology mentioned in every job description.

## Complementary skills with a clear purpose

1. **Analytics engineering:** Introduce dbt-style versioned transformations, data tests and a semantic layer. This is a direct extension of his SQL skills. Build one dashboard to verify the usefulness of his data, without making dashboard specialization the main career goal. [dbt documentation](https://docs.getdbt.com/)
2. **Event-driven processing:** Use one Kafka exercise to learn partition keys, ordering, consumer recovery and replay. Apply it to trade amendments and cancellations. Explain exactly where guarantees hold, rather than promising universal “exactly once.” [Kafka introduction](https://kafka.apache.org/intro/)
3. **Statistical judgment:** Study distributions, sampling, confidence intervals, hypothesis testing, precision/recall, class imbalance and temporal validation. These support evaluating both surveillance experiments and AI quality.
4. **ML lifecycle literacy:** Train one simple baseline for synthetic operational anomalies. Track data, parameters, metrics and artifacts; compare against a rule-based baseline. The purpose is understanding reproducibility and deployment, not claiming a validated banking-risk model. [MLflow tracking](https://www.mlflow.org/docs/latest/ml/tracking)
5. **Governance and auditability:** Extend banking experience into data contracts, lineage, ownership, controlled access, evidence retention and reproducible outputs. Implement controls in the capstone instead of collecting terminology.
6. **Data product design:** Define consumers, service expectations, business metrics, support ownership and adoption measures. Present findings to a nontechnical reviewer.
7. **Cloud economics:** Estimate and measure storage, compute, data transfer and model-inference costs. Compare alternatives at equal correctness and service requirements.
8. **Migration leadership:** Practice replacing a PL/SQL-style batch with a modern pipeline through shadow runs, reconciliation, staged cutover and rollback. His existing expertise makes this an especially useful bridge project.

Graph databases/entity resolution, deeper distributed storage internals, Kubernetes, native Python extensions and specialized deep learning remain optional branches. Add them when a target role or measured project limitation requires them. This avoids spending the core study budget on a long list of disconnected tools.

## First 90 days: concrete work

Confirmed availability: 15–20 hours per week. Thirteen weeks provide about 195–260 hours before breaks. Use the additional time for deliberate Python practice, independent exercises and testing rather than skipping foundations. Python practice is embedded in the project rather than added on top.

| Week | Work | Evidence to save |
|---|---|---|
| 1 | Baseline Python/SQL/Git/Linux assessment; select synthetic trades, accounts and instruments | Skills inventory and a one-page project charter |
| 2 | Python types, collections, functions, Decimal and timezone-aware timestamps | Small, tested financial-data transformations |
| 3 | Modules, files, API pagination, exceptions and context managers | Runnable ingestion command and failure examples |
| 4 | Database transactions, parameterized SQL and batched writes | Idempotent loader with rollback test |
| 5 | Iterators, generators and bounded-memory processing | Memory measurements for increasing input sizes |
| 6 | Typing, dataclasses, interfaces and configuration | A second source adapter and documented contracts |
| 7 | Unit/integration tests, logging and debugging | Regression checks for duplicates, bad input and interruptions |
| 8 | Git review workflow, packaging and automated checks | Clean installation and automated test run |
| 9 | Trade facts, account/instrument dimensions and historical changes | Model diagram and business definitions |
| 10 | Incremental updates, cancellations and late arrivals | Reconciliation and replay reports |
| 11 | Scheduler dependencies, retries and backfill behavior | Scheduled workflow and recovery demonstration |
| 12 | Versioned SQL models, data tests and a simple dashboard | Tested metrics and freshness report |
| 13 | Independent review and unfamiliar change request | Recorded demonstration, feedback and next-quarter backlog |

**Day-90 outcome:** A defensible Python and SQL data pipeline with useful operational controls. This is an early engineering milestone, not evidence of Python mastery or readiness for every senior data role.

If Python fundamentals require more time, move dashboard work into month 4. If he passes the baseline convincingly, replace beginner exercises with realistic failure, design and performance problems.

## Baseline assessment before assigning proficiency scores

Give him unfamiliar tasks using synthetic data and ordinary documentation access:

- SQL: explain and improve a slow reconciliation query while preserving results.
- Python: implement a paginated loader, safely restart it and explain its resource handling.
- Engineering: review a small code change, write a regression test and run it automatically.
- Data design: handle a corrected trade, a cancelled trade and an instrument attribute change.
- Architecture: draw a service boundary and explain identity, failure recovery and cost assumptions.
- AI: distinguish using an assistant from building a system; design an evaluation for cited answers.

Record guided/independent/operational evidence using the roadmap rubric. Do not mark undocumented skills as zero before assessment.

## Career checkpoints

- **Months 4–6:** Seek a bounded Python/pipeline modernization assignment or suitable hybrid SQL/Python opportunities if the practical gates pass. Existing banking expertise makes this more relevant than a generic beginner project.
- **Months 6–9:** Review readiness for hybrid SQL/Python or data-engineering opportunities, using the completed pipeline, cloud and Spark evidence. Begin conversations before the entire roadmap ends.
- **Months 9–15:** Add AI retrieval and reliability evidence; assess fit for senior roles against actual ownership and design expectations.
- **Months 18–24:** Present architecture and Python capstones. Architect/principal progression should depend on cross-team scope and operational judgment, not the completion date alone.

An internal project can provide a bridge if available, but access and manager support have not been established. No applications, outreach or employer communications are part of this assessment.

## Resume evidence to improve now

The main presentation gap is that many bullets describe responsibilities without showing scale, decisions or results. Capture verified numbers where available: rows or events processed, batch duration, query latency, failure rate, recovery time, release frequency and engineers mentored. Do not invent numbers or disclose confidential details.

Use a structure such as: “Improved [specific workflow] by changing [technical approach], moving [verified metric] from [before] to [after], while preserving [reconciliation/control requirement].” This is a template, not a claim to add unchanged.

Specify the actual version-control and scheduling tools if known. Clarify the scope behind “database design,” “well-tested code” and “large-volume ETL.” Distinguish AI-assisted productivity from independently built AI solutions. Keep future study projects separate from paid experience.

The rendered resume places a role heading at the bottom of page 1 and its bullets on page 2; keep them together in a future edit. The profile URL also appears as `h?ps://` in the supplied document and should be verified and corrected. The original resume has not been changed.

## How to use the project files

1. Read this assessment to understand priorities and the evidence still needed.
2. Follow `AI-Data-Architecture-Roadmap.md` for the personalized 24-month curriculum, Python track, project gates and resources.
3. Update `AI-Data-Project-Tracker.md` weekly with actual evidence and reviewer feedback.
4. Use `Sujeet-Market-and-Job-Strategy.md` for target-role selection, interview gates and current market evidence.

The plan is a route toward deep capability. It cannot guarantee a title, salary or mastery; repeated independent delivery and production responsibility are the evidence that closes the remaining gap.
