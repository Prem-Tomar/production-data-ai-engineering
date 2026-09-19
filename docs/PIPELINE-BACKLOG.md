# Pipeline implementation backlog after Python coaching

The original 30 implementation assignments are preserved here as P01–P30. The live issues #1–#30 now form the coached Python foundation sequence requested by the user. References below use P identifiers, not the reassigned GitHub issue numbers.

These remain planned work. Reuse evidence from the coached foundation where it already satisfies an increment; do not repeat completed work. After the Python foundation gate, turn the next unsatisfied increment into a focused issue, then continue into the ETL, cloud, AI and production roadmap. No earlier implementation requirement has been marked complete or discarded.

## P01 — Run the first Python program locally

### Goal

Build a runnable Python entry point so the financial-data project has a working starting point.

### Context

The repository currently contains learning plans, but no application code. An entry point is the file you run to start a program. A virtual environment keeps this project's Python dependencies separate from other projects.

### Task

Create `src/trade_ingestion/main.py` and make it print a short startup message. Use a local Python virtual environment. Keep this focused on starting the program; database setup, packaging and cloud tools come later.

### Acceptance Criteria

- [ ] Running `python src/trade_ingestion/main.py` from the repository root prints the startup message and exits successfully.
- [ ] The program runs with the project's virtual environment active.
- [ ] Running the command again works without changing any files.

### Hint

Search for "Python venv Windows" and "run Python script from terminal". Pay attention to which Python interpreter runs the file.



## P02 — Display one synthetic trade using a dictionary

### Goal

Build a readable trade summary so the program can display the data it will eventually ingest.

### Context

Continue after P01. A dictionary holds named values, such as a trade identifier and its currency. Synthetic data is invented practice data. Start with a small subset of the future trade-event fields.

### Task

In `src/trade_ingestion/main.py`, represent one fictional trade with `trade_id`, `quantity`, `price` and `currency`, then display those values with clear labels. Keep quantity and price as decimal text for the next exercise. Focus on accessing dictionary values; calculations and file input come later.

### Acceptance Criteria

- [ ] The output includes all four trade fields with readable labels.
- [ ] Changing the trade's currency or identifier changes the displayed summary.
- [ ] The startup command from P01 still runs successfully.

### Hint

Search for "Python dictionary access values" and "Python formatted string literals". Look at the difference between a dictionary key and its value.



## P03 — Calculate trade notional with Decimal

### Goal

Calculate the trade's notional value so the summary includes quantity multiplied by price.

### Context

Continue after P02. Notional here means quantity multiplied by price in the trade's currency. Decimal represents decimal numbers explicitly; ordinary binary floating-point numbers can introduce surprising rounding in financial calculations.

### Task

Add the notional calculation to `src/trade_ingestion/main.py` using the trade's decimal text values and Python's `Decimal`. Display the result alongside its currency. Keep this to a single trade with valid positive values and at most two decimal places; currency conversion and aggregate totals come later.

### Acceptance Criteria

- [ ] Quantity `3` and price `0.10` produce a notional numerically equal to `0.30`, labelled with the trade's currency.
- [ ] Changing quantity or price changes the result correctly.
- [ ] Input decimal text is not first converted through a binary floating-point value.
- [ ] The existing trade summary and startup command still work.

### Hint

Search for "Python decimal financial arithmetic" and "Decimal from string versus float". Pay attention to how the initial number is constructed.



## P04 — Read synthetic trades from a JSONL file

### Goal

Read trades from a local file so changing input data does not require editing Python code.

### Context

Continue after P03. JSON is a text format for structured values. JSONL stores one JSON value on each line. A fixture is a small known input used while developing; use three fictional trades here.

### Task

Add `labs/01-reliable-ingestion/fixtures/trades.jsonl` and update `src/trade_ingestion/main.py` to read its three trades and display each summary and notional. Use the same four fields as P02, with quantity and price stored as JSON strings. Focus on file reading and iteration; assume well-formed input for this increment.

