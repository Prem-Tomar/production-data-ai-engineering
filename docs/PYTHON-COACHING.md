# Python: foundations to expert practice

Python is a primary learning track from the first session through the final practical defense. These notes start from SQL/PLSQL experience and no prior Python knowledge. Read a short explanation, run its example and apply the concept in a concrete task.

**First 30 days target:** working knowledge and at least intermediate capability in the Python needed for this project, demonstrated by a useful local ETL command and an independent variation/debugging assessment. Use roughly 60–85 hours within the existing 15–20 hours/week. This is the learning target, not a proficiency award based on elapsed time. Advanced Python continues while building the rest of the platform.

## How to use these notes

Each session follows **brief example → run → change → fix → apply**. Spend roughly 5–10 minutes on the explanation and most of the session writing or debugging code. No written theory answers are required.

Read the relevant explanation, run the example, and then make the change requested in the issue. The examples introduce the concept without completing the full project task. Use the hint or reference when a result is unexpected. Keep review questions separate from task completion so study can continue independently.

Day 1 starts with the small calculation below. Run it in the interpreter, change a value and run it again. A project script, database, tests and written report are not needed for that first task. Days 2–10 each have their own explanation and example below.

Completion is demonstrated by the issue's runnable results and its specified changed-input or debugging case. Every task includes its own inputs, setup and necessary starter code. No task depends on earlier work or another person choosing an example. Day numbers indicate recommended study order, not a deadline to rush. The 30-day foundation can take longer within the 15–20 hour weekly budget. Advanced Python mastery is the longer track, not a 30-day claim.

## First session: what Python does

A Python program is a sequence of instructions. The interpreter is the program that executes them. A value is data, such as the number `3` or the text `"USD"`. A name lets the program refer to a value. An expression computes a result from values.

Open a terminal and enter `python` to start the interpreter. Its `>>>` prompt accepts Python instructions; do not type the prompt itself. Enter this example, then change it:

```python
quantity = 3
price = 10
total = quantity * price
print(total)
```

The first line makes the name `quantity` refer to the integer value `3`. The second does the same for `price` and `10`. The third calculates a product and makes `total` refer to the result. Assignment uses `=`; it is not an equality test. In this example, `total` is a computed value, not a spreadsheet formula that will recalculate whenever another name changes.

`print(total)` displays the value referred to by `total`. The parentheses contain the value passed to the print function. `*` is the multiplication operator.

The output is `30`. Change quantity to 5, rerun the multiplication and print the result: it becomes `50`. Then try quantity 2 and price 7. If the result stays unchanged, rerun the statement that calculates total before printing it. There is no written explanation to submit.

Finish when those calculations run correctly. This arithmetic will also be useful in trade transformation. No script or report is needed for this task.

## Days 1–10: explanation index

Read one section, run its example, then complete the matching GitHub task. Each task supplies what it needs and can be completed independently. The examples are starting points; the issue's inputs and acceptance criteria define the work to finish.

