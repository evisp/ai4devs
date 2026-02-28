# Prompt Pattern Library (AI-Assisted Development)

Prompting is a development skill: you design inputs, constraints, and checks to reliably get useful output.

!!! note
    In this project you’ll use an AI assistant as a partner, but you are responsible for correctness.
    Treat suggestions as ideas to test, not answers to accept.

## Learning Objectives

By the end of this project, you will be able to:

- Identify recurring use cases for AI-assisted development.
- Design reusable prompt templates with placeholders for inputs and outputs.
- Test prompts against sample code or documentation tasks.
- Document a categorized library of prompt patterns.
- Reflect on how prompt structure influences AI-generated results.

## How to use this page (workflow)

Use this page like a toolbox, not like a textbook.

1. Pick a prompt pattern that matches your task (build, decide, or verify).
2. Fill in the placeholders with your context (code, constraints, expected output).
3. Run a quick validation: test cases, edge cases, and a “does this actually solve my task?” check.
4. Log the result in your prompt library so you can reuse it later.

!!! tip
    Copy the prompt first, then fill placeholders one by one.
    If you start “freestyling”, you usually forget constraints and expected outputs.

!!! warning
    Never paste secrets (API keys, passwords, private tokens) into prompts.
    If you need to share config, redact sensitive values.

## Concepts you need (light, practical)

These concepts make prompts reusable and testable:

- Placeholders: `[LIKE_THIS]` marks what you must provide each time.
- Inputs vs outputs: clearly separate “what I give you” from “what I want back”.
- Constraints: define boundaries (style, length, performance, allowed changes).
- Examples: show the format you want when output shape matters.
- Validation: define how you will check correctness before you accept the output.

### A reusable “prompt shell” (baseline)

Use this when you’re not sure which pattern to start with.

!!! tip
    Fill **Validation** before you send the prompt.
    If you can’t explain how you’ll test the answer, you’re not ready to trust it.

```text
Context:
- Project: (1 sentence: what is this repo/app?)
- Audience: (who will use/read this?)
- Language/runtime/tooling: (Python 3.11, Node 20, React, Docker, etc.)
- Constraints: (do not change signature, no new deps, must be O(n), style rules)
- What I already tried: (1–3 bullets; include errors/output if relevant)

Task:
- Objective: (one clear goal; “Implement X” / “Fix Y” / “Document Z”)
- Definition of done: (what must be true for this to be finished?)

Inputs:
- Source material: (paste code/spec/docs; include minimal reproduction if bug)
- Expected output format: (patch, markdown section, JSON schema, test list, etc.)

Validation:
- How I will test: (exact command(s) or steps; include expected signals)
- Required test cases: (normal + regression)
- Edge cases to include: (empty, boundary values, large input, error paths)
- Risks to watch: (what could this change break?)
```


## Prompt library (copy/paste)

Choose a group based on what you need *right now*—shipping output, making a decision, or proving correctness.

- Build: Produce a first usable draft (code, docs, tests) with clear format + constraints.
- Decide: Explore options and trade-offs (cost, complexity, performance, security) and pick a direction you can justify.
- Verify & improve: Turn “looks right” into “is right” with validation criteria, edge cases, and iterative refinement.



### Group 1 — Build (produce outputs)

Use these prompts when your goal is to **create** something: a first draft of code, documentation, tests, or a patch.  
They work best when you provide concrete inputs (snippet/spec) and tight constraints (format, length, “must include/must avoid”) so the output is immediately usable and easy to review.


=== "Role-based (build with expertise)"
    **Use when:** you want the assistant to adopt a specific professional lens (DevOps, backend, security, data).

    ```text
    Act as a [SPECIFIC ROLE] with [X years] of experience in [DOMAIN].

    You specialize in [SPECIFIC EXPERTISE] and have worked on [RELEVANT SYSTEMS/PROJECTS].

    Context:
    - Project: [PROJECT NAME + 1 sentence]
    - Environment: [LANGUAGE/RUNTIME/FRAMEWORK/VERSIONS]
    - Constraints: [DO NOT CHANGE SIGNATURE / MUST BE O(N) / NO NEW DEPS / ETC.]

    Task:
    - Objective: [SPECIFIC OBJECTIVE]
    - Deliverable: [PATCH / FILE / PLAN / COMMANDS]

    Consider:
    - Key factors: [SECURITY, COST, PERFORMANCE, MAINTAINABILITY]
    - Assumptions: [LIST 2–4]

    Output format:
    - Section 1: Proposed solution
    - Section 2: Risks / edge cases
    - Section 3: Verification steps (tests/commands)
    ```