### Acceptance Criteria

- [ ] The command prints a summary and correct notional for each of the three input trades.
- [ ] Adding a fourth valid line produces a fourth summary without changing the code.
- [ ] An empty file produces no trade summaries and exits successfully.
- [ ] The file is closed after reading and the program still runs from the repository root.

### Hint

Search for "Python read JSON Lines file" and "Python with open context manager". Pay attention to processing one line at a time and releasing the file.



## P05 — Reject trades with invalid field values

### Goal

Validate decoded trades so incomplete or invalid data is not used in financial calculations.

### Context

Continue after P04. Validation checks whether data satisfies the program's rules. A decoded record is the Python value obtained from one JSON line. For this starter exercise, support only positive quantities and prices with up to two decimal places.

### Task

Add field validation in `src/trade_ingestion/validation.py` and use it before calculating each trade in `main.py`. Require a JSON object, nonblank text `trade_id`, currency from `INR`, `USD` or `EUR`, and decimal text quantity and price that are finite, positive and have at most two decimal places. On an invalid record, show its line number and reason, then stop with an unsuccessful exit status. Malformed JSON and file-access errors are handled in P07; full event versions and timestamps come later.

### Acceptance Criteria

- [ ] Valid input from P04 still produces the same summaries.
- [ ] A missing required field, non-object record or unsupported currency is rejected before that record's calculation.
- [ ] Zero, negative, nonnumeric, non-finite or overly precise quantity/price values are rejected.
- [ ] The first rejected record produces a readable line number and reason, stops subsequent processing, and returns a nonzero exit status.

### Hint

Search for "Python validate dictionary fields" and "Python Decimal finite number validation". Distinguish valid JSON syntax from valid business data.



## P06 — Choose the input file with a command-line option

### Goal

Make the input path configurable so the same program can process different trade files.

### Context

Continue after P05. A command-line option is a named value supplied when starting a program. Configuration changes how a program runs without editing its source code.

### Task

Update the command entry point in `src/trade_ingestion/main.py` to accept an optional `--input` path. Keep the existing fixture as the default. Focus only on selecting a local input file; configuration frameworks and database settings come later.

### Acceptance Criteria

- [ ] Running without `--input` processes the original fixture.
- [ ] Running with `--input` processes the selected file instead.
- [ ] A quoted file path containing spaces works.
- [ ] `--help` explains the input option and exits without processing trades.
- [ ] Validation and decimal calculations still behave as before.

### Hint

Search for "Python argparse optional file path argument". Pay attention to default values and paths supplied by the caller.



## P07 — Handle file and JSON errors at the command boundary

### Goal

Show useful failure messages so a learner can correct an input problem and rerun the program.

### Context

Continue after P06. An exception signals a failure during execution. The command boundary is where internal failures become messages and exit statuses for the person running the program. A nonzero exit status tells the caller that execution failed.

### Task

Handle expected file-opening and JSON-decoding failures in the input path used by `src/trade_ingestion/main.py`. Stop at the first error, report a useful cause, and close the file. Keep this focused on known input failures; retries, logging systems and suppressing unexpected programming errors are outside this issue.

### Acceptance Criteria

- [ ] A missing or unreadable input file produces a readable message and a nonzero exit status.
- [ ] Malformed JSON identifies the affected line and stops processing later lines.
- [ ] Expected input failures do not dump a Python traceback.
- [ ] Correcting the file and rerunning succeeds; the validation behavior from P05 still works.

### Hint

Search for "Python specific exception handling JSONDecodeError OSError" and "Python command line exit status". Catch errors where enough context exists to explain them.



## P08 — Separate trade processing from terminal output

### Goal

Make trade processing callable independently so the same behavior can later be used by another entry point.

### Context

Continue after P07. A service function performs a useful piece of application work independently of how someone starts it. The command entry point should handle arguments and output, while the service performs the trade calculation workflow.

### Task

