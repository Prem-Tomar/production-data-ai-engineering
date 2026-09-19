# Coaching lab: name binding, scope and late binding

Teach in stages: assignment in the first week; function scope on Day 12; shared state on Day 13; closures on Day 23. Revisit the model in decorators, asynchronous callbacks and library design later. The examples below are teaching probes, not the solution to the ETL assignment.

## What “bind on write” means here

Use precise language: **assignment binds or rebinds a name; mutation changes an object**. It does not imply copying. Reading a name finds its binding; ordinary function-local classification considers assignments throughout that function. This explains why a later assignment can affect an earlier read. See the [Python execution model](https://docs.python.org/3/reference/executionmodel.html).

Global names belong to a module, not one universal namespace shared by all modules. `global` directs rebinding to that module; `nonlocal` refers to an existing binding in an enclosing function. Reading an outer binding is different from assigning to it. Coach the distinction before recommending either declaration. Prefer explicit arguments and returned results for ordinary pipeline helpers. See the [global and nonlocal statement reference](https://docs.python.org/3/reference/simple_stmts.html#the-global-statement).

## Predict before running

The coach reveals results only after the learner predicts and explains them. When a prediction is wrong, shrink the example and rerun it before continuing.

### Probe A — reading before a local assignment

```python
limit = 5

def inspect_limit():
    print(limit)
    limit = 9
```

Predict what happens when called. Identify which name the function considers local and when it first receives a value. Repair the function by passing needed data explicitly. Then compare with a deliberately global variant in a scratch exercise, explaining the shared-state consequence rather than adopting globals as the default fix.

### Probe B — mutation versus rebinding

```python
events = ["A"]
alias = events
alias.append("B")
alias = ["C"]
```

Draw which names refer to which lists after each line. Explain why changing a list and rebinding a name are different operations. Repeat with a helper that receives the list as an argument. Assignment itself is not a copy-on-write mechanism. Study dataframe copy-on-write behavior separately for the selected library/version.

### Probe C — when a closure reads a value

```python
def build_rules():
    rules = []
    for limit in (5, 10):
        rules.append(lambda quantity: quantity <= limit)
    return rules
```

Predict the result of calling both returned rules with quantity 7 after construction has finished. Investigate a function factory and a definition-time default as alternative fixes; explain what each captures. Do not assume the issue is unique to lambda syntax. The [Python programming FAQ](https://docs.python.org/3/faq/programming.html#why-do-lambdas-defined-in-a-loop-with-different-values-all-return-the-same-result) explains this behavior.

### Probe D — state in an enclosing function

Have the coach supply a tiny counter factory. Compare reading its enclosing count, rebinding it without a declaration, and deliberately rebinding with `nonlocal`. Explain which state survives between calls and verify that two factory-created counters are independent. Then compare returning a new count to maintaining hidden state.

### Probe E — defaults are evaluated once per definition

Compare two calls to a helper with a mutable default list. Explain why results may depend on previous calls. Choose an explicit per-call initialization strategy. Also examine a default used to capture a mutable configuration object: capturing the reference is not an immutable snapshot of its contents. See the [FAQ on shared default values](https://docs.python.org/3/faq/programming.html#why-are-default-values-shared-between-objects).

## Project and interview checks

- Day 12: a transformation receives configuration explicitly and does not accidentally rebind module state.
- Day 13: independent calls do not share a mutable default collection unintentionally.
- Day 23: two generated predicates retain distinct intended limits after the construction loop completes.
- Day 30: the coach changes a scope or captured value; the learner predicts, diagnoses and repairs the behavior independently.
- Later: repeat the exercise for retry callbacks, task scheduling and decorators, where execution can occur after surrounding state changes.

Explain the binding and its timing before proposing a fix. Passing a memorized “lambda in a loop” question is insufficient if an unfamiliar nested-function variation still fails. Keep version-specific annotation and class-scope behavior for the advanced runtime phase; ordinary LEGB reasoning is a starting model, not every special scope rule.
