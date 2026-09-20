# Python coaching: foundations to expert practice

Python is a primary learning track from the first session through the final practical defense. The learner is experienced in SQL/PLSQL but new to Python. Start by teaching its mental model, then build guided exercises into independent engineering work. Do not begin by handing over a loader assignment.

**First 30 days target:** working knowledge and at least intermediate capability in the Python needed for this project, demonstrated by a useful local ETL command and an independent variation/debugging assessment. Use roughly 60–85 hours within the existing 15–20 hours/week. This is the learning target, not a proficiency award based on elapsed time. Advanced Python continues while building the rest of the platform.

## Coaching contract

Each session follows **brief demonstration → run → change → fix → apply**. Spend roughly 5–10 minutes introducing the concept and most of the session writing or debugging code. The learner does not submit written theory answers.

The coach checks prerequisites and demonstrates one small example before assigning a change. If the learner is stuck, offer a smaller example or hint, then let them run the variation. Discuss a misconception at the point where it affects the code. SQL/PLSQL comparisons are useful when they clarify the current task, not as extra material to memorize.

Day 1 starts with a coached demonstration, then the learner changes and runs a tiny calculation in the interpreter. The coach helps with opening the interpreter; prior coding, independent setup, a project script, tests and documentation are not prerequisites. Small demonstrations are allowed; giving away the full exercise solution is not.

Completion is demonstrated by the issue's runnable results and a changed-input or debugging case. A copied example alone does not pass. If the learner is confused, use another small coding variation before progressing. Day numbers indicate order, not a deadline to rush. The 30-day foundation can take longer within the 15–20 hour weekly budget. Advanced Python mastery is the longer track, not a 30-day claim.

## First session: what Python does

A Python program is a sequence of instructions. The interpreter is the program that executes them. A value is data, such as the number `3` or the text `"USD"`. A name lets the program refer to a value. An expression computes a result from values.

Watch the coach run this example, then change it yourself:

```python
quantity = 3
price = 10
total = quantity * price
```

The first line makes the name `quantity` refer to the integer value `3`. The second does the same for `price` and `10`. The third calculates a product and makes `total` refer to the result. Assignment uses `=`; it is not an equality test. In this example, `total` is a computed value, not a spreadsheet formula that will recalculate whenever another name changes.

Run the calculation with quantity 3 and price 10 and inspect the result, 30. Change quantity to 5, rerun the multiplication and inspect 50. Finally, try values chosen by the coach. If the result stays unchanged, inspect which statement needs to run again. There is no definitions quiz or written explanation to submit.

Finish when those calculations run correctly. This is the first working piece of the later trade transformation. Save it in the project script on Day 3; no standalone report is needed.

## First 30 sessions

The live GitHub issues #1–#30 follow this sequence. Coaching precedes the practice task in every issue. The original ingestion assignments remain in [PIPELINE-BACKLOG.md](PIPELINE-BACKLOG.md), with P identifiers; they are resumed after the foundation gate rather than discarded.

| Day | Main concept | Small practice after coaching |
|---|---|---|
| 01 | Interpreter, values, names and expressions | Run 3 × 10, change quantity to 5, rerun and obtain 50 after coaching |
| 02 | Interactive execution | Add numbers/text, convert a quantity and correct a bad conversion |
| 03 | Script execution and project environment | Run a tiny greeting script in a virtual environment |
| 04 | Types and explicit conversion | Convert a quantity from text and observe invalid conversion |
| 05 | Strings | Normalize and format a fictional trade identifier |
| 06 | Boolean decisions | Classify a positive, zero or negative quantity |
| 07 | Lists | Store and update a few fictional trade identifiers |
| 08 | Iteration | Process every item, including an empty list |
| 09 | Dictionaries | Represent and read one synthetic trade |
| 10 | Sets | Identify repeated identifiers without assuming output order |
| 11 | Functions and return values | Return a calculated value that another call can use |
| 12 | Name binding and local/global/nonlocal scope | Diagnose read-before-assignment and use explicit inputs instead of hidden state |
| 13 | Mutability and aliasing | Observe and correct an unintended shared-list change |
| 14 | Reading tracebacks | Locate and fix one deliberately broken calculation |
| 15 | Raising and handling exceptions | Reject an invalid quantity with a clear reason |
| 16 | Modules and imports | Reuse the calculation without executing work on import |
| 17 | Decimal arithmetic | Calculate a monetary amount from decimal text |
| 18 | Timezone-aware timestamps | Parse and compare explicit offsets |
| 19 | Files and resource cleanup | Read a small text fixture and close it safely |
| 20 | JSON records | Decode one synthetic trade line before processing it |
| 21 | Generators | Yield records incrementally instead of retaining the file |
| 22 | Dataclasses and their field contracts | Model a validated trade while preserving runtime checks |
| 23 | Closures and late binding | Repair two callbacks so quantity 7 fails limit 5 and passes limit 10 |
| 24 | Automated tests | Protect a calculation and rejection behavior |
| 25 | Parameterized tests | Cover multiple meaningful boundary cases |
| 26 | Composing functions | Connect reading, validation and calculation in a local transformation |
| 27 | Command-line arguments | Select the input path without changing code |
| 28 | Logging | Show useful progress and errors without full payloads |
| 29 | Small local ETL increment | Save valid transformed records to a separate output file |
| 30 | Independent foundation check | Implement a fresh rule, repair a defect and keep the ETL command/tests working |

## What the project gains in the first month