Move the per-trade validation and notional workflow into `src/trade_ingestion/service.py`. Have it accept a decoded record and return the processed trade data; let `main.py` keep file selection, iteration, display and user-facing error messages. Reuse `validation.py`. Focus on this separation; classes, web APIs and dependency-injection frameworks are unnecessary.

### Acceptance Criteria

- [ ] The service can process a valid record and return its result without reading a file, parsing command-line arguments or printing.
- [ ] Invalid data is reported back to the caller without the service terminating the process.
- [ ] The command still displays the same results and handles the same input failures.
- [ ] Importing the service does not start the command or process the fixture.

### Hint

Search for "Python separate business logic from CLI" and "Python function return value versus print". Pay attention to the responsibilities of the caller and the called function.



## P09 — Store processed trades in memory

### Goal

Add a small storage boundary so processed trades can be saved and retrieved during a run.

### Context

Continue after P08. A storage boundary gives application code one place to save and retrieve data. An in-memory store holds values only while the program runs; it is a simple stand-in for a database. For these starter records, `trade_id` is unique.

### Task

Add an in-memory trade store under `src/trade_ingestion/storage.py` with save and retrieve behavior. Wire the command to save each successfully processed trade and report the number stored. Reject a repeated `trade_id` with a readable error rather than silently replacing it. Keep state local to each store instance. This is a temporary practice rule; event-history and replay semantics belong to later Lab 01 work.

### Acceptance Criteria

- [ ] Three valid trades with distinct identifiers can be saved and retrieved with their calculated values intact.
- [ ] The command reports three stored trades after processing that fixture.
- [ ] A repeated identifier is reported as an error without overwriting the first saved trade.
- [ ] A new store starts empty, and earlier validation and input-error behavior still work.

### Hint

Search for "Python in memory repository pattern" and "Python dictionary key uniqueness". Compare what the caller needs with how the values are stored; keep the interface small.



## P10 — Save processed trades in local PostgreSQL

### Goal

Add database persistence so a saved trade can be retrieved after the Python process exits.

### Context

Continue after P09. Persistence means data survives the process that created it. A database adapter implements the storage operations using a database. A parameterized query passes values separately from SQL text. A transaction groups database work that is either committed or rolled back.

### Task

Implement PostgreSQL-backed save and retrieve operations under `src/trade_ingestion/`, reusing the storage operations introduced in P09. Add a small table definition under `labs/01-reliable-ingestion/sql/`, use `trade_id` as the unique identifier and preserve decimal values in numeric columns. Connect using an environment variable and wire the command to this store. Commit each saved trade and close database resources on success or failure. Keep this to local single-trade persistence; batches, event history, updates, replay, API sources and cloud deployment remain later work.

### Acceptance Criteria

- [ ] A valid trade saved through the command is retrievable through the storage code after restarting Python.
- [ ] Stored quantity, price and notional retain their exact decimal values.
- [ ] A repeated identifier fails clearly and leaves the original stored trade unchanged.
- [ ] A failed write is rolled back, resources close, and the command exits unsuccessfully without exposing connection credentials.
- [ ] Existing input validation and summaries still work; Python code contains no embedded database credentials.

### Hint

Search for "Psycopg parameterized queries Decimal PostgreSQL" and "Python PostgreSQL transaction context manager". Pay attention to commit, rollback and who owns the connection.



## P11 — Protect trade calculations with automated tests

### Goal

Add repeatable checks so later changes cannot silently break validated trade calculations.

### Context

Continue after P10.

An automated test runs code and compares the result with an expected outcome. A regression is behavior that used to work but breaks after a change.

### Task

Add focused tests in `tests/test_trade_service.py` for the existing validation and calculation service. Cover valid decimal arithmetic and representative invalid fields. Keep this issue about testing the current service; database and command tests come later.

### Acceptance Criteria