| Task | Explanation |
|---|---|
| [Day 01](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/1) | [Values, names and calculation](#first-session-what-python-does) |
| [Day 02](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/2) | [Numbers and text](#day-02-numbers-and-text) |
| [Day 03](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/3) | [Running a script](#day-03-running-a-script) |
| [Day 04](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/4) | [Converting source values](#day-04-converting-source-values) |
| [Day 05](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/5) | [Cleaning strings](#day-05-cleaning-strings) |
| [Day 06](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/6) | [Choosing a branch](#day-06-choosing-a-branch) |
| [Day 07](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/7) | [Lists and positions](#day-07-lists-and-positions) |
| [Day 08](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/8) | [Loops](#day-08-loops) |
| [Day 09](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/9) | [Dictionary records](#day-09-dictionary-records) |
| [Day 10](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/10) | [Sets and repeated values](#day-10-sets-and-repeated-values) |

## Day 02: numbers and text

`6` is a number, while `"6"` is text, called a string. Quotation marks tell Python to treat the characters as text. The same operator can behave differently depending on the values: `+` adds numbers but joins strings.

```python
print(6 + 2)
print("6" + "2")
```

The outputs are `8` and `62`. Python does not guess whether text containing digits should be a number. Conversion makes that choice explicit: `int("6")` produces the whole number 6. Use `type(6)` and `type("6")` to inspect their types. For this project, converting source text is a separate step before arithmetic; printing digits is not evidence that they have a numeric type.

## Day 03: running a script

The interpreter lets you try instructions one at a time. A script saves those instructions in a `.py` file so the same program can be run again. For example, a file containing the following statement prints one message when executed:

```python
print("Trade tool ready")
```

Work from the repository root. Create a virtual environment once; it provides a separate Python environment for this project. Then run the task's script using that interpreter:

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe src/trade_ingestion/main.py
```

Create `src/trade_ingestion/main.py` as part of the task before running the second command. A virtual environment does not create your application file. You do not need to activate it when invoking its interpreter directly. Keep `.venv` out of Git. If `python` is not found, install Python or use the available Python launcher; check which interpreter the command starts.

## Day 04: converting source values

External values often arrive as strings. `int()` interprets a whole-number string and returns a number suitable for arithmetic. Conversion is different from validating a business rule: converting `"0"` succeeds, even if zero is later rejected as a trade quantity.

```python
raw_count = "8"
count = int(raw_count)
print(count + 1)
```

The output is `9`; `raw_count` is still text. Conversion returned another value instead of changing the original string. Try `int("eight")` separately: it raises `ValueError` because the text is not a valid integer. Correct the input and rerun. Error handling comes in a later task; do not hide the failure yet.

## Day 05: cleaning strings

A string method performs an operation on text. `strip()` removes surrounding whitespace, while `upper()` returns uppercase text. These operations return new strings; the original value is unchanged unless you assign a result back to its name.

```python
raw_code = " eur "
clean_code = raw_code.strip().upper()
print(clean_code)
print(repr(raw_code))
```

The outputs are `EUR` and `' eur '`. `repr()` makes the surrounding spaces visible. This is normalization: different presentations can become one consistent label. It is not validation—`"xyz"` becomes `"XYZ"` even if your application does not support that currency. Add only the normalization requested in Day 5; supported-currency rules come later.

## Day 06: choosing a branch

A comparison such as `amount > 0` produces `True` or `False`. An `if` statement runs its indented block only when the condition is true. `else` handles the other case. Use consistent indentation; it is part of Python's structure.

```python
amount = 0
if amount > 0:
    print("positive")
else:
    print("not positive")
```

This prints `not positive`. Change amount to 4 and it prints `positive`. Change it to -1 and the other branch runs again. The operator `>` excludes zero; `>=` includes it. The project task needs the former rule. Keep the actual calculation inside the accepted path so rejected input does not also produce a calculated amount.

## Day 07: lists and positions

A list holds several values in order. Its first position has index 0, the next index 1, and so on. `append()` adds an item at the end. A list can change in place; it is mutable.

```python
prices = [10, 20]
print(prices[0])
prices.append(30)
print(prices)
```

The outputs are `10` and `[10, 20, 30]`. Indexing selects a position, not an item with a matching value. Accessing a position beyond the list raises `IndexError`. Appending changes the existing list; avoid assigning the return value of `append()` back to the list name. The task applies these ideas to trade IDs and adds an item-replacement operation.

## Day 08: loops

A `for` loop visits the items in a collection. On each iteration, its loop name refers to the next item. The indented body runs once per item; an empty collection runs it zero times.

```python
currencies = ["INR", "EUR"]
for currency in currencies:
    print(currency)
```

This prints `INR` and `EUR` on separate lines. Add another item to the list without adding another print statement. Then try an empty list. To count processed items in your task, initialize the count before the loop and update it inside the body. Initializing it inside the body would reset it on every iteration. Print the final count after the loop so the empty-input case also has a result.

## Day 09: dictionary records

A dictionary stores values under keys. Keys make a record easier to read than relying on positions: `record["currency"]` asks for a named field. Values can have different types, so preserve the source's text values until the conversion step.

```python
account = {"account_id": "A7", "currency": "EUR"}
print(account["currency"])
account["currency"] = "INR"
print(account["currency"])
```

The outputs are `EUR` then `INR`. Assigning to an existing key replaces that field. Reading an absent key using brackets raises `KeyError`; it does not produce zero. Apply this structure to the task's trade fields. The dictionary records data but does not automatically check required fields or calculate anything.

## Day 10: sets and repeated values

A set keeps distinct values and supports membership checks with `in`. It is useful for checking whether an identifier has already appeared. Keep the original input list when processing order matters.

```python
seen = {"A1"}
print("A1" in seen)
seen.add("A2")
seen.add("A2")
print(len(seen))
```

The outputs are `True` and `2`; adding A2 twice does not create two copies. A set does not provide an input-order guarantee. Also, converting an entire list to a set removes duplicates but does not tell you which arrival was repeated. For the task, check membership while visiting the original input sequence and keep separate counts for first occurrences and repeats.

## First 30 sessions

The live GitHub issues #1–#30 follow this concept sequence. Each issue is a plain, self-contained task with exact inputs and results. The original ingestion assignments remain in [PIPELINE-BACKLOG.md](PIPELINE-BACKLOG.md), with P identifiers, for the next project stage.

Read all [versioned task descriptions](PYTHON-DAILY-TASKS.md), including the starter code for later debugging and extension tasks.

| Day | Main concept | Programming task |
|---|---|---|
| 01 | Interpreter, values, names and expressions | Calculate 3 × 10, 5 × 10 and 2 × 7 to obtain 30, 50 and 14 |
| 02 | Interactive execution | Add numbers/text, convert a quantity and correct a bad conversion |
| 03 | Script execution and project environment | Run a tiny greeting script in a virtual environment |
| 04 | Types and explicit conversion | Convert a quantity from text and observe invalid conversion |
| 05 | Strings | Normalize currency text while preserving the original string |
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
| 20 | JSON records | Decode trade lines and report malformed JSON or missing fields |
| 21 | Generators | Yield records incrementally instead of retaining the file |
| 22 | Dataclasses and their field contracts | Model a validated trade while preserving runtime checks |
| 23 | Closures and late binding | Repair two callbacks so quantity 7 fails limit 5 and passes limit 10 |
| 24 | Automated tests | Protect a calculation and rejection behavior |
| 25 | Parameterized tests | Cover multiple meaningful boundary cases |
| 26 | Composing functions | Connect reading, validation and calculation in a local transformation |
| 27 | Command-line arguments | Select the input path without changing code |
| 28 | Logging | Show useful progress and errors without full payloads |
| 29 | Small local ETL increment | Save valid transformed records to a separate output file |
| 30 | Independent foundation check | Add a currency allow-list to a supplied ETL starter and reproduce/fix its acceptance bug |

## What the project gains in the first month

The tasks create code under `src/trade_ingestion/`, synthetic fixtures under `labs/01-reliable-ingestion/fixtures/` and focused tests under `tests/`. Day 3 uses `main.py`; other script tasks use distinct day-specific locations so they can run independently. Each issue includes its own fixture data, setup and any required starter code. They share trade-processing concepts and produce candidate components for the later platform; no earlier implementation is required to start a task.

The month-one deliverables include a standalone file-to-file ETL command, focused functions/modules, a typed data model, logging practice and meaningful tests. Day 29 builds the local ETL command with incremental JSONL reading, validation, Decimal calculations, explicit timezones, failure reporting and separate file output. Day 30 supplies its own smaller ETL starter for a currency-rule regression exercise. Integrating and reviewing these components belongs to the next project stage; the independent exercises do not establish that one combined application already contains every feature.

Intermediate readiness means the learner can independently use and explain collections, function contracts and scope, ordinary objects/dataclasses, exceptions, imports, iterators/generators, context managers, file/JSON handling, basic testing and debugging in this program. Include an unfamiliar name-binding or closure defect in the assessment. Review [binding and scope](PYTHON-BINDING-AND-SCOPE.md) on Days 12, 13 and 23; do not delay these requested nuances until the final year.

After the check, continue through [the preserved pipeline backlog](PIPELINE-BACKLOG.md), reusing completed work. PostgreSQL, transactional replay, HTTP integration, CI and cloud deployment remain required later increments. An unresolved foundation topic receives targeted coaching while unrelated safe work can continue.

## Continuing Python tasks

New tasks extend the queue as reviewed issues close. Their day numbers indicate study order, not prerequisites; each task includes its own setup and inputs. Adding a task here does not mean the first-month foundation gate has been passed.

| Day | Explanation | Task |
|---|---|---|
| 31 | [Equality and identity](#day-31-equality-and-identity) | [Issue #38](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/38) / [task text](PYTHON-DAILY-TASKS.md#day-31-compare-trade-records-by-value) |
| 32 | [Copying nested records](#day-32-copying-nested-records) | [Task text](PYTHON-DAILY-TASKS.md#day-32-copy-nested-trade-data-safely) |

## Day 31: equality and identity

Equality asks whether values compare equal. Identity asks whether two names refer to the very same object. For dictionaries containing these simple field values, `==` compares keys and their values, while `is` checks identity. Equal contents do not require the same object or the same key insertion order.

```python
first = {"trade_id": "T9", "quantity": 3}
same_values = {"quantity": 3, "trade_id": "T9"}
alias = first

print(first == same_values)
print(first is same_values)
print(first is alias)

same_values["quantity"] = 4
print(first == same_values)
print(first["quantity"])
```

The output is `True`, `False`, `True`, `False`, `3`, on separate lines. The two dictionary expressions created separate objects. Assigning `alias = first` instead created another name for the original object; it did not copy that dictionary. Changing the separate `same_values` dictionary leaves `first` unchanged. Changing a field through `alias` would affect `first` because both names refer to one dictionary.

A repeated trade read from a file can arrive as a new dictionary with unchanged contents. Testing identity alone would incorrectly treat it as different data. For this exercise, compare the supplied trade IDs and field values to distinguish a new trade, an unchanged replay and a conflicting version. Inspect equality and identity separately when the starter gives an unexpected classification.

Keep the scope to the supplied fields and types. Dictionary equality is not financial-data validation: it does not normalize currency labels, convert text quantities or decide which fields define a real business duplicate. Those policies must be specified before using this idea in the production replay pipeline. Avoid using string or small-integer identity experiments to infer value equality; implementation reuse can make those observations misleading.

## Day 32: copying nested records

Assigning another name to a dictionary does not copy it. Calling its `copy()` method creates a new outer dictionary, but this is a shallow copy: values inside it still refer to the same objects. If a value is a mutable list or dictionary, changing that nested object can affect both records.

```python
source = {"account_id": "A7", "labels": ["new"]}
shallow = source.copy()

print(source is shallow)
print(source["labels"] is shallow["labels"])
shallow["labels"].append("checked")
print(source["labels"])
```

The output is `False`, `True`, then `['new', 'checked']`. The outer dictionaries are different, but both contain a reference to the same list. `append()` mutates that shared list. Assigning a completely new list to `shallow["labels"]` would instead replace one dictionary entry; that would not replace the entry in `source`.

For a prepared trade that must leave its source intact, identify every nested mutable object the transformation can change. Copying those objects explicitly or using a deep copy can provide independent data for this task's dictionaries, lists and strings. A deep copy recursively copies nested data; it is not the same operation as copying only the outer dictionary. The searchable hint in the task points to the standard-library tool.

Check isolation by changing one returned record and inspecting both the source and another result. Checking only that the outer dictionaries have different identities misses this bug. Avoid copying more than the use case needs in large pipelines: copying also takes time and memory. This exercise uses small in-memory records and does not establish transaction or database isolation.

## Master-level Python syllabus and gates

The target is expert applied Python engineering: independently design, maintain, debug, optimize and teach substantial software. The periods below align with the existing 24-month roadmap and may move when prerequisites need more time. Passing a gate needs demonstrated work; no proficiency score is assigned in advance.

| Stage | Concepts taught progressively | Project application | Gate |
|---|---|---|---|
| Foundations, first 30 sessions and months 1–2 | Execution, names/types, operators, strings/Unicode, conditions, collections, loops, functions/scope, imports, exceptions, files, Decimal, timestamps, basic tests | Self-contained exercises and local ETL command, then database ingestion | Explain and independently modify/debug a new input variation |
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

Use the [official Python tutorial](https://docs.python.org/3/tutorial/) as supporting reading, the [data model reference](https://docs.python.org/3/reference/datamodel.html) for advanced object behavior, and the [free-threading guide](https://docs.python.org/3/howto/free-threading-python.html) when the concurrency phase needs build-specific details. Start with the explanations here and use reference material for more detail. These sources support Python behavior; the study sequence and assessment gates are this project's plan.
