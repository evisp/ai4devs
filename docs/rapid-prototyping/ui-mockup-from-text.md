# UI Mockup from Text


![Motivation](https://i.imgur.com/e9Ctq2T.png)

A good interface starts with a clear idea, not a pretty screen.  
If you can turn a rough product description into a useful layout, you save time, reduce confusion, and make better design decisions earlier.

!!! note
    Text-to-UI tools can help you move fast, but speed is not the goal.
    Your job is to make screens clear, useful, and easy to improve.
    This page teaches the core concepts + ready prompts you can use for almost any product idea.


## Why you'll want these skills


- **Turn vague ideas into visible screens**: Move from "we need an app for this" to something people can react to
- **Find design problems early**: Catch confusion before anyone writes code
- **Improve communication**: Show teammates, clients, or stakeholders what the product could look like
- **Iterate faster**: Try multiple layout directions without starting from scratch every time
- **Build better judgment**: Learn what makes a screen clear, usable, and worth keeping



## What good UI mockups actually do for you

### 1. **Give each screen one clear job**
A strong mockup is not just a collection of boxes. It shows what the screen is for, what matters most, and what the user should do next.


- Put the main action where users can find it fast
- Show the most important content first
- Use labels people understand right away


### 2. **Reduce friction for the user**
A useful interface helps people move through a task with less guessing and fewer mistakes.


- Group related content together
- Make buttons, inputs, and feedback easy to notice
- Show errors, empty states, and next steps clearly


### 3. **Make design decisions easier to explain**
A mockup is useful when you can say why it looks the way it does.

- Keep a record of the prompt, result, and changes
- Compare versions based on clarity, not taste alone
- Explain what improved and what still needs work


## Your 4-step workflow to go from idea → interface


![Workflow](https://i.imgur.com/j3oLQzQ.png)


1. **Interpret** the brief
    - Find the user, the screen goal, and the main action.
    - Ask: What is this screen trying to help someone do?

2. **Structure** the screen
    - Decide what content appears first, what actions matter most, and how sections should be grouped.
    - Start simple before worrying about style.

3. **Refine** the design
    - Improve hierarchy, labels, spacing, states, and layout.
    - Make the screen easier to scan and easier to use.

4. **Review** and iterate
    - Check the result for clarity, usability, accessibility, and consistency.
    - Then adjust the prompt or the layout and try again.


!!! tip
    At every step, ask: "What is the user trying to do here, and does the screen make that obvious?"


## Prompt patterns you can reuse


These prompts follow the 4-step process above.  
Pick the group that matches your current stage, fill in your product details, and refine the result until the screen becomes clear and believable.


### Group 1 - Understand the screen


Start here when you only have a rough idea.  
These prompts help you define the screen before you try to generate or sketch it.


=== "Brief → screen plan"
    **Use when:** turning a product idea into a clear screen goal.


    ```text
    Turn this product idea into a screen plan: "[PRODUCT OR FEATURE DESCRIPTION]"

    Identify:
    1. The target user
    2. The purpose of the screen
    3. The main action the user should take
    4. The key content that must appear
    5. The secondary actions or supporting information
    6. The likely user questions or points of confusion

    Output format:
    - Screen name
    - User type
    - Main goal
    - Primary action
    - Required content
    - Risks or unclear areas
    ```


=== "Content hierarchy"
    **Use when:** deciding what deserves the most attention on the screen.


    ```text
    Organize the content hierarchy for this screen: "[SCREEN DESCRIPTION]"

    Create:
    1. The most important information at the top
    2. The supporting information underneath
    3. A clear primary call to action
    4. Secondary actions that should not compete with the main goal
    5. A suggested layout order from top to bottom

    Keep the structure simple and realistic for a first mockup.
    ```


=== "User flow"
    **Use when:** understanding what happens before, during, and after this screen.


    ```text
    Map the user flow around this screen: "[SCREEN OR FEATURE]"

    Show:
    1. What the user was doing before arriving here
    2. What they need to do on this screen
    3. What happens after success
    4. What could go wrong
    5. What support or feedback the interface should provide

    Output format: Short, practical user flow with clear transitions.
    ```


### Group 2 - Generate the mockup


Now turn the plan into an interface direction.  
Start with structure first, then move toward more polished design.


=== "Low-fidelity wireframe"
    **Use when:** you need a simple first layout without visual polish.


    ```text
    Create a low-fidelity UI wireframe for: "[SCREEN NAME]" in "[APPLICATION TYPE]"

    Include:
    1. The main layout structure
    2. Section order and content grouping
    3. Primary and secondary actions
    4. Navigation placement
    5. Form fields, cards, lists, or tables if needed
    6. Notes on what each section is for

    Keep it simple, practical, and focused on usability.
    Use real labels instead of placeholder nonsense.
    ```


=== "High-fidelity screen"
    **Use when:** you want a more realistic screen with stronger visual direction.


    ```text
    Design a polished interface for this screen: "[SCREEN NAME]" for "[APP OR PRODUCT]"

    Create:
    1. A clear visual hierarchy
    2. Realistic headings, labels, and button text
    3. A clean layout with strong spacing
    4. Consistent components and states
    5. A clear main action
    6. Short notes explaining why the layout works

    Keep the screen modern, easy to scan, and believable for a real product.
    ```


=== "Responsive variants"
    **Use when:** checking how the same screen should adapt across devices.


    ```text
    Adapt this interface across screen sizes: "[SCREEN DESCRIPTION]"

    Show:
    1. Mobile layout
    2. Tablet layout
    3. Desktop layout

    For each version, explain:
    - What stays the same
    - What moves or changes
    - How the primary action stays visible
    - How content priority is preserved
    ```

=== "State variations"
    **Use when:** the first mockup only shows the ideal case.


    ```text
    Create key interface states for this screen: "[SCREEN DESCRIPTION]"

    Include:
    1. Default state
    2. Empty state
    3. Loading state
    4. Error state
    5. Success state

    For each state, show:
    - What the user sees
    - What message appears
    - What action they can take next
    ```


### Group 3 - Review and improve


These prompts help you judge whether the design actually works.  
Use them after you have a first mockup, not before.


=== "Usability review"
    **Use when:** checking if the screen is easy to understand and use.


    ```text
    Review this interface for usability: "[MOCKUP OR SCREEN DESCRIPTION]"

    Evaluate:
    1. Clarity of the screen purpose
    2. Visual hierarchy and scanability
    3. Navigation and task flow
    4. Button and input clarity
    5. Error prevention and feedback
    6. Content clarity and wording

    Give:
    - 3 strengths
    - 5 problems
    - 3 priority fixes
    ```

=== "Accessibility check"
    **Use when:** making sure the design is usable for more people.


    ```text
    Review this interface for accessibility: "[MOCKUP OR SCREEN DESCRIPTION]"

    Check:
    1. Contrast between text and background
    2. Readability of labels and body text
    3. Clarity of button states and focus states
    4. Form labels and error messages
    5. Keyboard-friendly interaction
    6. Mobile readability and touch comfort

    Output:
    - Issues found
    - Why they matter
    - Simple fixes in priority order
    ```


=== "Iteration log"
    **Use when:** documenting how the design changed over time.


    ```text
    Create a design iteration log for this mockup process.

    Context:
    - Product idea: "[PRODUCT IDEA]"
    - First prompt: "[PROMPT USED]"
    - First result: "[SHORT DESCRIPTION]"
    - Problems found: "[ISSUES]"
    - Revised prompt: "[UPDATED PROMPT]"
    - New result: "[SHORT DESCRIPTION]"

    Summarize:
    1. What changed
    2. Why it changed
    3. What improved
    4. What still needs work
    5. What I would test next
    ```

## Design habits that make mockups better


Small habits make a huge difference when you turn text into screens.


- Start with one screen, not the whole product
- Decide the main user action before you design anything
- Use real headings, button labels, and content
- Keep layouts simple before adding decoration
- Show important states, not just the perfect case
- Write down what changed between versions


## Do's and Don'ts


Simple rules that help you create mockups people can understand quickly.  
Follow them and your screens become easier to review, fix, and improve.



!!! tip "Do's"
    - Start with the user's goal
    - Use clear labels and realistic content
    - Show one strong primary action
    - Group related information together
    - Review empty, error, and success states
    - Keep notes on prompts and revisions


!!! warning "Don'ts"
    - Design the whole product at once
    - Hide the main action in a crowded layout
    - Use vague labels like "Submit" when something more specific works better
    - Rely on style to fix a weak structure
    - Ignore accessibility and readability
    - Keep only the final version and lose the thinking behind it


## 60-second UI checklist


| Area | Check | Pass? |
|------|-------|-------|
| **Purpose** | Is the screen's job obvious in 5 seconds? | ☐ |
| **Hierarchy** | Do the most important items stand out first? | ☐ |
| **Action** | Is the main action clear and easy to find? | ☐ |
| **Clarity** | Are labels, buttons, and messages easy to understand? | ☐ |
| **States** | Have you considered empty, error, loading, and success states? | ☐ |
| **Access** | Is the screen readable and usable for different users? | ☐ |


## Quick validation ladder


Test your mockup in 4 steps, from fast to useful:


1. **Five-second scan**: Can someone tell what this screen is for almost immediately?
2. **One-task test**: Can a user complete the main action without explanation?
3. **State check**: What happens when data is missing, wrong, slow, or complete?
4. **Revision check**: Can you explain what changed between version 1 and version 2?


!!! tip
    A good mockup does not need to be beautiful first.
    It needs to be understandable first.

> If the user has to stop and decode the screen, the mockup is not finished.