- [ ] The tests pass for the existing service without a database connection.
- [ ] Cases include the exact result for `3 × 0.10`, missing fields and non-finite numbers.
- [ ] Deliberately changing the multiplication to an incorrect calculation makes a relevant test fail; restore the correct code afterward.
- [ ] The trade command still runs.

### Hint

Search for "pytest testing functions" and "pytest raises exception". Think about the behavior each assertion protects.



## P12 — Parse the complete trade-event record

### Goal

Accept versioned trade events so the program can later represent changes to an existing trade.

### Context

Continue after P11.

An event describes a change. `event_id` identifies that event; `trade_id` identifies the trade. A version is a positive integer indicating the order of changes. A timezone-aware timestamp includes an offset from UTC.

### Task

Extend validation under `src/trade_ingestion/` to accept the ten fields in the Lab 01 specification: event_id, trade_id, version, event_type, occurred_at, account_id, instrument_id, quantity, price and currency. Extend the synthetic fixture to this format. Accept CREATE, AMEND and CANCEL; for this exercise each event carries all fields and CANCEL retains the prior quantity/price. Reuse existing numeric/currency rules. Focus on parsing the event; storage semantics change tomorrow.

### Acceptance Criteria

- [ ] A valid full event reaches the calculation service with its identifiers, version and timestamp intact.
- [ ] Missing identifiers, non-integer or nonpositive versions, unknown event types and timestamps without a timezone are rejected.
- [ ] Existing decimal validation and its automated checks still pass after fixture updates.
- [ ] The command can process distinct valid CREATE events in the new format.

### Hint

Search for "Python datetime fromisoformat timezone aware" and "Python validate JSON integer bool". Distinguish identifying an event from identifying the trade it changes.



## P13 — Persist an append-only trade-event history

### Goal

Save each accepted event so changes to a trade remain available for later processing.

### Context

Continue after P12.

Append-only history adds new records without rewriting earlier ones. Several events may belong to one trade, so trade_id alone cannot identify a history row.

### Task

Add an event-history table under `labs/01-reliable-ingestion/sql/` and its save/read operations in the PostgreSQL storage code. Switch the command's persistence step to save complete validated events by event_id. Keep the starter trade table separate until current-state work begins. Use distinct event IDs for this increment; duplicate replay is the next task.

### Acceptance Criteria

- [ ] Two events with different event IDs for the same trade remain separately retrievable after restart.
- [ ] Reading an event returns all its validated fields with decimal and timestamp values intact.
- [ ] Saving a later event does not alter an earlier history row.
- [ ] The command still validates input and reports write failures.

### Hint

Search for "PostgreSQL append only event table primary key" and "psycopg insert returning". Consider which identifier must be unique.



## P14 — Make identical event replay harmless

### Goal

Recognize a repeated event so running the same input twice does not add duplicate history rows.

### Context

Continue after P13.

Replay means processing input again. Idempotent behavior means repeating the same operation has no additional unintended effect.

### Task

Update event-history saving in the PostgreSQL storage module to recognize an existing event_id. Compare its validated fields: skip an identical event; stop on changed content without overwriting it. Report the number skipped in the command. Keep this focused on exact duplicate replay; improving conflict details is the next task.

### Acceptance Criteria

- [ ] Processing the same valid fixture twice leaves one history row per event_id.
- [ ] The second run succeeds and reports the repeated events as skipped.
- [ ] New event IDs in a partially repeated file are still saved.
- [ ] An existing event is never overwritten with changed content.

### Hint

Search for "PostgreSQL ON CONFLICT DO NOTHING" and "idempotent data ingestion". Notice that matching identifiers do not automatically mean matching contents.



## P15 — Explain conflicting duplicate event IDs

### Goal

Report event identity conflicts clearly so bad source data cannot be mistaken for a harmless replay.

### Context

Continue after P14.

A conflicting duplicate reuses an event_id for different data. It is different from an identical repeat and must not silently change accepted history.

### Task

