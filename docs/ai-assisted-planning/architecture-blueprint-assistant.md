# Architecture Designer

Your architecture choices determine a good deal of your system's success or failure.   Good architecture scales, stays maintainable, and saves money long-term.  
Bad choices mean rewrites, outages, and frustrated teams.

![Happy team around successful architecture diagram](https://i.imgur.com/UP0l0om.png)

## Why you'll want these skills

- Build systems that grow without breaking
- Choose between monolith vs microservices confidently  
- Draw diagrams everyone instantly understands
- Explain your decisions to managers and developers
- Avoid "it worked in prototype but failed in production"


## What good architecture actually does

![Three pillars architecture diagram](https://i.imgur.com/Av4gWHJ.png)


Great architecture works quietly in the background.  
It lets small teams ship fast, big teams coordinate cleanly, and systems grow without panic rewrites.  
When done right, nobody notices. When done wrong, everybody suffers.

!!! tip
    Good architecture = practical choices that work for your real constraints.

### 1. **Matches your reality**

Right tool for your team size, budget, and timeline-not what you read in blogs.

- Small team? Monolith gets you shipping faster
- Big team/scaling needs? Microservices split responsibilities cleanly
- No team? Serverless removes ops burden

### 2. **Handles growth gracefully** 

Today's 100 users become tomorrow's 100K without panic rewrites.

- Database that scales with traffic patterns
- Services that fail independently 
- Clear upgrade paths

### 3. **Explains itself**

Anyone onboarded next week can understand the "why" behind every choice.

- Diagrams show data flows clearly
- Decision records explain trade-offs
- No magic-everything has rationale


## Your 4-step architecture workflow

Follow these steps to go from requirements to a defensible architecture decision.

1. **Analyze** requirements  
   Figure out what actually needs to scale, perform well, or stay simple. Consider your real team size and budget.

2. **Sketch alternatives**  
   Draw monolith, microservices, and hybrid options-each showing clear strengths and trade-offs.

3. **Detail components**  
   Define services, databases, APIs, and message flows with concrete diagrams anyone can follow.

4. **Compare + decide**  
   Score options against your constraints and document exactly why you picked the winner.

!!! tip
    Always ask: "Does this match *my* team size, timeline, and scaling needs?"

## Prompt patterns (match your workflow stage)

These ready-to-use prompts follow the 4 steps above.  
Pick your stage, copy the prompt, fill project details, get structured output.

### Group 1 - Analyze Requirements

Start with what you actually need to build.  
These prompts dig into your real constraints and identify what matters most for architecture decisions.


=== "System constraints"
    **Use when:** turning requirements into architecture drivers.

    ```text
    Analyze these requirements for architecture impact: "[REQUIREMENTS BRIEF]"

    Identify:
    1. Scaling needs (users, traffic patterns, growth rate)
    2. Performance requirements (response times, throughput)
    3. Team constraints (size, skills, velocity)
    4. Budget limits (infrastructure, development time)
    5. Key risks (single points of failure, complexity)

    Output format: Clear sections with concrete numbers where possible.
    ```

=== "Scaling needs"
    **Use when:** figuring out what actually needs to scale.

    ```text
    From this system description, identify scaling requirements: "[SYSTEM DESCRIPTION]"

    For each component:
    1. Expected load (users/day, requests/sec, data volume)
    2. Growth rate (monthly/annual)
    3. Peak vs average patterns
    4. Failure tolerance (how many users can we lose?)
    5. Geographic distribution needs

    Suggest database, compute, and caching needs.
    ```

=== "Component inventory"
    **Use when:** listing everything that needs building.

    ```text
    Create component inventory for: "[PRODUCT DESCRIPTION]"

    List all:
    1. User-facing services (web, mobile, admin)
    2. Core business services (matching, payments, notifications)
    3. Data stores (user data, transactions, analytics)
    4. Integration points (external APIs, 3rd parties)
    5. Shared infrastructure (auth, logging, monitoring)

    Include rough size/complexity estimates.
    ```

### Group 2 - Design Alternatives

Turn requirements into concrete architecture options.  
These prompts generate monolith, microservices, and data designs you can actually build and compare.

=== "Monolith design"
    **Use when:** considering single-deployable architecture.

    ```text
    Design monolith architecture for: "[REQUIREMENTS + CONSTRAINTS]"

    Provide:
    1. High-level component diagram (modules/layers)
    2. Database design (tables/relationships)
    3. API structure (major endpoints)
    4. Deployment model (servers, containers)
    5. Scaling strategy (vertical vs horizontal)
    6. Known limitations for future growth

    Include simple ASCII diagram.
    ```

=== "Microservices breakdown"
    **Use when:** splitting into independent services.

    ```text
    Design microservices architecture for: "[REQUIREMENTS + CONSTRAINTS]"

    Create:
    1. Service boundaries (5-8 services max)
    2. Communication patterns (sync API vs async events)
    3. Data ownership per service (no shared DB)
    4. Deployment strategy (per service or platforms)
    5. Observability plan (tracing, metrics, logs)
    6. API gateway design

    Include service interaction diagram (ASCII).
    ```

=== "Data model options"
    **Use when:** deciding database strategy.

    ```text
    Design data architecture for: "[SYSTEM REQUIREMENTS]"

    Compare 3 options:
    1. Single relational DB (schema + trade-offs)
    2. Multiple databases per service (CQRS/Event Sourcing)
    3. Hybrid approach (shared + service-specific)

    For each option include:
    - Consistency model
    - Query performance strategy
    - Migration complexity
    - Operational overhead

    Recommend best fit with justification.
    ```

### Group 3 - Compare & Decide

Make your final choice with clear reasoning.  
These prompts create objective comparisons and decision records that justify your architecture to anyone.

=== "Tradeoff matrix"
    **Use when:** comparing architecture options objectively.

    ```text
    Compare these architecture options: "[MONOLITH DESCRIPTION] vs [MICROSERVICES DESCRIPTION]"

    Rate each across:
    - Development velocity (team of X developers)
    - Initial cost (infrastructure + dev time)
    - Operational complexity (deploy, monitor, debug)
    - Scaling capability (handle 10x growth)
    - Team skill requirements
    - Failure isolation
    - Technology lock-in risk

    Provide clear winner + 3-step migration path from current state.
    ```

=== "Decision record"
    **Use when:** documenting your final choice.

    ```text
    Document architecture decision for: "[PROJECT + CHOSEN ARCHITECTURE]"

    Create Architecture Decision Record (ADR):
    1. Context + problem statement
    2. Options considered (2-3 alternatives)
    3. Decision + justification
    4. Consequences (positive + negative)
    5. Risks + mitigations
    6. Timeline for revisit

    Status: Proposed/Accepted/Deprecated/Superseded.
    ```

=== "Migration plan"
    **Use when:** moving from simple to complex architecture.

    ```text
    Create migration plan from "[CURRENT ARCHITECTURE]" to "[TARGET ARCHITECTURE]"

    Phases:
    1. Minimum viable target (extract 1 service)
    2. Incremental decomposition (next 2 services)
    3. Full transition + cleanup
    4. Optimization phase

    Include: risks per phase, rollback strategy, success metrics.
    ```

## Templates (copy/paste)

Ready-made starting points for your diagrams and decisions.  
Copy, fill in your project details, iterate as needed.  
These formats work for any architecture discussion.

### Monolith layers

A monolith is one application that contains all the main parts of your system in a single deployable unit.  
Everything ships together, but you still organize the code into layers (UI, business logic, data access) so it stays understandable and testable as it grows.

```markdown
┌─────────────────────────────────────┐
│            Presentation             │
│   Web UI / Mobile / Public API      │
└─────────────────────────────────────┘
            │ HTTP/JSON
┌─────────────────────────────────────┐
│              Business               │
│   Core logic / Use cases / Domain   │
└─────────────────────────────────────┘
            │ In-process calls
┌─────────────────────────────────────┐
│              Data Access            │
│   Repositories / Queries / Events   │
└─────────────────────────────────────┘
            │ SQL
┌─────────────────────────────────────┐
│              Database               │
└─────────────────────────────────────┘
```

### Microservices canvas

Each service gets its own template to define responsibilities clearly.  
Fill this out for every microservice so teams know exactly what each one owns, how it communicates, and how it's deployed.

```markdown
Service: [NAME]                    Owner: [TEAM]
├── Purpose: [Single responsibility]
├── Data: [Owned tables/collections]
├── APIs: [REST/GraphQL endpoints]
├── Events published: [list]
├── Events consumed: [list]
├── Downstream calls: [external APIs]
├── Deployment: [Docker/K8s/Serverless]
└── Monitoring: [metrics, alerts, traces]
```

### Architecture tradeoff table

Compare your options side-by-side across real criteria that matter.  
Fill in scores for each architecture, see the clear winner emerge.  
This format works for any architecture decision, not just monolith vs microservices.

```markdown
| Criterion          | Monolith | Microservices | Winner    |
|--------------------|----------|---------------|-----------|
| Dev Velocity       | Fast     | Slow (start)  | Monolith  |
| Operational Cost   | Low      | High          | Monolith  |
| Scaling            | Limited  | Excellent     | Micro     |
| Failure Isolation  | Poor     | Excellent     | Micro     |
| Team Size Fit      | <10 devs | >20 devs      | Depends   |
```

## Do's and Don'ts

Simple rules that separate solid architecture from tech debt disasters.

!!! tip "Do's"
    - Start simple, evolve based on real needs
    - Draw before you code-paper sketches first
    - Document trade-offs, not just the winner
    - Design for your *actual* team size
    - Plan failure modes from day one
    - Keep deployment simple (fewer moving parts)

!!! warning "Don'ts"
    - Copy blog architecture without context
    - Microservices for 3-developer startup
    - Skip diagrams-words confuse, visuals clarify
    - Assume "scaling later is easy"
    - Ignore operational reality (who pages at 3am?)
    - Optimize prematurely

## Architecture checklist (before you commit)

Final gut check before you present or build.  
Run through these 5 questions-answer "yes" to all before moving forward.  
Missing any means you're probably making a risky choice.

| Area | Check | Pass? |
|------|-------|-------|
| **Team Fit** | Matches current team size/skills? | ☐ |
| **Scaling** | Handles expected growth? | ☐ |
| **Operations** | Someone can deploy/monitor it? | ☐ |
| **Failure** | Single failure doesn't kill everything? | ☐ |
| **Cost** | Budget realistic for infra + people? | ☐ |

## Quick validation ladder

1. **One read**: Can junior dev understand deployment?
2. **Load test**: Does it handle 2x expected traffic?  
3. **Failure test**: Kill one component-does rest survive?
4. **Cost check**: Monthly infra bill realistic?

!!! tip
    Good architecture seems obvious *after* you draw it, confusing *before* you do.
    
> "Make the simplest architecture that could possibly work... then simplify it again." - Architecture wisdom
