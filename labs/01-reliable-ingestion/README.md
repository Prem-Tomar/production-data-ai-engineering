# Lab 01 — Reliable Financial-Data Ingestion

**Status:** Specification only; implementation is the learning assignment.

**Purpose:** Learn foundational Python by building an ingestion program whose correctness and restart behavior can be demonstrated. Work locally before introducing cloud or Spark.

## Scenario

A fictional source emits immutable trade events. Each event has `event_id`, `trade_id`, `version`, `event_type`, `occurred_at`, `account_id`, `instrument_id`, `quantity`, `price` and `currency`. Use `CREATE`, `AMEND` and `CANCEL` events; retain cancelled trades with explicit status.

Declare the source contract: an event ID uniquely identifies one payload; trade versions are positive integers; the highest version defines current state; a conflicting payload under the same ID is an error. Timestamps include a time zone. Represent quantity and price using declared decimal precision and scale. Do not silently mix currencies in totals.

Start with generated JSONL files containing about 1,000 events, including intentional duplicates, late versions, amendments, cancellations and invalid records. Introduce a paginated API adapter after the local source works.

## Implementation increments

1. Define a small hand-checked fixture and the expected current trade state. Write down validation and reconciliation rules.
2. Implement Python parsing and validation, with explicit errors and correctly handled decimal/timestamp values.
3. Load valid events into PostgreSQL using parameterized SQL and a documented transaction boundary. Preserve raw event history and derive a current-state table.
4. Add bounded batches, checkpoints, duplicate handling and reconciliation. Prevent an older arriving event from overwriting a later version.
5. Add configuration, logs, an installable command and automated checks. Keep credentials outside Git.
6. Force an interruption, replay the source and explain the resulting state. Add an API source to exercise pagination, timeouts and bounded retries.

## Acceptance criteria

- A clean environment can run the fixture using the documented commands and declared Python/database versions.
- The known fixture produces exactly the expected trade states and per-currency aggregates.
- Reprocessing identical input makes no unintended changes.
- Conflicting duplicate IDs are surfaced and quarantined or rejected according to the declared policy.
- Late older versions do not regress current trade state; a duplicate cancellation is safe.
- Invalid records are counted and visible, with a documented retry/correction route.
- The checkpoint never advances past uncommitted required work. Describe recovery if the process fails between database commit and checkpoint persistence.
- Terminating the process during a batch and restarting eventually gives the same valid result as an uninterrupted run.
- Increasing input size does not require loading the whole file into memory; retain peak-memory measurements.
- Logs identify runs, counts and errors without credentials or unnecessary payloads.
- Tests cover the stated failure cases and a reviewer can explain their purpose.

## Submission

Add implementation under `src/`, tests under `tests/` and small generated fixtures or a generator. Add dependency/build configuration as part of implementation. Record real setup/test commands only after running them.

Complete a [milestone evidence record](../../templates/milestone-evidence.md), an [architecture decision](../../templates/architecture-decision.md) for checkpoint/transaction behavior and a short [runbook](../../templates/runbook.md). Update the [project tracker](../../docs/AI-Data-Project-Tracker.md).

## Independent learning check

Explain the difference between object identity and equality, why mutable defaults can cause defects, why Decimal matters here, how iteration bounds memory and who closes database/file resources. Then implement an unfamiliar event validation rule and diagnose an injected restart defect without a tutorial.