Improve the existing conflict path in the PostgreSQL storage module and command error handling. Return a specific conflict error containing the event ID and names of changed fields, without dumping the full payload. Compare validated field values rather than raw JSON formatting. Focus on conflict detection and reporting; quarantine comes later.

### Acceptance Criteria

- [ ] An identical event with reordered JSON keys is treated as a safe duplicate.
- [ ] Reusing an event ID with a different price, trade ID or version reports a conflict and returns a nonzero exit status.
- [ ] The original history row remains unchanged and later input lines are not processed.
- [ ] Exact replay still succeeds.

### Hint

Search for "Python custom exceptions" and "compare normalized records duplicate event". Think about semantic equality versus text equality.



## P16 — Create the current-trade view for CREATE events

### Goal

Maintain one current row per trade so consumers can read trade state without interpreting history.

### Context

Continue after P15.

Current state is the latest accepted representation of a trade. Event history records how that state was reached. A transaction makes related writes succeed or fail together.

### Task

Add a current-trade table in the lab SQL directory and update the ingestion service/storage boundary so a CREATE event for a new trade saves history and an ACTIVE current row in one transaction. Retain version and last event ID. Reject AMEND/CANCEL for now. This issue handles new trades only; updates follow next.

### Acceptance Criteria

- [ ] A new CREATE event produces matching history and ACTIVE current-state rows.
- [ ] A failure writing either row leaves neither new row committed.
- [ ] Replaying the identical CREATE leaves the same state.
- [ ] Unsupported changes fail clearly, and the command still runs.

### Hint

Search for "PostgreSQL transaction multiple inserts" and "event history current state projection". Focus on which writes must succeed together.



## P17 — Apply a higher-version trade amendment

### Goal

Update a trade from an AMEND event so corrected quantities and prices appear in current state.

### Context

Continue after P16.

An amendment changes an existing trade. Here each AMEND carries a complete replacement set of trade fields. History remains unchanged while current state advances.

### Task

Extend the current-state update in the ingestion service for a higher-version AMEND targeting an existing ACTIVE trade. Save its event and update the current row together. Reject missing trades, non-increasing versions and amendments after cancellation for now. Keep this to ordered amendments; handling older arrivals follows next.

### Acceptance Criteria

- [ ] CREATE version 1 followed by AMEND version 2 updates the stored values and notional to version 2.
- [ ] Both events remain in history and the current row records the amendment's event ID.
- [ ] An amendment for an unknown trade fails without leaving a partial event/state write.
- [ ] CREATE and identical-replay behavior still work.

### Hint

Search for "PostgreSQL update returning transaction" and "versioned records optimistic update". Consider what makes an incoming version eligible to replace current state.



## P18 — Prevent late events from regressing current state

### Goal

Handle older arrivals safely so processing order does not overwrite a newer accepted trade version.

### Context

Continue after P17.

A late event arrives after an event with a higher version. In this lab, the highest accepted version defines current state; arrival order does not.

### Task

Update version selection in the ingestion service/storage code. Retain a lower-version CREATE or AMEND in history without changing newer current state. An identical replay remains a no-op; reject a different event claiming the same trade/version. Continue to reject AMEND for an unknown trade. Focus on this ordering rule; missing-history reconstruction is outside this increment.

### Acceptance Criteria

- [ ] CREATE v1, AMEND v3, then AMEND v2 leaves current state at v3 and retains all three events.
- [ ] Replaying that input does not add rows or regress state.
- [ ] A different event claiming an already accepted trade/version fails clearly without overwriting either record.
- [ ] Ordered amendments and current-state transactions still work.

### Hint

Search for "PostgreSQL conditional upsert version column" and "out of order events latest state". Distinguish the history write from the decision to update current state.



## P19 — Keep cancelled trades with explicit status

### Goal

Apply CANCEL events so a cancelled trade remains traceable while no longer being active.

### Context

Continue after P18.

A cancellation ends a trade's active state; it does not erase its history. Use ACTIVE and CANCELLED as explicit current-state values.

