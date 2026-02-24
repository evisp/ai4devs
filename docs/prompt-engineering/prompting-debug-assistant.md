# Prompting Debug Assistant

Debugging is not guessing. It is a **method**: reproduce the problem, form a theory, change one thing, and verify with evidence.

!!! note
    In this project you’ll use an AI assistant as a partner, but you are responsible for correctness.
    Treat suggestions as ideas to test, not answers to accept. 


## What you should learn

By the end of this project, you should be able to:

- Describe a bug clearly (expected vs actual, steps to reproduce, and evidence). 
- Reduce a problem to a minimal reproducible example (MRE) so it becomes easier to solve. 
- Use an AI assistant to propose likely causes and candidate fixes, then verify them with tests. 
- Explain the root cause in plain language and document the fix so someone else can trust it.


## The mental model: debugging is experiments

![Overall](https://i.imgur.com/J2cT5Pd.jpeg)

A good debugging session looks like a series of small experiments:

1. **Reproduce** the problem reliably.
2. **Observe** what is happening (error message, output, state).
3. **Hypothesize** a cause (one clear theory).
4. **Test** the theory with a small change or a focused check.
5. **Fix** and then **verify** with tests and edge cases.
6. **Document** what happened and what you learned.

!!! tip
    Make one change at a time.
    If you change three things at once, you won’t know which change mattered.

## Reproduce → Reduce → Explain

These three habits will make you faster than any tool.

### 1) Reproduce (make it stable)
Before you ask for help (human or AI), get a reliable reproduction:

- Same inputs produce the same failure.
- You can explain how to run it (command, file, function call).
- You capture the *exact* error text or unexpected output. 

!!! warning
    “It doesn’t work” is not a bug description.
    Always include the error message or a concrete “actual output” statement. 

### 2) Reduce (build an MRE)
An MRE is: **Minimal, Complete, Reproducible**. 

- Minimal: keep only the code that still fails.
- Complete: include everything needed to run it (imports, data, config).
- Reproducible: you ran it and confirmed it fails exactly as described. 

Reducing is powerful because it removes noise. It also forces clarity: you discover what truly matters.

### 3) Explain (expected vs actual)
Always write both:

- **Expected**: what should happen and why you expect it.
- **Actual**: what happens instead (error message, wrong result, crash). 

This single habit improves AI responses and makes your bug reports actionable. 

## Using AI effectively (without over-trusting it)

AI is helpful when you give it good context and ask for structured output. Copilot’s debugging guidance emphasizes giving clear context and using it to generate tests and understand code, but pairing it with verification. 

### The “debugging packet” (what to paste)
When you ask the AI for help, include:

- The snippet (or the reduced snippet).
- Language + runtime/tool (Python 3.11, Node 20, gcc flags, etc.).
- How to run it (exact command).
- The full error / stack trace (copy text, not screenshots). 
- Expected behavior and actual behavior. 
- Any constraints (“don’t change function signature”, “must be O(n)”, etc.).

!!! tip
    If you’re using an IDE assistant, it may already see the file context.
    Still include “expected vs actual” and the exact reproduction steps—those are the pieces it can’t guess. 

### Ask for a structured answer
Instead of “fix this”, ask for:

- Root cause (what line, what rule, what assumption broke)
- Fix (minimal patch)
- Side effects (what could this break)
- Tests (2–5 tests, including edge cases) 

Use wording like:

> “Identify the root cause, propose the smallest fix, list risks/edge cases, and propose tests to verify.”

### Compare fixes, don’t collect fixes
If the AI gives multiple options, that’s normal. Your job is to choose based on evidence:

- Does it reproduce before and stop reproducing after?
- Does it pass edge cases?
- Is it minimal and understandable?

!!! warning
    If the AI proposes a large rewrite, pause.
    First ask for a minimal change that proves the root cause. Big rewrites hide mistakes.


## Verification is the product

A fix is real only when you can prove it.

### A simple validation ladder
Start small and climb only if needed:

1. **One direct check** (print/log, quick run, a single input).
2. **A small set of tests** (normal case + edge cases). 
3. **Regression check** (the original failing case must pass).
4. **Safety check** (did you break something else obvious?).

Copilot guidance explicitly calls out generating tests and using them to catch edge cases. 

### Edge cases you should actively try
Even for tiny snippets, try at least a few:

- Empty input (empty list/string, null/None)
- Single element
- Boundary values (0, 1, length-1, length)
- Negative values (if meaningful)
- Very large values (if loops or indexes exist)

!!! tip
    If you don’t know the edge cases, ask the AI: “List the edge cases for this function and explain why each matters.”
    Then verify them yourself. 


## Root cause: what it should sound like

“Root cause” is not “it crashed”. It’s the *reason* it crashed.

Good root cause statements usually include:

- The incorrect assumption (e.g., “n can equal len(items) but the slice subtracts one extra index”)
- The mechanism (e.g., “index goes out of range”, “operator precedence changes the expression”)
- The location (file + line or function)

!!! note
    Your bug report should help another developer understand the problem without re-reading the entire file.


## Writing strong bug reports (fast)

A good bug report reduces back-and-forth. It usually contains: steps to reproduce, expected vs actual, evidence, and environment. 

### A simple bug report structure
Use this structure for each bug:

- Summary (one sentence)
- Steps to reproduce (numbered)
- Expected result vs actual result 
- Root cause (what and why)
- Resolution (what changed and why)
- Evidence (tests run, logs, small diff)
- Lesson learned (one line)

!!! tip
    If someone can reproduce your bug in under 60 seconds from your report, it’s a great report. 


## Common failure modes (and fixes)

- Missing reproduction steps → AI (and humans) guess wrong. Fix: always include “how to run” + exact error. 
- Too much code → the real issue is buried. Fix: reduce to an MRE. 
- Fixing symptoms → bug comes back. Fix: write a root cause statement and test it.
- No edge cases → fix passes one input but fails others. Fix: add edge cases and a regression test. 
- Accepting a confident answer → incorrect patch. Fix: require tests and evidence. 


## Templates (with examples)

### Debugging packet (for your AI prompt)

=== "Generic"
    Copy, fill, and paste:

    ```text
    Language/runtime:
    How to run:
    Expected behavior:
    Actual behavior:
    Error/trace (full text):
    Constraints:

    Code:
    (paste here)
    ```

=== "Example (Python off-by-one)"
    ```text
    Language/runtime:
    Python 3.11

    How to run:
    python3 bug1.py

    Expected behavior:
    Return the last n items of a list.
    For items=[1,2,3,4,5], n=3 => [3,4,5]
    For n == len(items) => return the whole list

    Actual behavior:
    For n == len(items), it returns a shorter list than expected.

    Error/trace (full text):
    No exception. Wrong output.

    Constraints:
    Keep the same function signature.
    Prefer a minimal change.

    Code:
    def last_n(items, n):
        return items[len(items) - n - 1:]
    ```

### Mini template: AI debug log entry

=== "Generic"
    ```md
    ## Bug – <filename>

    **Prompt**:
    (paste your prompt)

    **AI diagnosis**:
    (what it claims is wrong)

    **Suggested fix**:
    (paste or summarize)

    **Risks / side effects**:
    (what could break)

    **Tests to verify**:
    - Test 1:
    - Test 2:
    - Edge case:

    **What I did**:
    (what you actually changed and why)

    **Result**:
    (pass/fail + evidence)
    ```

=== "Example (bug1.py)"
    ```md
    ## Bug – bug1.py

    **Prompt**:
    This function should return the last n items of a list.
    It gives wrong output when n == len(items).
    Identify the root cause, propose the smallest fix, and give tests (including edge cases).

    **AI diagnosis**:
    The slice start index subtracts one extra position: `len(items) - n - 1`.
    When `n == len(items)`, it starts at index `-1`, so it only returns the last element.

    **Suggested fix**:
    Change to:
    `return items[len(items) - n:]`

    **Risks / side effects**:
    If n can be negative, behavior should be defined (not handled here).
    If n > len(items), Python slicing is forgiving, but expected behavior should be clarified.

    **Tests to verify**:
    - items=[1,2,3,4,5], n=3 => [3,4,5]
    - items=[1,2,3,4,5], n=1 =>  [github](https://github.com/squidfunk/mkdocs-material/blob/master/docs/reference/content-tabs.md)
    - Edge case: items=[1,2,3], n=3 => [1,2,3]
    - Edge case: items=[], n=0 => []

    **What I did**:
    Applied the one-line change to the slice start index.

    **Result**:
    PASS — manual checks matched expected output (see fix_validation.md).
    ```

### Mini template: validation entry

=== "Generic"
    ```md
    ## <fixed filename>

    - Input:
    - Expected:
    - Actual:
    - Evidence: (command run, test output, screenshot/log link)
    ```

=== "Example (bug1_fixed.py)"
    ```md
    ## bug1_fixed.py

    - Input: items=[1,2,3,4,5], n=3
    - Expected: [3,4,5]
    - Actual: [3,4,5]
    - Evidence: `python3 bug1_fixed.py` (prints test outputs)

    - Input: items=[1,2,3], n=3
    - Expected: [1,2,3]
    - Actual: [1,2,3]
    - Evidence: Same run, edge-case check
    ```

### Mini template: bug report section

=== "Generic"
    ```md
    ## Bug Report – <filename>

    - **Summary**:
    - **Steps to reproduce**:
      1.
      2.
    - **Expected vs actual**:
    - **Root cause**:
    - **Resolution**:
    - **Evidence**:
    - **Lesson learned**:
    ```

=== "Example (bug1.py)"
    ```md
    ## Bug Report – bug1.py

    - **Summary**: Off-by-one error in slice start index returns incorrect results at the boundary.
    - **Steps to reproduce**:
      1. Run the function with `items=[1,2,3]` and `n=3`.
      2. Observe the returned value.
    - **Expected vs actual**:
      - Expected: `[1,2,3]`
      - Actual: `[3]`
    - **Root cause**: The code uses `len(items) - n - 1`, subtracting one extra index. When `n == len(items)`, start becomes `-1`, so slicing returns only the last element.
    - **Resolution**: Changed slice start to `len(items) - n` (minimal fix).
    - **Evidence**: Validation cases in `fix_validation.md` pass, including the `n == len(items)` boundary.
    - **Lesson learned**: Always test boundaries (0, 1, len-1, len) for indexing and slicing logic.
    ```



!!! tip
    Keep templates short.
    The goal is clarity and proof, not long writing.


