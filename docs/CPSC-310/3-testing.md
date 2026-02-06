# Testing

## Ethics
- Protect individuals affected by software behavior
- Ensure fairness (bias, discrimination)
- Integrity and trust in testing outcomes

## Static analysis

Any analysis on the actual code (instead of running the code); dynamic analysis needs to run the code

- Semantics and syntax
- Formatting (prettier)
- Linting (eslint): no unused vars, globals, misused promises

Linters can also help with variable naming and inefficient code

Try to catch bugs early, first in the compiler stage

## Testing

### Kinds of tests by scope

- Unit: behavior of single unit
    - fast and targetted
- Integration: how parts of the system work together
    - slower and broader
- End-to-end: how the entire app works
    - even slower and broader

Flaky tests: pass/fail randomly; will happen as scope grows  

### Kinds of test by purpose (test suites)

- Smoke: testing on core, critical functionality
    - viable for further testing?
    - very quick
- Regression: test previously working functionality after changes
    - ensure existing behavior (did we break something)
    - slower
- Acceptance: tests functional requirements, user stories
    - validate expectations
    - run before release, very slow

### Parts of a test

- Setup
- Meaningful name
- Execution
    - Code under test (CUT) or system under test (SUT)
- Validation
- Teardown

### Blackbox testing

- focuses on external behavior
- not looking at the code
- uses specifications, requirements
- challenge: input space
    - need for systematic test design

#### Equivalence class partitioning
- by specification or required behavior
    - partition possible inputs into equivalence classes
    - test one input from each class
- input/output partitioning
    - input: numeric ranges
    - output: return values, UI response, error message
    - may produce same test cases, but different reasoning paths

#### Boundary value analysis
- at, just below, and just above boundaries

### Glass box testing

#### Coverage: how much code did the tests execute

- Line coverage
- Statement coverage
- Branch coverage

### Mutation testing

- run the test suite and make sure tests pass
- "mutate" the implementation
    - changing operations like `+, -, *, /, &&, ||, >, <`
- tests should fail, "catching" mutation