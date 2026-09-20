# Daily Python tasks

These are the versioned descriptions for GitHub issues #1–#30. Each task supplies its own inputs, setup and any required starter code. Day order guides study; completion of another issue or availability of another person is not required. Use an installed Python 3 interpreter and run commands from the repository root. Create folders named by a task if they do not exist.

The [Python study notes](PYTHON-COACHING.md) contain explanations and runnable examples for Days 1–10. The later tasks share trade-processing concepts and provide components to assess and integrate into the project. These descriptions and starter examples are learning material, not completed project implementation.

## Day 01: Calculate a trade amount

[GitHub issue #1](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/1)

### Goal

Calculate the value of a small synthetic trade.

### Context

The interpreter runs Python expressions. Start it by entering `python` in a terminal; `>>>` is its input prompt.

Read the [explanation and example](PYTHON-COACHING.md#first-session-what-python-does).

### Task

Enter quantity 3 and price 10, multiply them, and display the result. Repeat with quantity 5 and price 10, then quantity 2 and price 7. Use whole numbers; no file is needed.

### Acceptance Criteria

- [ ] The three calculations display 30, 50 and 14 respectively.
- [ ] Changing an input and rerunning the multiplication updates the displayed result.

### Hint

Search for "Python interactive interpreter multiplication".

## Day 02: Use numbers and text correctly

[GitHub issue #2](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/2)

### Goal

Distinguish numeric addition from joining text.

### Context

Text containing digits is still text until converted. Open a Python interpreter with `python` in a terminal.

Read the [explanation and example](PYTHON-COACHING.md#day-02-numbers-and-text).

### Task

Add `3 + 2`, then `"3" + "2"`. Convert quantity text `"4"` to a whole number and multiply it by 10. Try converting `"four"`, then correct it to `"4"` and repeat.

### Acceptance Criteria

- [ ] Numeric addition gives 5; text addition gives "32".
- [ ] Converted quantity "4" multiplied by 10 gives 40.
- [ ] "four" raises ValueError; correcting it to "4" makes conversion succeed.

### Hint

Search for "Python int str conversion".

## Day 03: Run a trade script locally

[GitHub issue #3](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/3)

### Goal

Save a small program that can be run again.

### Context

A script is a `.py` file of instructions. A virtual environment provides a separate project interpreter.

Read the [explanation and example](PYTHON-COACHING.md#day-03-running-a-script).

### Task

From the repository root, run `python -m venv .venv`. Create any missing folders and `src/trade_ingestion/main.py`. Print `Trade tool ready`, then the product of quantity 3 and price 10. Run with `.\.venv\Scripts\python.exe src/trade_ingestion/main.py`. Change quantity to 5 and run again. Keep `.venv` out of Git.

### Acceptance Criteria

- [ ] The first run prints Trade tool ready and 30.
- [ ] After the change, the run prints Trade tool ready and 50.
- [ ] Running again without edits produces the same output.

### Hint

Search for "Python venv run script".


## Day 04: Convert a source quantity

[GitHub issue #4](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/4)

### Goal

Use a text quantity in arithmetic.

### Context

`int()` converts whole-number text. Invalid text raises ValueError.

Read the [explanation and example](PYTHON-COACHING.md#day-04-converting-source-values).

### Task

Create `src/trade_ingestion/day04.py` and any missing folders. Set quantity text to `"12"` and price to 2. Convert the quantity before multiplying and print the amount. Repeat with `"0"`, then `"abc"`; leave conversion errors visible.

Run from the repository root with `python src/trade_ingestion/day04.py`.

### Acceptance Criteria

- [ ] "12" produces amount 24; "0" produces 0.
- [ ] "abc" raises ValueError.
- [ ] Restoring "12" produces 24 again.

### Hint

Search for "Python int ValueError".

## Day 05: Clean currency text

[GitHub issue #5](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/5)

### Goal

Display consistent currency labels.

### Context

String methods return new text. Normalization changes presentation; it does not validate a currency.

Read the [explanation and example](PYTHON-COACHING.md#day-05-cleaning-strings).

### Task

Create `src/trade_ingestion/day05.py` and any missing folders. For each separate run, set currency to `" usd "`, `"inr"` or `" xyz "`. Remove surrounding spaces, uppercase the result and print it. Also print the original text with `repr()`.

Run from the repository root with `python src/trade_ingestion/day05.py`.

### Acceptance Criteria

- [ ] The cleaned outputs are USD, INR and XYZ respectively.
- [ ] The original " usd " still contains its surrounding spaces.
- [ ] XYZ is normalized without claiming it is a supported currency.

### Hint

Search for "Python strip upper repr".

## Day 06: Reject nonpositive quantities

[GitHub issue #6](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/6)

### Goal

Calculate an amount only for a positive quantity.

### Context

An `if` statement selects a block using a condition; indentation defines the block.

Read the [explanation and example](PYTHON-COACHING.md#day-06-choosing-a-branch).

### Task

Create `src/trade_ingestion/day06.py` and any missing folders. Set price to 10. Use an `if`/`else` to print the amount for a positive quantity and `Rejected quantity` otherwise. Run separately with quantities 3, 0 and -2.

Run from the repository root with `python src/trade_ingestion/day06.py`.

### Acceptance Criteria

- [ ] Quantity 3 prints 30.
- [ ] Quantities 0 and -2 print Rejected quantity and no amount.

### Hint

Search for "Python if else indentation".


## Day 07: Manage a list of trade IDs

[GitHub issue #7](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/7)

### Goal

Store and update ordered identifiers.

### Context

A list stores items in order; its first index is 0.

Read the [explanation and example](PYTHON-COACHING.md#day-07-lists-and-positions).

### Task

Create `src/trade_ingestion/day07.py` and any missing folders. Create the list `["T1", "T2"]`. Append `"T3"`, replace `"T2"` with `"T4"`, then print the whole list and its first item. Use separate statements.

Run from the repository root with `python src/trade_ingestion/day07.py`.

### Acceptance Criteria

- [ ] The final list is ['T1', 'T4', 'T3'].
- [ ] The first item is T1.

### Hint

Search for "Python list append indexing".

## Day 08: Process every trade ID

[GitHub issue #8](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/8)

### Goal

Visit every input item and count it.

### Context

A `for` loop visits collection items. With an empty list, its body runs zero times.

Read the [explanation and example](PYTHON-COACHING.md#day-08-loops).

### Task

Create `src/trade_ingestion/day08.py` and any missing folders. Start with `["T1", "T2", "T3"]`. Print each ID on its own line and a final processed count. Repeat with an empty list and with `["T1", "T2", "T3", "T4"]`.

Run from the repository root with `python src/trade_ingestion/day08.py`.

### Acceptance Criteria

- [ ] The first input prints three IDs and count 3.
- [ ] Empty input prints count 0 without an error.
- [ ] The four-item input prints four IDs and count 4 with the same loop.

### Hint

Search for "Python for loop counter".

## Day 09: Build a trade record

[GitHub issue #9](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/9)

### Goal

Keep related trade fields together.

### Context

A dictionary stores values under named keys.

Read the [explanation and example](PYTHON-COACHING.md#day-09-dictionary-records).

### Task

Create `src/trade_ingestion/day09.py` and any missing folders. Create a dictionary with `trade_id="T1"`, `quantity="3"`, `price="10"` and `currency="USD"`. Print all four fields by reading their keys. Rerun after changing only trade_id to T2, then only currency to INR. Keep quantity and price as text.

Run from the repository root with `python src/trade_ingestion/day09.py`.

### Acceptance Criteria

- [ ] The first output contains T1, 3, 10 and USD.
- [ ] Changing the field values produces T2 and then INR without changing the print expression.

### Hint

Search for "Python dictionary access values".


## Day 10: Find repeated trade IDs

[GitHub issue #10](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/10)

### Goal

Count first occurrences and repeated arrivals.

### Context

A set tracks distinct values. Use the original list for processing order.

Read the [explanation and example](PYTHON-COACHING.md#day-10-sets-and-repeated-values).

### Task

Create `src/trade_ingestion/day10.py` and any missing folders. Scan `["T1", "T2", "T1"]` using a set of seen IDs. Print each repeated arrival and final distinct/repeat counts. Also run with `["T1", "T10"]`, `["T1", "T1", "T1"]` and `[]`.

Run from the repository root with `python src/trade_ingestion/day10.py`.

### Acceptance Criteria

- [ ] T1, T2, T1 reports T1 once, distinct 2 and repeats 1.
- [ ] T1 and T10 gives distinct 2 and repeats 0.
- [ ] Three T1 arrivals give distinct 1 and repeats 2; empty input gives both counts 0.

### Hint

Search for "Python set membership duplicates".

## Day 11: Return a reusable calculation

[GitHub issue #11](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/11)

### Goal

Use a calculation's result in another expression.

### Context

`return` sends a value to the caller; printing only displays text.

### Task

Create `src/trade_ingestion/day11.py` and any missing folders. Write `calculate_amount(quantity, price)` for whole numbers. Return their product without printing inside the function. Call it with (3, 10) and (4, 5); print each result and their sum in the calling code.

Run from the repository root with `python src/trade_ingestion/day11.py`.

### Acceptance Criteria

- [ ] The calls return 30 and 20; their sum is 50.
- [ ] The function itself prints nothing.

### Hint

Search for "Python function return print".

## Day 12: Fix a scope bug

[GitHub issue #12](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/12)

### Goal

Use explicit inputs and independent enclosing state.

### Context

Assignment inside a function makes a name local unless declared otherwise. `global` targets the module binding; `nonlocal` targets an enclosing function binding.

### Task

Create `src/trade_ingestion/day12.py` and any missing folders. Run this starter, observe its error, then change `inspect_limit` to accept a limit argument and return it without changing the module variable. Add `make_counter()` returning an inner function that increments an enclosing count with `nonlocal`.

```python
limit = 100

def inspect_limit():
    print(limit)
    limit = 5

inspect_limit()
```

Run from the repository root with `python src/trade_ingestion/day12.py`.

### Acceptance Criteria

- [ ] The starter raises UnboundLocalError.
- [ ] Repaired calls with 5 and 10 return 5 and 10; module limit remains 100.
- [ ] For counters a and b created separately, a(), a(), b() return 1, 2, 1.

### Hint

Search for "Python local assignment binding global nonlocal UnboundLocalError".


## Day 13: Stop helper calls sharing a list

[GitHub issue #13](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/13)

### Goal

Give omitted collections fresh state on each call.

### Context

A mutable default is created once when the function is defined. Two names can also deliberately refer to the same list.

### Task

Create `src/trade_ingestion/day13.py` and any missing folders. Run this starter, then fix the default-call behavior. Preserve in-place appending when an explicit list is passed.

```python
def collect(trade_id, records=[]):
    records.append(trade_id)
    return records

first = collect("T1")
second = collect("T2")
print(first, second)
```

Run from the repository root with `python src/trade_ingestion/day13.py`.

### Acceptance Criteria

- [ ] After repair, first is ['T1'] and second is ['T2'].
- [ ] For shared=[], alias=shared, calling collect('T3', shared) makes both names show ['T3'].
- [ ] Rebinding alias to a new empty list leaves shared containing T3.

### Hint

Search for "Python mutable default argument aliasing rebinding".

## Day 14: Repair a failing calculation

[GitHub issue #14](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/14)

### Goal

Use a traceback to locate a conversion failure.

### Context

A traceback shows the call path and failing line. Multiplying text by an integer repeats text, so conversion must be explicit.

### Task

Create `src/trade_ingestion/day14.py` and any missing folders. Run this broken example, locate the failing conversion, and correct the price input. Do not suppress the error.

```python
def calculate_amount(quantity, price_text):
    return quantity * int(price_text)

print(calculate_amount(3, "abc"))
```

Run from the repository root with `python src/trade_ingestion/day14.py`.

### Acceptance Criteria

- [ ] The starter raises ValueError at int(price_text).
- [ ] Price text "10" with quantity 3 prints 30.
- [ ] Quantity 2 with price text "7" prints 14; quantity 4 with "5" prints 20.

### Hint

Search for "Python traceback ValueError debugging".

## Day 15: Return useful validation failures

[GitHub issue #15](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/15)

### Goal

Reject invalid quantity input with a clear message.

### Context

A function can raise ValueError; the caller can catch that expected failure.

### Task

Create `src/trade_ingestion/day15.py` and any missing folders. Write `parse_quantity(raw)` returning a positive integer. Treat None and empty text as missing. Reject nonnumeric text and zero/negative numbers. In a separate caller, print either `quantity: <value>` or `Rejected quantity: <reason>`. Run each listed input separately.

Run from the repository root with `python src/trade_ingestion/day15.py`.

### Acceptance Criteria

- [ ] "3" returns 3 and prints quantity: 3.
- [ ] None, "", "abc", 0 and -2 each print a rejection reason with no calculated amount.
- [ ] A separate run with "5" succeeds.

### Hint

Search for "Python raise ValueError try except".


## Day 16: Move helpers into modules

[GitHub issue #16](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/16)

### Goal

Import reusable logic without starting a program.

### Context

Python executes top-level statements on import. An entry guard restricts command execution.

### Task

Create `src/trade_ingestion/day16/` with empty `__init__.py`, `calculation.py`, `validation.py` and `main.py`. Put `calculate_amount(quantity, price)` returning their product in calculation.py. Put `parse_quantity(raw)` converting text to a positive integer or raising ValueError in validation.py. In main.py import both, parse `"3"`, multiply by 10 and print the amount behind an entry guard.

Run `python -m src.trade_ingestion.day16.main` from the repository root. Check imports separately with `python -c "from src.trade_ingestion.day16.calculation import calculate_amount; from src.trade_ingestion.day16.validation import parse_quantity"`.

### Acceptance Criteria

- [ ] The module command prints 30.
- [ ] The import command prints nothing and processes no input.
- [ ] Calling calculate_amount(2, 7) from an interpreter returns 14.

### Hint

Search for "Python modules relative imports __name__ main".

## Day 17: Calculate amounts with Decimal

[GitHub issue #17](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/17)

### Goal

Calculate exact decimal amounts from source text.

### Context

Decimal constructed from text avoids a preliminary binary-float conversion. Reject non-finite values before comparing them.

### Task

Create `src/trade_ingestion/day17.py` and any missing folders. Write `calculate_amount(quantity_text, price_text)`. Convert both using Decimal and require finite positive values with at most two fractional digits in the supplied text. Reject bad values with ValueError. Return their Decimal product; do not convert through float.

Run from the repository root with `python src/trade_ingestion/day17.py`.

### Acceptance Criteria

- [ ] ("3", "0.10") returns Decimal equal to 0.30; ("3", "10") returns 30.
- [ ] Either operand containing "NaN", "Infinity", "abc", "0", "-2" or "1.001" is rejected.
- [ ] The representation "1.000" is rejected under this task's two-fractional-digit rule.

### Hint

Search for "Python Decimal string is_finite as_tuple exponent".

## Day 18: Parse an event timestamp

[GitHub issue #18](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/18)

### Goal

Accept timestamps that identify an explicit instant.

### Context

An offset relates local time to UTC. A timestamp without one does not identify an unambiguous instant.

### Task

Create `src/trade_ingestion/day18.py` and any missing folders. Write `parse_timestamp(text)` using datetime. Return an aware datetime and reject missing offsets or malformed text with ValueError. Compare the two valid inputs below.

Run from the repository root with `python src/trade_ingestion/day18.py`.

### Acceptance Criteria

- [ ] 2026-09-20T10:00:00+05:30 and 2026-09-20T04:30:00+00:00 compare equal.
- [ ] 2026-09-20T10:00:00 and not-a-time are rejected.

### Hint

Search for "Python datetime fromisoformat utcoffset aware".


## Day 19: Read a source file safely

[GitHub issue #19](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/19)

### Goal

Close a file after normal reading and failures.

### Context

A `with` block manages a file's lifetime.

### Task

Create `src/trade_ingestion/day19.py` and any missing folders. Create `labs/01-reliable-ingestion/fixtures/day19.txt` containing T1, T2 and T3 on separate lines, and an empty day19-empty.txt. Read with a context manager and print each stripped line. Run a second case raising `RuntimeError("read failed")` inside the block after its first line; catch it outside the block and inspect the file object's `closed` property.

Run from the repository root with `python src/trade_ingestion/day19.py`.

### Acceptance Criteria

- [ ] Normal reading prints T1, T2, T3 exactly once; the file is closed afterward.
- [ ] The empty file prints no records and closes.
- [ ] The injected error is observable and the file is closed after it.

### Hint

Search for "Python with open context manager closed".

## Day 20: Parse JSONL trades

[GitHub issue #20](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/20)

### Goal

Decode one trade dictionary per source line.

### Context

JSONL contains one JSON value per line. Valid JSON can still be missing a required field.

### Task

Create `src/trade_ingestion/day20.py` and any missing folders. Write a file reader using `json.loads` per line. Require each decoded value to be a dictionary containing trade_id, quantity, price, currency and timestamp. Print the trade ID. Report the line number and stop on malformed JSON or missing fields; use a context manager.

Create `labs/01-reliable-ingestion/fixtures/day20.jsonl` with these two lines:

```jsonl
{"trade_id":"T1","quantity":"3","price":"10","currency":"USD","timestamp":"2026-09-20T04:30:00+00:00"}
{"trade_id":"T2","quantity":"2","price":"5","currency":"INR","timestamp":"2026-09-20T10:00:00+05:30"}
```

Run from the repository root with `python src/trade_ingestion/day20.py`.

### Acceptance Criteria

- [ ] The fixture prints T1 then T2.
- [ ] Replacing line 2 with {bad json reports line 2 and stops.
- [ ] Replacing line 2 with {"trade_id":"T2"} reports missing fields on line 2.
- [ ] The file closes after success and either failure.

### Hint

Search for "Python json loads JSONDecodeError enumerate".

## Day 21: Stream records with a generator

[GitHub issue #21](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/21)

### Goal

Read records only as they are requested.

### Context

A generator pauses at `yield`. Explicit close releases its resources after early stopping.

### Task

Create `src/trade_ingestion/day21.py` and any missing folders. Write `read_records(path)` that opens a file in a with block and yields each decoded JSON line without loading the whole file. Include the line number in a decoding error. Create day21.jsonl under `labs/01-reliable-ingestion/fixtures/` with these three lines:

```jsonl
{"trade_id":"T1"}
{"trade_id":"T2"}
{bad json
```

Use a `finally` block outside the file's with block to print its `closed` property when iteration exits.

Run from the repository root with `python src/trade_ingestion/day21.py`.

### Acceptance Criteria

- [ ] Calling next() once returns T1 without reading the malformed third line.
- [ ] Continuing returns T2 and then reports an error on line 3; the file is closed.
- [ ] In a fresh run, consuming one item and calling generator.close() closes the file.
- [ ] With only the two valid lines, exhaustion closes the file.

### Hint

Search for "Python generator yield close lazy iteration finally".


## Day 22: Create a validated trade object

[GitHub issue #22](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/22)

### Goal

Represent valid trade fields with appropriate Python types.

### Context

A dataclass groups fields; annotations alone do not validate input.

### Task

Create `src/trade_ingestion/day22.py` and any missing folders. Define a Trade dataclass and `parse_trade(raw)` for trade_id, quantity, price, currency and timestamp. Require nonempty ID/currency strings, finite positive Decimal quantity/price from text, and a datetime with an offset. Reject invalid input with ValueError. Use these raw dictionaries (one JSON object per line) as inputs:

```jsonl
{"trade_id":"T1","quantity":"3","price":"10","currency":"USD","timestamp":"2026-09-20T04:30:00+00:00"}
{"trade_id":"T2","quantity":"2","price":"5","currency":"INR","timestamp":"2026-09-20T10:00:00+05:30"}
```

Create both objects and print quantity multiplied by price for each.

Run from the repository root with `python src/trade_ingestion/day22.py`.

### Acceptance Criteria

- [ ] The objects hold distinct IDs, Decimal numbers and offset-bearing datetimes; their amounts are 30 and 10.
- [ ] Removing quantity, using price "NaN", or removing the timestamp offset produces ValueError.
- [ ] The first object's fields retain their values when the second object is created.

### Hint

Search for "Python dataclass Decimal datetime runtime validation".

## Day 23: Fix late-bound validation rules

[GitHub issue #23](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/23)

### Goal

Keep each generated predicate's intended limit.

### Context

A closure looks up an enclosing name when called, which can happen after a loop has rebound it.

### Task

Create `src/trade_ingestion/day23.py` and any missing folders. Run this starter and fix the closure bug. Each predicate must retain the limit from its creation iteration.

```python
def build_rules(limits):
    rules = []
    for limit in limits:
        rules.append(lambda quantity: quantity <= limit)
    return rules

rules = build_rules([5, 10])
print([rule(7) for rule in rules])
```

Run from the repository root with `python src/trade_ingestion/day23.py`.

### Acceptance Criteria

- [ ] The starter incorrectly prints [True, True] for 7; the repaired version prints [False, True].
- [ ] Quantity 3 gives [True, True]; quantity 12 gives [False, False].
- [ ] After build_rules([1, 2]), the original rules still give [False, True] for 7.

### Hint

Search for "Python closure late binding lambda loop default argument".

## Day 24: Test a calculation and a rejection

[GitHub issue #24](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/24)

### Goal

Detect a broken calculation automatically.

### Context

pytest runs test functions and reports failing assertions. The complete function under test is included.

### Task

Create `src/trade_ingestion/day24.py` with this function:

```python
from decimal import Decimal

def calculate_amount(quantity_text, price_text):
    quantity = Decimal(quantity_text)
    price = Decimal(price_text)
    if not quantity.is_finite() or not price.is_finite():
        raise ValueError("non-finite amount")
    if quantity <= 0 or price <= 0:
        raise ValueError("amount must be positive")
    return quantity * price
```

Create `tests/test_day24.py` importing it with `from src.trade_ingestion.day24 import calculate_amount`. Add a result check for ("3", "0.10") and an expected ValueError check for ("0", "10"). From the repository root install with `python -m pip install pytest`, then run `python -m pytest tests/test_day24.py`. Temporarily change multiplication to addition and rerun; restore multiplication afterward.

### Acceptance Criteria

- [ ] Both checks pass for the supplied function.
- [ ] The calculation check fails when multiplication becomes addition.
- [ ] Both checks pass again after restoring multiplication.

### Hint

Search for "pytest assert raises Decimal".


## Day 25: Test validation boundaries

[GitHub issue #25](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/25)

### Goal

Cover several invalid cases with one test structure.

### Context

A parameterized test runs one assertion pattern with different inputs. The validator is supplied.

### Task

Create `src/trade_ingestion/day25.py` using the validator below. Create `tests/test_day25.py` importing `validate` from `src.trade_ingestion.day25`. Install pytest with `python -m pip install pytest`; run `python -m pytest tests/test_day25.py` from the repository root.

```python
from datetime import datetime
from decimal import Decimal, InvalidOperation

def validate(raw):
    try:
        quantity = Decimal(raw["quantity"])
        stamp = datetime.fromisoformat(raw["timestamp"])
    except (KeyError, TypeError, ValueError, InvalidOperation) as exc:
        raise ValueError("missing or invalid field") from exc
    if not quantity.is_finite() or quantity <= 0:
        raise ValueError("quantity must be finite and positive")
    if stamp.utcoffset() is None:
        raise ValueError("timestamp needs an offset")
    return quantity, stamp
```

Start with `{"quantity":"1", "timestamp":"2026-09-20T04:30:00+00:00"}`. Parameterize separate copies with quantity removed; quantity "NaN", "Infinity", "-1" or "0"; and the timestamp replaced with `"2026-09-20T04:30:00"`. Add a separate passing check for the unchanged valid input.

### Acceptance Criteria

- [ ] All six invalid variants raise ValueError.
- [ ] The valid input returns Decimal 1 and an aware datetime.
- [ ] Each invalid case is reported separately by pytest; all seven checks pass.

### Hint

Search for "pytest parametrize boundary cases".

## Day 26: Connect a local transformation

[GitHub issue #26](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/26)

### Goal

Compose reading and calculation into a runnable program.

### Context

Composition connects functions. The supplied helpers handle this fixture's JSON and amounts; they are not a complete trade validator.

### Task

Create `src/trade_ingestion/day26.py` and any missing folders. Copy these helpers, then add `run(path)` to connect them. Print each ID/amount and a final count only on success. On a transform error, include its line number and stop. Explicitly close the generator when the caller stops early.

```python
import json
from decimal import Decimal

def read_rows(path):
    with open(path, encoding="utf-8") as source:
        for line_number, line in enumerate(source, 1):
            try:
                yield line_number, json.loads(line)
            except json.JSONDecodeError as exc:
                raise ValueError(f"line {line_number}: invalid JSON") from exc

def transform(raw):
    quantity = Decimal(raw["quantity"])
    price = Decimal(raw["price"])
    if not quantity.is_finite() or not price.is_finite():
        raise ValueError("non-finite amount")
    if quantity <= 0 or price <= 0:
        raise ValueError("amount must be positive")
    return raw["trade_id"], quantity * price
```

Create `labs/01-reliable-ingestion/fixtures/day26.jsonl` with these two lines:

```jsonl
{"trade_id":"T1","quantity":"3","price":"10","currency":"USD","timestamp":"2026-09-20T04:30:00+00:00"}
{"trade_id":"T2","quantity":"2","price":"5","currency":"INR","timestamp":"2026-09-20T10:00:00+05:30"}
```

Call run with the fixture path. For the failure case, change line 2 quantity to "0" and append a copy of valid line 1 with ID T3.

Run from the repository root with `python src/trade_ingestion/day26.py`.

### Acceptance Criteria

- [ ] The valid fixture prints T1 30, T2 10 and count 2.
- [ ] The invalid fixture reports line 2, never prints T3 and does not print a success count.
- [ ] The source closes after either run.

### Hint

Search for "Python function composition generator close try finally".

## Day 27: Choose the input path

[GitHub issue #27](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/27)

### Goal

Select a source file without editing code.

### Context

argparse parses command-line options. A quoted shell argument preserves spaces in a path.

### Task

Create `src/trade_ingestion/day27.py` and any missing folders. Use this supplied processor and add an entry function with optional `--input`, defaulting to `labs/01-reliable-ingestion/fixtures/day27.jsonl`. Print its returned count.

```python
import json

def process(path):
    count = 0
    with open(path, encoding="utf-8") as source:
        for line_number, line in enumerate(source, 1):
            try:
                json.loads(line)
            except json.JSONDecodeError as exc:
                raise ValueError(f"line {line_number}: invalid JSON") from exc
            count += 1
    return count
```

Create that default fixture containing two lines: `{"trade_id":"T1"}` and `{"trade_id":"T2"}`. Create `labs/01-reliable-ingestion/fixtures/day27 other.jsonl` containing only `{"trade_id":"T3"}`.

Run from the repository root with `python src/trade_ingestion/day27.py`.

### Acceptance Criteria

- [ ] The command without options prints 2.
- [ ] Adding --input "labs/01-reliable-ingestion/fixtures/day27 other.jsonl" prints 1.
- [ ] --help prints usage and exits without calling process, including when the default fixture is absent.

### Hint

Search for "Python argparse default __name__ main".


## Day 28: Log progress and failures

[GitHub issue #28](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/28)

### Goal

Locate failed runs without exposing full trade records.

### Context

Standard logging records events with severity. A nonzero exit code signals failure to the shell.

### Task

Create `src/trade_ingestion/day28.py` and any missing folders. Copy the processor below. Add a command boundary that accepts a positional file path, logs start with the path, calls process, logs count/completion on success, and logs the error with exit code 1 on failure. Configure INFO logging.

```python
import json

def process(path):
    count = 0
    with open(path, encoding="utf-8") as source:
        for line_number, line in enumerate(source, 1):
            try:
                json.loads(line)
            except json.JSONDecodeError as exc:
                raise ValueError(f"line {line_number}: invalid JSON") from exc
            count += 1
    return count
```

Create `labs/01-reliable-ingestion/fixtures/day28.jsonl` with `{"trade_id":"T1","private_note":"keep-out-of-logs"}` and `{"trade_id":"T2"}` on separate lines. For the failure case, replace line 2 with `{bad json`. Pass this path after the script name.

Run from the repository root with `python src/trade_ingestion/day28.py`.

### Acceptance Criteria

- [ ] The valid run logs start, processed count 2 and completion, then exits 0.
- [ ] The malformed run logs a line 2 error, exits 1 and never logs successful completion.
- [ ] Neither full records nor keep-out-of-logs appear in logs.

### Hint

Search for "Python logging basicConfig exception exit status".

## Day 29: Write transformed trade results

[GitHub issue #29](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/29)

### Goal

Build a standalone file-to-file ETL command.

### Context

ETL reads, changes and saves data. Decimal and datetime need explicit JSON representations; a partial output file is not a successful result.

### Task

Create `src/trade_ingestion/day29.py` and any missing folders. Accept required `--input` and `--output` paths. Read JSONL one line at a time. Require the five fields shown below, finite positive Decimal quantities/prices and an offset-bearing timestamp. Write each ID, currency, calculated `notional` as decimal text, and timestamp with its offset. Open the output exclusively so existing files are refused. Reject input/output paths resolving to the same file before writing.

Create `labs/01-reliable-ingestion/fixtures/day29.jsonl` with these two lines:

```jsonl
{"trade_id":"T1","quantity":"3","price":"10","currency":"USD","timestamp":"2026-09-20T04:30:00+00:00"}
{"trade_id":"T2","quantity":"2","price":"5","currency":"INR","timestamp":"2026-09-20T10:00:00+05:30"}
```

Run with `--input labs/01-reliable-ingestion/fixtures/day29.jsonl --output work/day29-result.jsonl`; create the work folder first. On failure, stop, exit nonzero and report the line/reason and any partial output path. Use a fresh output path for each experiment.

Run from the repository root with `python src/trade_ingestion/day29.py`.

### Acceptance Criteria

- [ ] Valid input creates two parseable records with IDs T1/T2 and notional strings "30"/"10"; timestamp offsets are preserved.
- [ ] An existing output or the input path as output is refused without changing its bytes.
- [ ] With line 2 quantity "0", the command fails after line 1, identifies line 2 and clearly reports any partial output.
- [ ] Files close on success and failure; successful runs exit 0.

### Hint

Search for "Python json Decimal datetime context manager exclusive file mode x".

## Day 30: Add a currency rule and regression test

[GitHub issue #30](https://github.com/Prem-Tomar/production-data-ai-engineering/issues/30)

### Goal

Fix an unsupported currency being accepted by a small ETL program.

### Context

An allow-list names accepted values. A regression test reproduces a defect and guards its repair. This standalone starter assumes valid quantities and timestamps; it is not the production implementation.

### Task

Create `src/trade_ingestion/day30.py` with this starter:

```python
import json
from decimal import Decimal

def normalize_currency(raw):
    return raw.strip().upper()

def transform(raw):
    return {
        "trade_id": raw["trade_id"],
        "currency": normalize_currency(raw["currency"]),
        "notional": str(Decimal(raw["quantity"]) * Decimal(raw["price"])),
        "timestamp": raw["timestamp"],
    }

def run(input_path, output_path):
    with open(input_path, encoding="utf-8") as source:
        with open(output_path, "x", encoding="utf-8") as destination:
            for line in source:
                destination.write(json.dumps(transform(json.loads(line))) + "\n")

if __name__ == "__main__":
    import argparse
    parser = argparse.ArgumentParser()
    parser.add_argument("--input", required=True)
    parser.add_argument("--output", required=True)
    args = parser.parse_args()
    run(args.input, args.output)
```

Create `tests/test_day30.py`, importing normalize_currency and run from `src.trade_ingestion.day30`. First write a check that XYZ raises ValueError and run it against the starter. Then update normalization to accept only INR, USD and EUR after trimming and uppercasing. Add checks for those values and `" usd "`, plus a file-to-file check using pytest's tmp_path.

Create `labs/01-reliable-ingestion/fixtures/day30.jsonl` with these two lines:

```jsonl
{"trade_id":"T1","quantity":"3","price":"10","currency":"USD","timestamp":"2026-09-20T04:30:00+00:00"}
{"trade_id":"T2","quantity":"2","price":"5","currency":"INR","timestamp":"2026-09-20T10:00:00+05:30"}
```

Install pytest with `python -m pip install pytest`; run `python -m pytest tests/test_day30.py`. Run the command with the fixture as `--input` and a fresh `work/day30-result.jsonl` as `--output`, creating work first.

### Acceptance Criteria

- [ ] The XYZ regression check fails on the starter and passes after the fix.
- [ ] INR, USD and EUR are accepted; " usd " becomes USD; XYZ raises ValueError.
- [ ] All task tests pass; the two-trade fixture writes two records with amounts "30" and "10" to a new output file.

### Hint

Search for "pytest raises tmp_path regression test Python set membership".