### Task

Extend state processing for a higher-version CANCEL on an existing ACTIVE trade. Preserve its trade values and set status to CANCELLED in the same transaction as its history write. Keep the late-version rules: older events may enter history but cannot reactivate a newer cancelled state. Reject higher-version changes after cancellation for this starter contract; reinstatement is future work.

### Acceptance Criteria

- [ ] CREATE v1 then CANCEL v2 leaves a visible CANCELLED row with both events in history.
- [ ] Identical cancellation replay is harmless.
- [ ] A late older amendment cannot reactivate or change the cancelled current state.
- [ ] Cancellation of an unknown trade or a later attempted reinstatement fails clearly.

### Hint

Search for "soft delete status versus physical delete" and "event driven cancellation handling". Consider why retaining a row helps explain past activity.



## P20 — Reconcile active trade totals by currency

### Goal

Show per-currency totals so the learner can check that stored state matches expected financial results.

### Context

Continue after P19.

Reconciliation compares computed results with an independently known answer. Values in different currencies cannot be added into one meaningful monetary total without conversion.

### Task

Add a reconciliation function under `src/trade_ingestion/` that reads current state and reports ACTIVE trade counts and total notional per currency. Show it after successful file ingestion. Use a small synthetic multi-currency fixture whose expected results can be calculated by hand. Keep this to exact totals; dashboards and currency conversion come later.

### Acceptance Criteria

- [ ] Each currency has a separate count and exact decimal total.
- [ ] Cancelled trades are excluded and amendments use current values.
- [ ] A fixture with no active trades reports an empty or zero result clearly.
- [ ] Totals match a hand-calculated example and remain unchanged after replay.

### Hint

Search for "PostgreSQL GROUP BY currency SUM numeric" and "data reconciliation expected totals". Decide which rows belong in the reported population.



## P21 — Yield bounded batches from the input stream

### Goal

Group events into limited-size batches so later database work can avoid committing every row individually.

### Context

Continue after P20.

A generator produces values as they are needed. A bounded batch has a maximum number of records instead of growing with the full file.

### Task

Add a batching iterator under `src/trade_ingestion/` and use it between file reading and processing. Give the command a positive batch-size option. Keep the existing per-event database behavior for this issue; batch transactions follow next. Preserve source line positions for error messages.

### Acceptance Criteria

- [ ] Seven valid events with batch size three produce batch sizes 3, 3 and 1.
- [ ] Empty input produces no batches and nonpositive batch sizes are rejected.
- [ ] Iteration does not read or retain the whole source file before producing the first batch.
- [ ] Ingestion results, duplicate handling and error line numbers remain correct.

### Hint

Search for "Python generator batch iterator lazy evaluation". Pay attention to when input is consumed and what remains in memory.



## P22 — Commit a complete batch atomically

### Goal

Commit each batch as one unit so a failed event cannot leave half of that batch stored.

### Context

Continue after P21.

Atomic means all required changes in a transaction commit together or none do. A previously committed batch can remain saved even if a later batch fails.

### Task

Move transaction ownership from each event to the batch-processing boundary in the ingestion service and PostgreSQL storage code. Include history and current-state writes. On a validation or database failure, roll back the current batch and stop. Keep checkpoints and skipping bad records for later issues.

### Acceptance Criteria

- [ ] A successful batch commits all its event and state changes.
- [ ] A failure in the middle of a batch leaves no changes from that batch.
- [ ] Earlier committed batches remain saved and can be replayed safely.
- [ ] Per-currency results for a successful full run are unchanged.

### Hint

Search for "psycopg transaction context manager batch rollback". Consider which layer should own commit and rollback.



## P23 — Save a checkpoint with each committed file batch

### Goal

Resume file ingestion from saved progress so completed batches do not need to be read again.

### Context

Continue after P22.

A checkpoint is a saved source position. It is safe only when it cannot move beyond the work that has actually committed.

### Task