=== "Constraint-based (controlled generation)"
    **Use when:** you need tight control (style, length, allowed changes, compliance).

    ```text
    Generate [OUTPUT TYPE] with the following constraints:

    REQUIREMENTS:
    - Must include: [MANDATORY ELEMENTS]
    - Must avoid: [FORBIDDEN ELEMENTS]
    - Format: [SPECIFIC FORMAT]
    - Length: [SIZE CONSTRAINTS]
    - Style: [TONE/APPROACH]

    INPUT:
    [PASTE CODE/SPEC/TASK]

    VALIDATION CRITERIA (you must self-check before finalizing):
    - [CRITERION 1]
    - [CRITERION 2]
    - [CRITERION 3]

    OUTPUT:
    [GENERATED CONTENT HERE]
    ```

=== "Few-shot (match my format)"
    **Use when:** the output shape matters (API docs, tickets, commit messages, test cases).

    ```text
    Here are examples of [TASK TYPE] that demonstrate the expected format and quality:

    Example 1:
    Input: [EXAMPLE INPUT 1]
    Output:
    [EXAMPLE OUTPUT 1]

    Example 2:
    Input: [EXAMPLE INPUT 2]
    Output:
    [EXAMPLE OUTPUT 2]

    Now apply the same approach to:
    Input: [ACTUAL INPUT]
    Output: [GENERATE IN THE SAME FORMAT]
    ```

### Group 2 — Decide (design and trade-offs)

Use these prompts when you’re not writing code yet, you’re choosing *what to build* and *why*.  
They help you compare options, make assumptions explicit, and evaluate trade-offs (performance, cost, complexity, security, UX) so your final decision is defensible and aligned with constraints.

=== "Multi-perspective (balanced analysis)"
    **Use when:** you need a decision that holds up technically and practically.

    ```text
    Analyze [PROBLEM/DECISION] from multiple perspectives:

    Context:
    - System: [WHAT YOU’RE BUILDING]
    - Constraints: [TIME/BUDGET/STACK/TEAM SKILLS]
    - Success metrics: [LATENCY, COST, RELIABILITY, UX, ETC.]

    Technical perspective:
    - Options:
    - Trade-offs:
    - Complexity:
    - Performance considerations:

    Business perspective:
    - Cost impact:
    - Delivery timeline impact:
    - Operational overhead:

    User perspective:
    - UX implications:
    - Failure modes visible to users:
    - Accessibility/clarity:

    Security perspective:
    - Threats:
    - Data handling:
    - Abuse/rate limiting:

    Synthesis:
    - Recommendation:
    - Why this is best for the given constraints (brief justification):
    - What I should validate next (2–5 checks/tests)
    ```

=== "Scenario-based (normal/edge/failure)"
    **Use when:** you want a solution that handles real-world cases, not just the happy path.

    ```text
    Consider these scenarios for [SYSTEM/FEATURE]:

    Scenario 1: Normal case
    - Conditions:
    - Expected behavior:
    - Implementation approach:

    Scenario 2: Edge case
    - Conditions:
    - Expected behavior:
    - Implementation approach:

    Scenario 3: Failure case
    - Conditions:
    - Expected behavior (including error messages/status codes):
    - Implementation approach (fallbacks, retries, timeouts):

    Comprehensive solution:
    - Unified approach that covers all scenarios:
    - Assumptions:
    - Tests to verify (include one regression test):
    ```

=== "What-if (compare alternatives)"
    **Use when:** you have an existing approach but want to explore better options safely.

    ```text
    Current approach:
    [DESCRIBE WHAT WE DO TODAY]

    What if we [ALTERNATIVE 1]?
    - Benefits:
    - Drawbacks:
    - Implementation sketch:
    - Risks:

    What if we [ALTERNATIVE 2]?
    - Benefits:
    - Drawbacks:
    - Implementation sketch:
    - Risks:

    Comparison (side-by-side):
    - Criteria: [COST, LATENCY, MAINTAINABILITY, SECURITY, DELIVERY TIME]
    - Winner per criterion:

    Recommendation:
    - Choose:
    - Rationale (brief, evidence-driven):
    - Next validation steps:
    ```