The practice evolves into code under `src/trade_ingestion/`, synthetic fixtures under `labs/01-reliable-ingestion/fixtures/` and focused tests under `tests/`. Create those files as the relevant lesson begins. Use the same small program rather than 30 disconnected exercises.

The month-one tool reads JSONL incrementally, validates synthetic trades, uses Decimal and explicit timezones, applies transformations, reports meaningful failures and writes a separate JSONL result. It has reusable functions/modules, a small typed data model, configurable input/output, resource cleanup, logs and meaningful tests. It is an initial local ETL capability, not the later transactional PostgreSQL pipeline.

Intermediate readiness means the learner can independently use and explain collections, function contracts and scope, ordinary objects/dataclasses, exceptions, imports, iterators/generators, context managers, file/JSON handling, basic testing and debugging in this program. Include an unfamiliar name-binding or closure defect in the assessment. Review [binding and scope](PYTHON-BINDING-AND-SCOPE.md) on Days 12, 13 and 23; do not delay these requested nuances until the final year.

After the check, continue through [the preserved pipeline backlog](PIPELINE-BACKLOG.md), reusing completed work. PostgreSQL, transactional replay, HTTP integration, CI and cloud deployment remain required later increments. An unresolved foundation topic receives targeted coaching while unrelated safe work can continue.

## Master-level Python syllabus and gates

The target is expert applied Python engineering: independently design, maintain, debug, optimize and teach substantial software. The periods below align with the existing 24-month roadmap and may move when prerequisites need more time. Passing a gate needs demonstrated work; no proficiency score is assigned in advance.

| Stage | Concepts taught progressively | Project application | Gate |
|---|---|---|---|
| Foundations, first 30 sessions and months 1–2 | Execution, names/types, operators, strings/Unicode, conditions, collections, loops, functions/scope, imports, exceptions, files, Decimal, timestamps, basic tests | Coached exercises and local ETL command, then database ingestion | Explain and independently modify/debug a new input variation |
| Core language depth, months 2–5 | Identity/equality, hashing, copying, mutability, default arguments, unpacking, closures, decorators, iterator protocol, generators, context managers and exception chaining | Safe adapters, bounded iteration and cleanup | Diagnose aliasing/default-argument defects and extend a source without breaking callers |
| Design and typing, months 3–8 | Classes, dataclasses, composition, inheritance/MRO, protocols, generics, structural typing, public/private API choices and dependency boundaries | Typed ingestion library with interchangeable sources | Defend interface choices; distinguish static checks from runtime validation; complete an unseen adapter |
| Data and integrations, months 3–8 | SQL parameterization, transaction/connection lifecycle, serialization, schema evolution, HTTP pagination/deadlines, dataframe dtypes, vectorization and columnar files | Reliable ETL/ELT and API/database integrations | Reconcile incremental/full results and recover from failure without leaking resources |
| Concurrency, months 9–11 | Async tasks, cancellation, structured lifetimes, semaphores/queues, threads/processes, races, synchronization, backpressure and interpreter-build distinctions | Bounded ingestion/retrieval workers | Compare suitable sequential/thread/async/process workloads; explain measurements and cancellation behavior |
| Testing and diagnosis, throughout; deeper months 12–14 | Unit/integration/contract/property-based tests, fixtures, patch boundaries, deterministic fault injection, tracing, profiling and debugging unfamiliar code | Reproduce retry, concurrency and memory defects | Fix an injected fault, add a meaningful regression check and explain remaining coverage gaps |
| Runtime and performance, months 12–20 | Complexity, allocation/lifetimes, reference counting and cyclic GC as implementation topics, imports, descriptors, attribute lookup, data model and bytecode inspection | Diagnose retained objects and measured bottlenecks | Reproduce memory/CPU behavior, improve a bottleneck at equal correctness and distinguish language guarantees from implementation details |
| Packaging and maintenance, basic early; depth months 15–22 | Build artifacts, dependency constraints, compatibility, semantic API changes, plugin boundaries, release/version strategy and clean installation | Reusable library with two consumers | Install the built distribution cleanly; migrate a consumer across an API change; obtain independent review |
| Expert defense, months 22–24 | Unfamiliar code, design simplification, upgrade regressions, teaching, review and operational judgment | Maintained platform and independent extension | Reviewer selects a connector, failure and workload variation; learner implements, diagnoses, measures and teaches without a tutorial |

Teach descriptors and metaclasses to the depth needed to reason about framework behavior. Native extensions and interpreter implementation are optional specializations after profiling reveals a real need. They must not delay practical fluency or become trivia-based definitions of mastery.

For each stage, retain at least one observed nuance, a failed approach, an independent variation and its review outcome at the milestone level. Record actual interpreter/dependency versions. Do not generalize a concurrency measurement across builds or workloads.

## Interview connection

Pair learning with unfamiliar coding variations from the start. Discuss reasoning briefly while inspecting real code; do not make daily completion depend on reciting definitions. Later use the [interview track](ETL-AND-INTERVIEW-TRACK.md) for timed tasks and independent mocks, including the verbal design skills needed in interviews. Remembering syntax or rehearsing one loader is not enough.

## Authoritative study references

Use the [official Python tutorial](https://docs.python.org/3/tutorial/) as supporting reading, the [data model reference](https://docs.python.org/3/reference/datamodel.html) for advanced object behavior, and the [free-threading guide](https://docs.python.org/3/howto/free-threading-python.html) when the concurrency phase needs build-specific details. The coach introduces prerequisites before directing the learner into reference material. These sources support Python behavior; the teaching sequence and assessment gates are this project's plan.
