# Smart Bug Bounty

![Motivation](https://i.imgur.com/yulkNmq.png)

Every bug that reaches production costs ten times more to fix than one caught in review.  
The difference between a good developer and a great one is knowing how to hunt bugs systematically—before users find them for you.

!!! note
    AI can scan code and surface vulnerabilities fast, but you must validate every finding, reproduce it reliably, and judge its real impact. This page gives you the workflow, prompts, and checklist to do that right.

## Why bug hunting skills pay off

- **Catch issues before users do**: Find the bugs that break trust, corrupt data, or expose security gaps before they ever hit production
- **Write reports that get fixes shipped**: Structure findings so developers can reproduce, understand, and prioritize without back-and-forth
- **Build security instincts**: Learn to think like an attacker—and design code that holds up under pressure
- **Accelerate code quality**: Turn every audit into a learning opportunity that makes your whole codebase stronger
- **Stand out professionally**: Developers who find and document bugs clearly are the ones teams trust with critical systems


## What a professional bug report actually does

![3 Pillars](https://i.imgur.com/vnvW7tP.png)

### 1. **Locates precisely**
A good report points to exactly where the problem lives—no guessing required.

- Class, method, and line number—not just "somewhere in the auth module"
- Identifies the execution path that triggers the issue
- Links the bug to a specific feature, user story, or system behavior

### 2. **Reproduces reliably**
If a developer can't reproduce it, it doesn't get fixed.

- Step-by-step trigger scenario anyone can follow
- Includes environment, inputs, and preconditions
- Documents both expected and actual behavior with evidence

### 3. **Prioritizes clearly**
Not all bugs are equal—a good report makes triage instant.

- Severity rating (P0–P3) with justification, not just a gut feeling
- Business impact stated in plain terms: data loss, downtime, financial risk
- Estimated fix effort so teams can plan realistically


## Your 4-step bug bounty workflow

![4 Step Workflow](https://i.imgur.com/OQUCV40.png)

1. **Scan** the codebase  
   Run structured AI prompts → surface bugs by category (critical, major, minor) and flag security vulnerabilities

2. **Classify** by severity  
   Apply the P0–P3 impact framework → rank findings by business risk, not just technical complexity

3. **Reproduce** every finding  
   Write a step-by-step trigger scenario → confirm the bug is real, consistent, and scoped correctly

4. **Report** with precision  
   Produce a structured bug report → location, reproduction steps, impact, fix recommendation, and severity rating

!!! tip
    At each step, ask: "Can someone else act on this without asking me a single question?"


## Prompt patterns (match your workflow stage)

These ready-to-use prompts follow the 4-step process above.  
Pick the group for your current task, copy a prompt, fill in your project details, and run it.  
Each one produces structured output you can validate and ship.

### Group 1 – Bug Detection

Start here with any codebase or snippet.  
These prompts surface bugs by type and severity so you know exactly what you're dealing with before you prioritize anything.

=== "Comprehensive audit"
    **Use when:** running a full sweep of a codebase or feature for all bug types.
```text
    Analyze this code for ALL bugs and vulnerabilities: "[CODE]"

    Categorize problems by severity:

    1. CRITICAL BUGS (system breaking)
       - Race conditions and concurrency issues
       - Security vulnerabilities allowing exploitation
       - Data corruption or inconsistent states
       - Memory leaks and critical performance issues
       - Authentication/authorization bypass

    2. MAJOR BUGS (broken functionality)
       - Incorrect business logic implementation
       - Inadequate error handling and validation
       - Missing input sanitization
       - Incorrect calculations (prices, quantities, etc.)
       - Data consistency issues

    3. MINOR BUGS (quality and maintainability)
       - Inappropriate shared variables
       - Inefficient data structures
       - Poor exception handling patterns
       - Code smells and maintainability issues
       - Performance inefficiencies

    For each bug provide:
    - Location: Class, method, specific line numbers
    - Impact: User experience and system consequences
    - Reproduction: Step-by-step trigger scenario
    - Fix: Precise technical solution with code example
    - Severity: Risk level (Low/Medium/High/Critical)
```

=== "Pattern recognition"
    **Use when:** scanning for known bug patterns across logic, memory, concurrency, and I/O.
```text
    Scan this code for common bug patterns: "[CODE]"

    Look specifically for:

    Memory & Resource Issues:
    - Resource leaks (files, connections, memory)
    - Improper resource cleanup in finally blocks
    - Circular references preventing garbage collection

    Logical Errors:
    - Off-by-one errors in loops and arrays
    - Incorrect boolean logic (AND/OR confusion)
    - Missing null checks and defensive programming
    - Incorrect operator precedence assumptions

    Concurrency Problems:
    - Unsynchronized access to shared data
    - Deadlock potential in multiple lock scenarios
    - Thread-unsafe collection usage

    Input/Output Errors:
    - Missing input validation and sanitization
    - Improper error handling in I/O operations
    - Format string vulnerabilities

    Configuration & Environment:
    - Hardcoded credentials or sensitive data
    - Environment-specific assumptions
    - Missing configuration validation

    For each pattern found, provide specific line references and recommended fixes.
```

=== "Systematic methodology"
    **Use when:** conducting a deep, phased analysis across static, logic, concurrency, and integration layers.
```text
    Conduct a systematic bug hunt in this codebase: "[CODE]"

    Use this methodology:

    1. Static Analysis Phase
       - Review all method signatures and return types
       - Identify potential null pointer exceptions
       - Check array/collection bounds access
       - Validate exception handling coverage

    2. Logic Flow Analysis
       - Trace execution paths for edge cases
       - Identify unreachable code segments
       - Check for infinite loop conditions
       - Validate state machine transitions

    3. Concurrency Analysis (if applicable)
       - Identify shared mutable state
       - Check for race condition patterns
       - Validate thread-safe operations

    4. Integration Analysis
       - Check external API error handling
       - Validate database transaction boundaries
       - Review file I/O error scenarios
       - Test network failure resilience

    Generate a structured report with findings categorized by analysis phase.
```

### Group 2 – Security & Vulnerability Assessment

Go deeper on security after your general scan.  
These prompts think like attackers—finding the paths that general bug detection misses.

=== "Security vulnerabilities"
    **Use when:** performing a dedicated security audit focused on exploitable weaknesses.
```text
    Perform a comprehensive security audit on this application: "[CODE]"

    Examine these vulnerability categories:

    1. Injection Vulnerabilities
       - SQL injection in database queries
       - Path traversal in file operations
       - Cross-site scripting (XSS) potential
       - Command injection risks

    2. Authentication & Authorization Flaws
       - Authentication bypass vulnerabilities
       - Privilege escalation opportunities
       - Session management issues
       - Weak credential storage

    3. Data Exposure & Privacy
       - Sensitive data in logs or error messages
       - Unencrypted storage of credentials
       - API data over-exposure
       - Debug information disclosure

    4. Business Logic Vulnerabilities
       - Race conditions in financial operations
       - Integer overflow in calculations
       - Business process bypass
       - Transaction integrity issues

    For each vulnerability:
    - Severity Score: 1-10 rating with justification
    - Exploit Scenario: Detailed attack vector
    - Business Impact: Real-world consequences
    - Secure Patch: Implementation-ready fix
```

=== "OWASP Top 10"
    **Use when:** validating a web application against the industry-standard vulnerability checklist.
```text
    Evaluate this application against OWASP Top 10 vulnerabilities: "[CODE]"

    Check systematically for:

    1. A01: Broken Access Control
       - Missing authorization checks
       - Privilege escalation paths
       - Direct object reference attacks

    2. A02: Cryptographic Failures
       - Weak encryption algorithms
       - Poor key management
       - Weak random number generation

    3. A03: Injection
       - SQL injection vulnerabilities
       - NoSQL injection risks
       - OS command injection

    4. A04: Insecure Design
       - Missing security controls
       - Insufficient business logic validation
       - Security by obscurity assumptions

    Continue through all OWASP categories with specific code examples
    and remediation strategies for each finding.
```

=== "Penetration mindset"
    **Use when:** stress-testing code by thinking through real attacker scenarios and chained exploits.
```text
    Approach this code as a penetration tester: "[CODE]"

    Think like an attacker and identify:

    1. Attack Surface Analysis
       - All input points (forms, APIs, parameters)
       - Authentication mechanisms
       - File upload functionality

    2. Vulnerability Exploitation Paths
       - How to bypass authentication
       - Ways to escalate privileges
       - Methods to access unauthorized data

    3. Data Flow Attacks
       - Where sensitive data flows
       - Interception and manipulation points
       - Exfiltration possibilities

    4. Chain Attack Scenarios
       - Combining multiple minor vulnerabilities
       - Multi-step attack sequences
       - Persistence and lateral movement

    Provide concrete exploitation scenarios with proof-of-concept
    code where applicable.
```

### Group 3 – Severity, Triage & Reporting

Turn raw findings into something a team can act on.  
These prompts classify impact, validate fixes, and produce structured reports developers can work from directly.

=== "Impact classification"
    **Use when:** prioritizing a list of findings so the team knows what to fix first.
```text
    Classify and prioritize these bugs based on impact: "[BUG LIST]"

    Use this framework:

    Critical (P0) - Immediate Fix Required
    - System crashes or becomes unavailable
    - Data corruption or loss
    - Security breaches or unauthorized access
    - Financial loss or legal compliance violations

    High (P1) - Fix Within 24 Hours
    - Major feature completely broken
    - Significant performance degradation
    - User data exposure risks

    Medium (P2) - Fix Within 1 Week
    - Minor feature failures
    - Usability issues affecting user experience
    - Minor security concerns

    Low (P3) - Fix When Resources Available
    - Cosmetic issues
    - Code quality improvements
    - Enhancement suggestions

    For each bug provide:
    - Priority classification with justification
    - Estimated fix effort (hours/days)
    - Risk assessment if left unfixed
    - Dependencies and prerequisites for fixing
```

=== "Structured bug report"
    **Use when:** turning a raw finding into a complete, professional bug report ready to file.
```text
    Write a structured bug report for this finding: "[BUG DESCRIPTION + CODE CONTEXT]"

    The report must include:

    1. Title: One-line summary (component + symptom)
    2. Severity: P0–P3 with justification
    3. Environment: Language, framework, version, OS
    4. Steps to Reproduce: Numbered, exact, reproducible
    5. Expected Behavior: What should happen
    6. Actual Behavior: What happens instead (with output/stack trace)
    7. Root Cause Analysis: Why this bug exists
    8. Proposed Fix: Code-level recommendation
    9. Affected Areas: Other parts of the system at risk
    10. Verification: How to confirm the fix works

    Write for an audience of developers who have not seen this code before.
```

=== "Fix validation"
    **Use when:** verifying that a proposed fix actually resolves the bug without introducing new issues.
```text
    Validate this proposed bug fix: "[ORIGINAL CODE]" → "[FIXED CODE]"

    Check the following:

    1. Correctness
       - Does the fix address the root cause (not just the symptom)?
       - Are all edge cases from the original bug now handled?

    2. Regression Risk
       - Does the fix break any existing functionality?
       - Are there new failure paths introduced?

    3. Test Coverage
       - What unit tests should now pass?
       - What edge cases need new test cases?

    4. Code Quality
       - Is the fix consistent with existing code style?
       - Are there simpler or safer alternatives?

    Provide a pass/fail verdict per category with specific recommendations.
```


## Do's and Don'ts

Rules that separate bug reports that get fixed from ones that get ignored.  
Follow these and your findings drive real action.  
Break them and developers will close your tickets without a second look.

!!! tip "Do's"
    - Use structured prompts for consistent, categorized results
    - Provide full code context so AI can understand business logic
    - Always reproduce a bug manually before filing a report
    - State business impact in plain terms, not just technical jargon
    - Combine AI analysis with your own reading of the code
    - Request both a fix and a test to verify the fix

!!! warning "Don'ts"
    - File AI output directly as a bug report without validation
    - Use vague prompts that generate surface-level analysis
    - Focus only on syntax errors and ignore logical or security bugs
    - Skip severity classification—untriaged bugs pile up and rot
    - Ignore edge cases and non-happy-path scenarios
    - Treat AI severity ratings as final without your own judgment


## 60-second bug report checklist

| Pillar | Check | Pass? |
|--------|-------|-------|
| **Location** | Class, method, and line number identified? | ☐ |
| **Reproduction** | Step-by-step trigger anyone can follow? | ☐ |
| **Evidence** | Expected vs actual behavior documented? | ☐ |
| **Severity** | P0–P3 rating with business impact justification? | ☐ |
| **Fix** | Concrete recommendation or code example included? | ☐ |
| **Verification** | Test or criteria to confirm fix is working? | ☐ |


## Quick triage ladder

Work through these in order—stop when you have enough confidence to act:

1. **One scan**: Run the comprehensive audit prompt and skim for P0/P1 findings first
2. **Three reproductions**: Pick your top 3 findings and reproduce each manually
3. **Team read**: Can a developer act on your report without asking you anything?
4. **Security pass**: Run the OWASP or penetration mindset prompt on anything touching auth, payments, or user data

!!! tip
    A bug report nobody acts on is just noise. Precision, reproducibility, and clear impact turn findings into fixes.

> "The best bug report is the one that makes fixing the bug easier than arguing about it."