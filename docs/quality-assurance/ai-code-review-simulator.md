# AI Code Review Simulator

![Motivation](https://i.imgur.com/dxJFAKG.png)

Code that works is not the same as code that's ready for production.  
The gap between the two is what code review exists to close—and learning to navigate that gap, with or without a human reviewer, is one of the most valuable skills you can build.

!!! note
    AI can simulate reviewer feedback instantly and from multiple perspectives, but you are the one who decides what to accept, what to reject, and why. This page gives you the workflow, prompts, and judgment framework to do that like a senior engineer.

## Why code review skills matter

- **Ship safer, stronger code**: Catch logic gaps, security flaws, and performance issues before they reach users
- **Learn faster than any tutorial**: Every review—human or AI—is a mirror that shows you exactly where your thinking has gaps
- **Build team trust**: Developers who give and receive feedback well are the ones teams want on critical projects
- **Own your decisions**: Knowing *why* you accept or reject a suggestion matters more than the suggestion itself
- **Close the AI judgment gap**: Use AI feedback as a starting point, not a verdict—the skill is in the evaluation


## What a great code review actually does

![3 Pillars](https://i.imgur.com/c9yMbAW.png)

### 1. **Catches what tests miss**
Tests verify behavior—reviews verify intent, structure, and risk.

- Spots security vulnerabilities that pass all unit tests
- Identifies design decisions that will cause pain six months from now
- Surfaces assumptions the author didn't know they were making

### 2. **Transfers knowledge**
A good review teaches both parties something.

- Reviewer learns the codebase; author learns better patterns
- Inline comments become permanent documentation
- Standards spread organically across the team

### 3. **Raises the bar over time**
Every review is an investment in future code quality.

- Consistent feedback builds shared coding instincts across the team
- Patterns caught in review stop appearing in new code
- The team gets faster and more confident with every cycle


## Your 4-step review simulation workflow

![4 Step Workflow](https://i.imgur.com/KAsj9Yi.png)

1. **Write** a meaningful pull request  
   Implement a real feature with a clear purpose → include context, user story, and acceptance criteria so the review has something to work with

2. **Review** with AI  
   Run role-based and scenario prompts → collect inline feedback, global observations, and suggested changes across multiple reviewer perspectives

3. **Decide** on every suggestion  
   Accept, reject, or modify each piece of feedback → document your justification so your reasoning is explicit and defensible

4. **Reflect** on the review quality  
   Compare AI feedback against what a human reviewer would likely catch → identify what the AI missed, what it got right, and what it overcalled

!!! tip
    At each step, ask: "Do I understand *why* this feedback matters—or am I just accepting it because an AI said so?"


## Prompt patterns 

These ready-to-use prompts follow the 4-step process above.  
Pick the group for your current task, copy a prompt, fill in your project details, and run it.  
Each one produces structured feedback you can evaluate, apply, and learn from.

### Group 1 – Role-Based Reviews

Start here to get feedback from distinct professional perspectives.  
Each prompt puts AI in a specific reviewer role so you get targeted, non-generic feedback rather than a generic list of suggestions.

=== "Security review"
    **Use when:** reviewing any code that handles authentication, user data, external input, or system access.

    ```text
    Act as a senior security-focused developer reviewing this code for a production deployment.

    Code Submission:
    ```[LANGUAGE]
    [CODE_TO_REVIEW]
    ```

    Context:
    - Application Type: [WEB_APP/API/MOBILE/DESKTOP]
    - Security Requirements: [COMPLIANCE_STANDARDS]
    - User Data Sensitivity: [HIGH/MEDIUM/LOW]
    - Deployment Environment: [CLOUD/ON_PREMISE/HYBRID]

    Focus your review on:
    - Security Vulnerabilities: SQL injection, XSS, CSRF, authentication flaws
    - Data Protection: PII handling, encryption, secure transmission
    - Input Validation: Sanitization and validation of user inputs
    - Authentication & Authorization: Access control and session management
    - Dependency Security: Third-party library vulnerabilities

    Provide specific security recommendations with code examples for each fix.
    ```

=== "Performance review"
    **Use when:** reviewing code that operates under load, handles large data sets, or has response time requirements.

    ```text
    Review this code from a performance and scalability perspective as a senior software architect.

    Code Under Review:
    ```[LANGUAGE]
    [PERFORMANCE_CRITICAL_CODE]
    ```

    Performance Context:
    - Expected Load: [CONCURRENT_USERS/REQUESTS_PER_SECOND]
    - Performance SLAs: [RESPONSE_TIME_REQUIREMENTS]
    - Scalability Requirements: [HORIZONTAL/VERTICAL_SCALING]
    - Resource Constraints: [MEMORY/CPU/STORAGE_LIMITS]

    Analyze for:
    - Algorithm Efficiency: Time and space complexity analysis
    - Database Performance: Query optimization and N+1 problems
    - Memory Management: Memory leaks and garbage collection impact
    - Caching Strategy: Opportunities for performance improvement
    - Async/Concurrency: Proper use of asynchronous patterns

    Suggest performance optimizations with benchmark expectations for each.
    ```

=== "Code quality review"
    **Use when:** reviewing any feature addition or refactor where maintainability, readability, and team standards matter.

    ```text
    Conduct a thorough code quality review focusing on maintainability and team collaboration.

    Code Submission:
    ```[LANGUAGE]
    [CODE_FOR_QUALITY_REVIEW]
    ```

    Team Context:
    - Team Size: [NUMBER] developers
    - Experience Level: [JUNIOR/MIXED/SENIOR]
    - Codebase Size: [SMALL/MEDIUM/LARGE]
    - Maintenance Timeline: [SHORT_TERM/LONG_TERM]

    Evaluate:
    - Code Readability: Naming conventions, structure, and clarity
    - Design Patterns: Appropriate use of patterns and principles
    - Documentation: Code comments, API docs, README coverage
    - Testability: Unit test coverage and test quality
    - SOLID Principles: Single responsibility, open/closed, etc.

    Provide refactoring suggestions with improved code examples for each finding.
    ```

### Group 2 – Scenario Reviews

Use these once you have general feedback and want to go deeper on specific situations.  
These prompts simulate real PR scenarios—the kind you'll encounter in professional teams every week.

=== "Feature addition"
    **Use when:** reviewing a new feature implementation against its original requirements and acceptance criteria.

    ```text
    Review this new feature implementation for completeness, quality, and integration.

    Feature Requirements:
    - Feature Description: [WHAT_THE_FEATURE_DOES]
    - User Stories: [USER_STORY_LIST]
    - Acceptance Criteria: [COMPLETION_CRITERIA]
    - Non-functional Requirements: [PERFORMANCE/SECURITY/etc.]

    Feature Implementation:
    ```[LANGUAGE]
    [FEATURE_CODE]
    ```

    Assess:
    - Requirements Fulfillment: Does the implementation meet all requirements?
    - Integration Quality: How well does it integrate with existing code?
    - Error Handling: Are error scenarios properly handled?
    - Performance Impact: Does the feature affect system performance?
    - Future Extensibility: Is the feature designed for future enhancement?

    Evaluate feature completeness and suggest specific improvements with code examples.
    ```

=== "Bug fix review"
    **Use when:** validating that a fix addresses the root cause without introducing regressions.

    ```text
    Review this bug fix to ensure it properly addresses the issue without introducing regressions.

    Original Bug Report:
    - Issue: [BUG_DESCRIPTION]
    - Severity: [HIGH/MEDIUM/LOW]
    - Affected Users: [USER_IMPACT]
    - Reproduction Steps: [HOW_TO_REPRODUCE]

    Bug Fix Implementation:
    ```[LANGUAGE]
    [BUG_FIX_CODE]
    ```

    Verify:
    - Root Cause Resolution: Does the fix address the actual root cause?
    - Scope of Changes: Are changes minimal and focused?
    - Edge Cases: Does the fix handle all edge cases?
    - Regression Risk: Could this fix break existing functionality?
    - Testing Coverage: Are there sufficient tests to confirm the fix?

    Assess the fix quality and suggest additional safeguards where needed.
    ```

=== "Multi-reviewer simulation"
    **Use when:** simulating a realistic team review discussion to compare perspectives and practice responding to varied feedback.

    ```text
    Simulate a code review discussion between multiple team members with different perspectives.

    Code Under Review:
    ```[LANGUAGE]
    [COMPLEX_CODE_SAMPLE]
    ```

    Review Participants:
    - Junior Developer: Focus on understanding and learning
    - Senior Developer: Focus on best practices and mentoring
    - Tech Lead: Focus on architecture and technical direction
    - Product Owner: Focus on business requirements fulfillment

    For each reviewer, provide:
    - Initial Feedback: First impression and immediate concerns
    - Detailed Comments: Specific line-level observations with explanations
    - Questions: Areas needing clarification before approving
    - Suggestions: Concrete improvement recommendations
    - Approval Status: Ready to merge / needs changes / requires discussion

    After all four reviews, simulate the team discussion:
    - Where do reviewers agree?
    - Where do they disagree, and why?
    - What is the consensus recommendation?
    - What is the final action plan before merging?
    ```


## Do's and Don'ts

Rules that separate developers who grow from reviews from ones who just click "resolve" and move on.  
Follow these and every review cycle—human or AI—makes you a stronger engineer.  
Break them and you'll ship AI-approved code you don't actually understand.

!!! tip "Do's"
    - Read AI feedback critically—treat it as a perspective, not a verdict
    - Document your justification every time you accept or reject a suggestion
    - Use role-based prompts to get targeted feedback, not just generic notes
    - Compare AI output against what you'd expect from a human teammate
    - Run multiple review types on the same code to surface different blind spots
    - Use the multi-reviewer simulation to practice handling disagreement

!!! warning "Don'ts"
    - Accept suggestions you can't explain to a teammate
    - Use AI review as a substitute for understanding your own code
    - Run only one review type and assume you've covered everything
    - Ignore suggestions just because they require significant changes
    - Forget that AI reviewers have no knowledge of your team's conventions or business context
    - Submit AI feedback directly as your own review without critical evaluation


## 60-second PR review checklist

| Pillar | Check | Pass? |
|--------|-------|-------|
| **Correctness** | Does the code do what the requirements say? | ☐ |
| **Security** | Are inputs validated, data protected, access controlled? | ☐ |
| **Performance** | No obvious bottlenecks, leaks, or inefficient patterns? | ☐ |
| **Readability** | Can a teammate understand this without asking questions? | ☐ |
| **Error handling** | Are failure scenarios explicitly handled? | ☐ |
| **Test coverage** | Does every acceptance criterion have a test? | ☐ |


## Quick review ladder

Work through these in order—stop when you have enough confidence to approve or request changes:

1. **One pass**: Run the code quality review prompt and skim for structural and readability issues first
2. **Role check**: Apply the security or performance prompt depending on what the PR touches
3. **Scenario match**: Pick the feature, bug fix, or multi-reviewer prompt that fits the PR type
4. **Reflection**: Write two sentences—what did AI catch that you missed, and what did it miss that you caught?

!!! tip
    The goal is not a perfect review—it is a defensible one. Know why every comment is there, and know why every suggestion was accepted or rejected.

> "Approving code you don't understand is just moving the problem downstream."