Add PostgreSQL-backed checkpoints to the local-file ingestion path. Identify the source using its content fingerprint and store the next unread line position with the batch's database work in the same transaction. Resume an unchanged source from that position; treat changed content as a different source. Keep this limited to immutable local files and one running worker.

### Acceptance Criteria

- [ ] A completed batch advances its checkpoint; a failed batch leaves the prior checkpoint unchanged.
- [ ] Restarting with the same unchanged file resumes from committed progress and reaches the same final state.
- [ ] A modified file is not silently resumed using another file's position.
- [ ] A completed-file rerun makes no unintended changes.

### Hint

Search for "transactional ingestion checkpoint" and "Python file content hash streaming". Think about both the progress position and the identity of its source.



## P24 — Verify recovery with a forced interruption

### Goal

Exercise restart behavior so the checkpoint guarantees are demonstrated under failure.

### Context

Continue after P23.

Failure injection deliberately interrupts work at a chosen point. An integration test checks components together, here the command and a real local test database.

### Task

Add a focused recovery integration test under `tests/integration/` that runs ingestion in a separate process, interrupts it during a batch, then reruns it. Use a disposable test database and deterministic synchronization so the test knows where the interruption occurred. Compare against an uninterrupted run. This issue is specifically about testing recovery, not adding new features.

### Acceptance Criteria

- [ ] The interrupted/restarted run produces the same event history, current state and currency totals as the uninterrupted run.
- [ ] No checkpoint points past required uncommitted work.
- [ ] The scenario can be repeated without relying on a lucky sleep duration.
- [ ] Existing fast service tests still pass.

### Hint

Search for "Python subprocess integration test terminate process" and "database crash recovery test synchronization". Choose an observable signal that establishes the failure point.



## P25 — Save invalid input separately and continue

### Goal

Retain rejected records so one bad input line does not prevent later valid trades from loading.

### Context

Continue after P24.

Quarantine is separate storage for input that could not be accepted, together with its source and rejection reason. Saving that rejection is part of processing the source line.

### Task

Add a rejected-record table and extend file ingestion to save malformed JSON, validation failures and identity/version conflicts there. Continue with later lines, counting accepted, repeated and rejected records separately. Save rejections with the batch/checkpoint transaction; use a per-record rollback boundary when needed to avoid partial event writes. Stop on infrastructure failures. This deliberately replaces the earlier stop-on-bad-input behavior; keep correction/reprocessing commands for future work.

### Acceptance Criteria

- [ ] A file with one invalid line between two valid events stores both valid events and one rejection with source line and reason.
- [ ] No partial history/current-state writes remain for a rejected record.
- [ ] Replay does not create duplicate rejection entries or skip unsaved required work.
- [ ] Database unavailability stops the run without advancing its checkpoint; summaries clearly report rejection counts.

### Hint

Search for "PostgreSQL savepoint recover failed statement" and "data ingestion quarantine table". Distinguish a bad record from an unavailable dependency.



## P26 — Read trades through a paginated local HTTP source

### Goal

Add a second source so the ingestion service can process events that arrive in pages over HTTP.

### Context

Continue after P25.

A page is one limited group of results. A source adapter translates source-specific details into the event stream used by the existing ingestion service.

### Task

Add an HTTP source adapter under `src/trade_ingestion/sources/` and a small local synthetic HTTP fixture under `tests/fixtures/`. Use a response containing events and an explicit next-page value; select this source through the command. Reuse validation and storage. For this first adapter, replay from page one and rely on event deduplication; local-file checkpoints remain specific to files. Do not use a real banking service.

### Acceptance Criteria

- [ ] At least two pages of synthetic events produce the same current state and totals as equivalent file input.
- [ ] Processing stops when the source explicitly reports no next page, including when the final events list is empty.
- [ ] Replaying the HTTP source creates no duplicate history.
- [ ] The local-file source still works and HTTP resources are closed.

### Hint

