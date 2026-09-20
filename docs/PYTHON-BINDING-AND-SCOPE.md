# Coaching lab: name binding, scope and late binding

Teach in stages: assignment in the first week; function scope on Day 12; shared state on Day 13; closures on Day 23. Revisit the model in decorators, asynchronous callbacks and library design later. The examples below are teaching probes, not the solution to the ETL assignment.

## What “bind on write” means here

Use precise language: **assignment binds or rebinds a name; mutation changes an object**. It does not imply copying. Reading a name finds its binding; ordinary function-local classification considers assignments throughout that function. This explains why a later assignment can affect an earlier read. See the [Python execution model](https://docs.python.org/3/reference/executionmodel.html).

Global names belong to a module, not one universal namespace shared by all modules. `global` directs rebinding to that module; `nonlocal` refers to an existing binding in an enclosing function. Reading an outer binding is different from assigning to it. Coach the distinction before recommending either declaration. Prefer explicit arguments and returned results for ordinary pipeline helpers. See the [global and nonlocal statement reference](https://docs.python.org/3/reference/simple_stmts.html#the-global-statement).

## Run, change and fix

The coach gives a short demonstration, then the learner runs each probe and changes it. Brief discussion helps locate the bug; written theory answers are not required. Finish each probe with a concrete working variation.

### Probe A — reading before a local assignment

```python
limit = 5

def inspect_limit():
    print(limit)
    limit = 9
```

Call the function and reproduce UnboundLocalError. Repair it using an explicit parameter, then run it with limits 5 and 10 and check that it uses each supplied value without changing the module's limit. Run a deliberately global variant with the coach to observe the different state change; keep explicit inputs in the project helper.

### Probe B — mutation versus rebinding

```python
events = ["A"]
alias = events
alias.append("B")
alias = ["C"]
```

Run the example: events must contain A and B, while alias contains only C. Change it so a helper receives the list and appends an item, then inspect the caller's list. Assignment itself is not a copy-on-write mechanism. Study dataframe copy-on-write behavior separately for the selected library/version.

### Probe C — when a closure reads a value

```python
def build_rules():
    rules = []
    for limit in (5, 10):
        rules.append(lambda quantity: quantity <= limit)
    return rules
```

Run both returned rules with quantity 7 after construction: observe that both accept it. Repair the capture so the limit-5 rule rejects 7 and the limit-10 rule accepts it. Also try 3 and 12, which must be accepted by both and rejected by both respectively. Explore a function factory or definition-time default with a hint rather than a complete supplied fix. The [Python programming FAQ](https://docs.python.org/3/faq/programming.html#why-do-lambdas-defined-in-a-loop-with-different-values-all-return-the-same-result) explains this behavior.

### Probe D — state in an enclosing function

Have the coach supply a tiny counter factory. Run a version that fails to update its enclosing count, then repair it with deliberate `nonlocal` rebinding. One counter must return 1 then 2; a separately created counter must begin at 1. Try an explicit input/return version as a second small variation.

### Probe E — defaults are evaluated once per definition

Call a helper with a mutable default list twice, adding T1 then T2. Reproduce the unintended accumulated result, then repair initialization: the first default call must return only T1 and the second only T2. Try a captured mutable configuration object separately and observe the effect of changing its contents. See the [FAQ on shared default values](https://docs.python.org/3/faq/programming.html#why-are-default-values-shared-between-objects).

## Project and interview checks

- Day 12: a transformation receives configuration explicitly and does not accidentally rebind module state.
- Day 13: independent calls do not share a mutable default collection unintentionally.
- Day 23: two generated predicates retain distinct intended limits after the construction loop completes.
- Day 30: the coach changes a scope or captured value; the learner predicts, diagnoses and repairs the behavior independently.
- Later: repeat the exercise for retry callbacks, task scheduling and decorators, where execution can occur after surrounding state changes.

Use the failed and repaired runs to discuss which binding changed. Daily completion depends on working variations rather than reciting scope rules. Keep version-specific annotation and class-scope behavior for the advanced runtime phase; ordinary LEGB reasoning is a starting model, not every special scope rule.
