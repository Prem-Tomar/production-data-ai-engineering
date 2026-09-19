# Technology depth and practical nuances

The track must teach how each selected technology behaves, where its guarantees end, and how to diagnose failures. Completing a happy-path tutorial is the starting point. Apply this requirement progressively within the existing roadmap and weekly budget.

## How depth enters a learning issue

Keep the five-part issue format: Goal, Context, Task, Acceptance Criteria and Hint. Introduce one relevant nuance in Context, define unfamiliar terms, and make its effect observable in the implementation. Give a concept to search for, not a complete solution. Add a deeper variation as a later issue when its prerequisites exist.

For example, the Decimal issue can ask the learner to compare constructing a value from decimal text with constructing it from a floating-point number. Transaction work can later distinguish a successful SQL statement from a committed transaction. Neither example requires adding an architecture report to a beginner task.

Use this progression for each technology:

1. Build a small useful behavior and understand its normal execution.
2. Observe an edge case or failure that exposes an important limitation.
3. Change the implementation and verify the result without breaking earlier behavior.
4. At the relevant milestone, explain a trade-off, measure it where appropriate, and solve an unfamiliar variation.

Automated tests and documentation belong in the issues dedicated to them and in release reviews. Early issues can demonstrate behavior by running the program. Milestone evidence records deeper coverage without turning every daily issue into several assignments.

## Coverage by technology

These are investigation topics and required experiments, not claims that a particular release guarantees a behavior. Check the official documentation for the exact version used before implementing version-sensitive features.