### Group 3 — Verify & improve (correctness first)

Use these prompts after you have a draft (yours or the AI’s) and need to **prove it works**.  

They force explicit validation criteria, generate edge cases and regression tests, and guide small, evidence-based iterations so you improve quality without accidental rewrites.


=== "Validation (quality gate)"
    **Use when:** you already have an output and want to check it before merging/shipping.

    ```text
    Validate the following [CODE/DOC/PLAN] against these criteria.

    INPUT:
    [PASTE CONTENT]

    CORRECTNESS:
    - Must satisfy: [FUNCTIONAL REQUIREMENTS]
    - Must not break: [KNOWN CONSTRAINTS]

    COMPLETENESS:
    - Must include: [REQUIRED SECTIONS/CASES]
    - Must handle: [EDGE CASES LIST]

    QUALITY:
    - Must follow: [STYLE GUIDE / BEST PRACTICES]
    - Must be readable and minimal

    USABILITY:
    - For a developer: [HOW TO RUN/TEST]
    - For a user: [EXPECTED BEHAVIOR + ERROR MESSAGES]

    Output format:
    1) Pass/fail per category (with evidence)
    2) Issues found (bulleted, actionable)
    3) Minimal fix suggestions
    4) Tests to verify (2–5)
    ```

=== "Iterative refinement (improve safely)"
    **Use when:** the first answer is close but not good enough, and you want a controlled loop.

    ```text
    Initial solution:
    [PASTE FIRST ATTEMPT]

    Review criteria:
    1. [EVALUATION METRIC 1]
    2. [EVALUATION METRIC 2]
    3. [EVALUATION METRIC 3]

    Analysis:
    - Identify weaknesses and what caused them (brief).
    - Identify the smallest change that improves the outcome.

    Improved solution:
    [REFINED VERSION]

    Final validation:
    - Show how the improved solution meets each review criterion.
    - Provide tests/commands/checks to verify.
    ```

=== "Context-aware (stay consistent)"
    **Use when:** the project spans multiple files/decisions and the assistant keeps forgetting constraints.

    ```text
    Context summary:
    - Project: [PROJECT DESCRIPTION]
    - Current state: [WHAT EXISTS TODAY]
    - Previous decisions: [KEY CHOICES MADE]
    - Constraints: [LIMITATIONS]
    - Goals: [OBJECTIVES]

    Current request:
    [SPECIFIC TASK]

    Consistency checks (must consider):
    - How does this fit previous decisions?
    - What impact on constraints?
    - How does this advance the goals?

    Response format:
    - Proposed solution
    - Compatibility notes (what stays the same)
    - Risks + edge cases
    - Verification plan (tests/checks)
    ```

!!! tip
    When a prompt “doesn’t work”, don’t immediately change the whole prompt.
    Change one variable: add an example, tighten one constraint, or clarify the expected output.

## Testing and documenting your prompts

### Prompt testing ladder

1. One direct check: run the smallest example input and see if the output format is correct.
2. Add 2-5 tests: normal case + edge cases (empty input, single element, boundary values).
3. Regression check: the original problem case must pass after changes.
4. Safety check: ensure you didn’t break obvious constraints (signature, complexity, style, forbidden changes).

### Prompt library entry template (copy/paste)

Use one entry per pattern you tested:

```text
## Pattern: <name>
Category: Build | Decide | Verify
Use case: <when I used it>
Task: <what I was trying to do>

Prompt (template):
<paste the prompt with placeholders>

Filled example:
- Inputs:
- Constraints:
- Expected output format:

Result:
- What the AI produced:
- What was correct:
- What was wrong:

Verification:
- Tests/commands run:
- Evidence (output/logs):

Refinement:
- Change I made to the prompt:
- Why it improved (or didn’t):

Lesson learned (one line):
<what I will do next time>
```

!!! warning
    Your “best prompt” is the one that keeps working across different inputs.
    If it only works once, you found a lucky guess, not a reusable pattern.