Search for "Python HTTP pagination iterator adapter pattern". Separate how events are fetched from how they are validated and stored.



## P27 — Bound HTTP timeouts and retries

### Goal

Limit how long ingestion waits on an HTTP source so transient failures can recover without hanging forever.

### Context

Continue after P26.

A timeout limits waiting for a response. A retry repeats a failed request. Transient failures may recover; permanent request errors usually will not.

### Task

Extend the HTTP adapter with explicit connection/read timeouts and a finite retry count for transport failures and selected transient HTTP statuses. Keep requests on the same page until that page succeeds. Stop with a useful message when the limit is reached; do not retry ordinary permanent client errors. Use the local fixture to trigger failures.

### Acceptance Criteria

- [ ] A temporary failure followed by success ingests the page once.
- [ ] Repeated failures stop after the configured number of attempts and return a nonzero command status.
- [ ] A permanent client error stops without consuming the retry budget.
- [ ] A failed page cannot cause the adapter to skip to the next page, and file ingestion still works.

### Hint

Search for "Python HTTP timeout bounded retries exponential backoff". Pay attention to which failures are safe to retry and when progress advances.



## P28 — Add run-level ingestion logs

### Goal

Emit concise run and batch messages so the learner can see where processing succeeded or failed.

### Context

Continue after P27.

A run identifier links messages from one command execution. Logs record operational events; they should help explain behavior without exposing passwords or whole trade payloads.

### Task

Add standard Python logging around the command and batch-processing boundary. Include a run identifier, source type, batch result and accepted/repeated/rejected counts. Keep user-facing errors understandable. Focus on terminal logs; external monitoring services and dashboards are outside this issue.

### Acceptance Criteria

- [ ] Messages from one run share an identifier, and a later run receives a different one.
- [ ] Successful runs report reconciled processing counts and a completion message.
- [ ] A failed run records the failure without claiming successful completion.
- [ ] Logs do not expose database credentials or full input payloads, and ingestion results remain unchanged.

### Hint

Search for "Python logging contextual information LoggerAdapter". Choose fields that help connect an error to a particular run and batch.



## P29 — Install the project as a Python command

### Goal

Package the working program so it can run from outside the repository directory.

### Context

Continue after P28.

A package groups importable Python code. A command entry point connects an installed terminal command to a Python function.

### Task

Add `pyproject.toml` and package metadata for `src/trade_ingestion/`, declare runtime dependencies, and expose the ingestion command through an entry point. Adjust imports and fixture-path handling as needed. Keep this to local installation; publishing to a package registry and container deployment come later.

### Acceptance Criteria

- [ ] A clean virtual environment can install the project and its declared dependencies.
- [ ] The installed command shows help and processes an explicitly supplied absolute input path from another working directory.
- [ ] Importing the package does not start ingestion.
- [ ] Existing automated checks pass using the installed package.

### Hint

Search for "Python pyproject src layout console scripts". Pay attention to the difference between the working directory and installed package resources.



## P30 — Run the existing checks in GitHub Actions

### Goal

Automate the implemented checks so each proposed code change receives repeatable feedback.

### Context

Continue after P29.

Continuous integration, or CI, runs checks automatically when code changes. A service container provides a temporary dependency such as PostgreSQL for that run.

### Task

Add a workflow under `.github/workflows/` that installs the package and runs the existing fast tests and PostgreSQL recovery integration test on pull requests. Use a disposable PostgreSQL service and synthetic fixtures. Keep this to validation; automatic merging, deployments and production credentials are outside this issue.

### Acceptance Criteria

- [ ] A pull request triggers the workflow and installs the project in a clean runner.
- [ ] Fast tests and database recovery checks run against the disposable database and pass.
- [ ] A failing test makes the workflow fail visibly.
- [ ] The workflow needs no production credentials and does not alter branch protection or merge code.

### Hint

Search for "GitHub Actions Python PostgreSQL service container pytest". Pay attention to database readiness and separating test connection settings from real credentials.