| Technology / selection | Nuances to investigate | Practical experiment in this project | When |
|---|---|---|---|
| Python — core | Aliasing and mutability; identity versus equality; exceptions and cleanup; lazy iteration; decimal contexts and rounding; timezone conversion; type hints versus runtime validation | Expose a shared-mutable-state defect, reject non-finite money values, and process a larger input without retaining every row | Foundations, then deeper Python gates |
| Python concurrency — core later | Blocking calls inside async code; cancellation; bounded queues; thread/process trade-offs; interpreter build and dependency compatibility | Compare sequential and concurrent source reading; cancel active work and check resource cleanup and memory | Months 9–14 and 19–24 |
| Python packaging — core | Working directory versus import paths; editable versus built installation; dependency compatibility; import side effects | Install a built distribution in a fresh environment and invoke it from outside the repository | Foundations, then library gates |
| pytest / automated testing — selected for the daily track | Test isolation; fixtures and cleanup; where to patch; mocks versus real integrations; deterministic failure timing | Make a regression test fail on an injected calculation defect and reproduce a restart failure against a disposable database | Foundations onward |
| SQL and PostgreSQL — core | NULL and three-valued logic; numeric precision; timestamp display versus stored meaning; isolation and snapshots; locks and deadlocks; query plans and index selectivity; connection limits | Reconcile NULL-containing data, run two conflicting sessions, inspect a query plan, and demonstrate rollback plus clean-environment restore | Foundations through reliability |
| Psycopg — selected PostgreSQL driver | Parameter binding versus SQL construction; transaction ownership; connection lifecycle; failed transactions and savepoints; pooling later | Fail one statement in a batch, recover using the declared transaction boundary, and verify both database state and connection cleanup | Foundations through pipeline gate |
| Oracle/PLSQL — existing expertise and reference | NULL/empty-string behavior; date and number conversions; implicit commits; procedural versus set-based work; vendor-specific SQL semantics | Compare a synthetic reference batch with PostgreSQL/Python results, explaining differences instead of translating syntax blindly | Baseline and migration work |
| HTTP/JSON and chosen client — core | JSON types versus business types; response status versus valid content; connection/read/overall deadlines; retry safety; pagination consistency and repeated cursors | Exercise malformed pages, a repeated cursor and a slow source; stop within a bound without skipping accepted work | Foundations, then adapter gate |
| Git and GitHub — core | Working tree/index/commit; merge conflicts; revert versus history rewriting; review and protected-branch workflow | Make a focused change, resolve a conflict, and undo a bad change through the approved review path | Foundations onward |
| GitHub Actions — selected CI | Job isolation; service readiness; cache versus artifact; permissions and secrets; untrusted pull-request input | Run tests against a disposable database and carry the same built artifact into a later deployment workflow | Foundations, then deployment gate |
| Linux and shell — core operational skills | Exit statuses; signals; permissions; quoting; environment inheritance; process and filesystem ownership | Stop a running worker gracefully, distinguish failed commands from successful output, and run with restricted filesystem access | Foundations through deployment |
| Docker — planned | Image versus container; build context; layers and cache; persistent volumes; startup order versus readiness; signals and non-root execution | Recreate the application container while preserving intended data; stop it during ingestion and observe recovery | Foundations after the local command works |
| dbt-style transformations; dbt if selected | Model grain; joins that multiply rows; incremental predicates; unique keys; late corrections; full refresh; data-test limits | Compare incremental output against a full reference rebuild after a late trade amendment | Months 3–5 |
| Orchestration; Airflow is a candidate | Scheduled interval versus execution time; retries and side effects; catch-up/backfill; dependency failures; overlapping runs | Rerun a failed interval and backfill a period without double counting or racing the current run | Months 3–5 |
| AWS — default cloud | Identity versus resource policies; network boundaries; credential lifecycle; encryption/key access; service quotas; regional dependencies; storage and transfer costs | Deploy with a restricted service identity, remove one permission, diagnose the failure, and measure teardown completeness and cost | Months 6–8 onward |
| Infrastructure as code — tool to select | Desired state versus actual state; drift; state-file sensitivity; locking; replacement versus in-place update; failed applies | Recreate an environment, detect a manual change, and review a plan that would replace a stateful resource | Months 6–8 |
| PySpark — planned | Lazy execution; driver versus executor memory; shuffle and skew; join strategy; partitioning; serialization and Python UDF boundaries | Inspect an execution plan, create a skewed workload, compare a built-in transformation with a Python UDF and preserve correctness | Months 6–8 |
| Databricks / Delta Lake — default platform | Runtime compatibility; transaction conflicts; schema enforcement versus evolution; MERGE ambiguity; small files; retention and recovery limits; access boundaries | Apply duplicate source keys, evolve a schema deliberately, and test restore behavior under the selected retention settings | Months 6–8 onward |
| Kafka — bounded planned exercise | Ordering within a partition; keys and repartitioning; offsets versus completed side effects; rebalances; delivery guarantees across external systems; event time | Interrupt a consumer around a database write and offset commit; reconcile duplicates and explain exactly where guarantees hold | Month 8 or later |
| PostgreSQL / pgvector — initial retrieval choice | Exact versus approximate retrieval; index/operator compatibility; filtering and recall; embedding dimensions and model changes; deletion freshness | Compare exact search with indexed retrieval on the same permission-filtered questions and check deleted-document behavior | Months 9–11 |
| LLM API, embeddings and RAG — provider/model to select | Tokenization and context limits; chunk boundaries; retrieval failure versus generation failure; nondeterminism; rate limits; prompt injection; tool authorization; version changes | Test missing/conflicting sources and denied access, compare retrieval methods, and rerun held-out evaluation after a model or index change | Months 9–14 |
| NumPy/dataframes and classical ML — later | Dtypes and missing values; copies versus views; vectorization; temporal leakage; imbalance; calibration and threshold selection | Compare a rule baseline and a simple model on a time-separated synthetic dataset, preserving a held-out split | Python performance and month 15 |
| MLflow or equivalent — candidate | Tracking versus reproducibility; dataset/artifact lineage; dependency capture; experiment versus released model | Reproduce a saved run from its recorded inputs and dependencies, then detect a changed dataset | Month 15 |
| Observability stack — tools to select | Logs/metrics/traces; label cardinality; percentiles; sampling; missing data; alert thresholds and useful context | Diagnose one injected failure from telemetry, check alert delivery and expose a monitoring blind spot | Months 12–14 |
| Pandas / PyArrow / Parquet — added core foundations | Dtype conversion; missing values; decimal preservation; copy/memory behavior; columnar layout and schema compatibility | Round-trip a synthetic fixture through Parquet and compare exact values, schema and peak memory | Months 3–5, before Spark optimization |
| Python web framework — choose one; Flask for relevant target roles | Request validation versus authorization; blocking work; connection lifecycle; pagination and error contracts | Serve a restricted query endpoint, reject unauthorized input and exercise dependency timeouts | Applied AI/backend phase |
| Redis — role-specific cache branch | Expiry; invalidation; stale data; atomic operations; cache keys and permission isolation | Change source data and user permissions, then verify cached responses cannot leak or remain incorrectly valid | After the API and access model work |
| AWS catalogue/query/workflow services — core selection during cloud design | Schema catalogue versus source truth; partition discovery; data permissions; orchestration retries and service limits | Integrate the chosen S3/Glue/Athena access path and Lambda/Step Functions workflow; diagnose a denied or repeated operation | Months 6–8 |
| Snowflake — required for selected target roles | Warehouse sizing and contention; pruning; incremental loads; role grants; retention and cost | Port a reconciled model, compare query plans/cost and demonstrate access and replay behavior | Platform branch when targeting a matching role |
| Azure/Fabric — alternative platform branch | Workspace/capacity boundaries; sharing/shortcuts; semantic models; identity; deployment separation | Deploy one pipeline and inspect contention, permitted sharing and environment isolation | Replaces corresponding AWS-specific work if selected |
| NLP / pretrained-model libraries — role-specific | Tokenization; preprocessing changes; model/artifact versions; leakage and evaluation labels | Reproduce a small text classification/extraction baseline and inspect failure cases with tracked versions | After AI/data foundations |

The [employer requirement mapping](JOB-REQUIREMENTS-2026-09.md) also preserves role-specific gaps for enterprise schedulers, internal deployment/monitoring products, numerical libraries and alternate languages. When one becomes a target requirement, name its version, learning task and limitation here before claiming coverage. Conceptual equivalence is not product experience.

Azure may replace AWS if approved access justifies that choice; create the equivalent coverage row rather than requiring both clouds. Dashboard, infrastructure, HTTP-client, monitoring and model-provider choices must receive a named row with their specific edge cases once selected. Optional technologies such as Kubernetes, graph databases or agent frameworks are not mandatory until adopted for a measured need.

## Depth gate for adopting a technology

Before relying on a technology in a production release, attach the following to its milestone evidence:

- Its purpose in the system, selected version/configuration, and the official version-specific references consulted.
- One demonstrated edge case or failure, its explanation, and the implementation behavior that handles it.
- The limits of its guarantees, including behavior at the boundary with another component.
- A justified alternative or reason to avoid it for a smaller workload; measurements when the decision depends on performance or cost.
- An independently completed variation and any unresolved upgrade, compatibility or operational limits.

These items accumulate across issues; they are not a claim of exhaustive expertise. Record coverage as planned, demonstrated or reviewed. A listed topic is not completed work. Use the [milestone evidence template](../templates/milestone-evidence.md) and track unresolved coverage in the [project tracker](AI-Data-Project-Tracker.md).
