# Specification Writer

![Motivation](https://i.imgur.com/71EjWAw.png)

Every software project starts with a spec. A good spec eliminates confusion and gets everyone working toward the same goal.  
Bad specs lead to wasted time, rework, and arguments about what was "really" meant.

!!! note
    AI helps generate structured specs fast, but you must check completeness, feasibility, and business fit.
    This page teaches key concepts + ready prompts for any project.

## Why you'll want these skills

- **Save weeks of back-and-forth**: Turn vague ideas into clear plans your team can actually build from
- **Stop "what did you mean?" arguments**: Write requirements everyone interprets the same way  
- **Ship faster**: Get developers coding the right thing from day one
- **Look professional**: Create specs that impress clients, managers, and teammates
- **Build confidence**: Know exactly when something is "done done"


## What good specs actually do for you

![3 Pillars](https://i.imgur.com/ccA32Gw.png)

### 1. **No more confusion** 
Your spec means exactly one thing to everyone who reads it.
- Use concrete examples (JSON shape, not "user data")  
- Say your assumptions out loud
- No room for "I thought you meant..."

### 2. **Nothing falls through cracks**
Covers everything that matters, not just the happy path.
- What users do + how fast it loads + how it fails
- Every feature → test cases → error messages
- Third-party APIs and edge cases included

### 3. **You can prove it's done**
No arguing about completion—just facts.
- "< 2s load time" not "feels fast"
- Tests exist for every acceptance criteria  
- Realistic timeline and team skills checked


### To illustrate, let's use...

**CarpoolConnect**  
Corporate carpooling app that matches employees by commute route/schedule, tracks CO2 savings, and connects with company login systems.

## Your 4-step workflow to complete specs

![4 Step Workflow](https://i.imgur.com/HjDEuyz.png)

1. **Analyze** the brief  
   Read between the lines → pull out *exactly* what they need (features, users, limits)

2. **Decompose** into user stories  
   Break big ideas → small, testable "As a [user] I want [feature] so [benefit]" cards

3. **Detail** the technical solution  
   APIs + database + integrations → concrete blueprints developers can code from

4. **Validate** everything works  
   Check for gaps → confirm timeline/team fit → get stakeholder buy-in


!!! tip
    At each step, ask: "Is this clear? Complete? Testable?"

## Prompt patterns (match your workflow stage)

These ready-to-use prompts follow the 4-step process above.  
Pick the group for your current task, copy a prompt, fill in your project details, and run it.  
Each one produces structured output you can refine and ship.

### Group 1 — Analyze & Decompose

Start here with raw ideas or client briefs.  
These prompts pull out the real requirements and break them into clear user stories everyone can understand.


=== "Brief → requirements"
    **Use when:** turning a client idea into structured requirements.

    ```text
    Analyze this client brief to identify technical requirements: "[CLIENT BRIEF]"

    Produce:
    1. Functional requirements (5-8 key features with acceptance criteria)
    2. Non-functional requirements (performance, security, compatibility)  
    3. Technical constraints (imposed technologies, budget/time limits)
    4. User personas (2-3 profiles with specific needs)
    5. Usage scenarios (detailed user journeys)

    Output format: Structured document with clearly delimited sections and concrete examples.
    ```

=== "User stories"
    **Use when:** breaking features into testable user needs.

    ```text
    Create comprehensive user stories for this application: "[APP DESCRIPTION]"

    For each user type, develop:
    1. Epic-level stories (high-level business objectives)
    2. Feature-level stories (specific functionality)  
    3. Acceptance criteria (testable conditions for completion)
    4. Edge cases (error handling, boundary conditions)
    5. Priority levels (must-have, should-have, could-have)

    Format: "As a [user type], I want [goal] so that [benefit]" with detailed acceptance criteria.
    ```

=== "Personas + scenarios"
    **Use when:** understanding different user types and their journeys.

    ```text
    Create user personas and usage scenarios for: "[PRODUCT DESCRIPTION]"

    For 3 key user types, provide:
    1. Persona profile (role, goals, pain points, tech comfort)
    2. Typical day journey (3-5 key moments)
    3. Pain points with current solutions
    4. Success metrics for this product

    Output format: Clear sections per persona with concrete examples.
    ```

### Group 2 — Detail (technical specs)

Turn user stories into concrete blueprints.  
These prompts generate APIs, database designs, and integration plans developers can code from directly.


=== "API design"
    **Use when:** defining endpoints, data formats, authentication.

    ```text
    Design API specifications for this application: "[APPLICATION REQUIREMENTS]"

    Create:
    1. OpenAPI specification with all endpoints
    2. Authentication design (OAuth 2.0, JWT, API keys)
    3. Data models (request/response JSON schemas)  
    4. Error handling (HTTP codes, error response format)
    5. Rate limiting specifications
    6. Versioning strategy

    Include example requests/responses for each endpoint.
    ```

=== "Database schema"
    **Use when:** designing data models and relationships.

    ```text
    Design database schema for this application: "[APPLICATION DESCRIPTION]"

    Generate:
    1. Entity-relationship diagram description (tables, relationships)
    2. Table definitions with columns, types, constraints
    3. Indexing strategy (performance considerations)
    4. Sample queries for common operations
    5. Data validation rules

    Include relationships between key entities.
    ```

=== "Integrations"
    **Use when:** connecting to external systems/services.

    ```text
    Define integration requirements for: "[APPLICATION + EXTERNAL SERVICES]"

    Specify for each integration:
    1. External service dependencies (APIs, databases)
    2. Authentication methods
    3. Data synchronization strategy (real-time vs batch)
    4. Error handling and retry logic
    5. Fallback mechanisms
    6. Monitoring requirements

    Include integration flow description.
    ```

### Group 3 — Validate & Refine

Your final quality check before sharing specs.  
These prompts find missing pieces, check if timelines are realistic, and spot risks before they become problems.

=== "Completeness check"
    **Use when:** ensuring nothing critical is missing.

    ```text
    Evaluate this specification for completeness: "[SPECIFICATION DOCUMENT]"

    Verify each area:
    - Functional requirements (features, acceptance criteria)
    - Non-functional requirements (performance, security, scale)
    - Technical constraints (stack, infrastructure)
    - Integration specifications (APIs, data flows)
    - Testing requirements (unit, integration, E2E)
    - Deployment specifications (CI/CD, monitoring)

    Flag gaps and propose specific fixes for each.
    ```

=== "Feasibility analysis"
    **Use when:** checking if specs match reality.

    ```text
    Assess feasibility of this specification: "[SPECIFICATION + CONSTRAINTS]"

    Analyze:
    - Technical feasibility (technology fit, complexity)
    - Budget alignment (development + infra costs)
    - Timeline realism (phases, milestones)
    - Team requirements (skills, size)
    - Maintenance costs

    Provide risk ratings and mitigation steps.
    ```

=== "Risks + gaps"
    **Use when:** identifying what could go wrong.

    ```text
    Identify risks for this project: "[PROJECT SPECIFICATIONS]"

    Categorize by:
    1. Technical risks (integration, performance)
    2. Business risks (adoption, market fit)
    3. Operational risks (team, timeline)
    4. External risks (vendors, regulations)

    For each risk: impact, probability, mitigation, contingency.
    ```

## Do's and Don'ts

Simple rules that separate good specs from endless arguments.  
Follow these and your team builds the right thing.  
Break them and you'll fix misunderstandings for weeks.


!!! tip "✅ Do's"
    - Use clear, specific language
    - Include concrete examples and schemas
    - Write measurable acceptance criteria
    - Consider non-functional requirements early
    - Document assumptions explicitly
    - Validate with stakeholders

!!! warning "❌ Don'ts"
    - Write vague requirements ("user-friendly")
    - Skip non-functional requirements
    - Ignore integration complexity
    - Forget error handling and edge cases
    - Overlook security/compliance
    - Skip feasibility validation

## 60-second spec checklist

| Pillar | Check | Pass? |
|--------|-------|-------|
| **Clarity** | Concrete examples? No ambiguity? | ☐ |
| **Completeness** | Functional + non-functional? Integrations? | ☐ |
| **Testability** | Measurable criteria? Edge cases? | ☐ |



## Quick validation ladder

Test your spec in 4 steps, from fast to thorough:

1. **One check**: Does it pass the 60-second checklist above?
2. **Three tests**: Pick 3 acceptance criteria—can you actually test them?  
3. **Team read**: Can a developer understand without asking questions?
4. **Edge case audit**: Are all failure scenarios handled?

!!! tip
    Good specs feel boring—they say exactly what they mean with no room for interpretation.
    
> "The best writing is writing you don't notice." — Spec writer's golden rule
