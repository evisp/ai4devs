# API Prototyper


![Motivation](https://i.imgur.com/wQ11uiB.png)


A good API starts with clear behavior, not just working code.  
If you can turn requirements into a clean contract, implement it correctly, and test it with confidence, you make the whole product easier to build and maintain.

!!! note
    API tools can help you move faster, but speed is not enough.
    Your job is to make the API clear, reliable, testable, and easy for others to use.
    This page teaches the core concepts + ready prompts you can use for almost any API project.


## Why you'll want these skills


- **Turn features into working endpoints**: Move from "the app needs this" to a usable API other people can build on
- **Reduce confusion between frontend and backend**: Define inputs, outputs, and errors clearly from the start
- **Catch mistakes earlier**: Spot gaps in validation, status codes, and edge cases before they break things
- **Test with confidence**: Prove that the API behaves the way the contract says it should
- **Document once, use everywhere**: Reuse the same API definition for implementation, docs, and testing



## What good API design actually does for you


### 1. **Makes the contract clear**
A strong API tells people exactly what goes in, what comes out, and what happens when something goes wrong.


- Define routes, methods, parameters, and request bodies clearly
- Use predictable response shapes
- Return useful errors instead of vague failures


### 2. **Makes the system more reliable**
A useful API handles more than the happy path.  
It validates input, protects data quality, and responds consistently.


- Check required fields and invalid values
- Use status codes on purpose
- Handle edge cases before users find them for you


### 3. **Makes the work reusable**
One good API definition helps with more than coding.  
It supports implementation, testing, documentation, and team communication.


- Reuse the same contract in YAML or JSON
- Keep docs and routes aligned
- Make it easier for others to explore and test the API


## Your 5-step workflow to go from requirement → working API


![Workflow](https://i.imgur.com/yy5nh5e.png)

1. **Interpret** the requirements
    - Identify the main resources, actions, inputs, outputs, and rules
    - Separate business logic from transport details
    - Ask: What should this API let the client do?


2. **Design** the contract
    - Define endpoints, methods, parameters, schemas, status codes, and errors
    - Write the API contract clearly before building the routes
    - Keep names and response shapes consistent


3. **Implement** the endpoints
    - Turn the contract into working routes in Express.js or FastAPI
    - Start with the core behavior before adding extras
    - Keep the code aligned with the contract


4. **Test** the API
    - Write unit tests for logic and integration tests for real request-response behavior
    - Check valid input, invalid input, and error cases
    - Make sure the implementation matches the contract


5. **Document** and reflect
    - Publish clear docs and example requests
    - Make the API easy to explore with Swagger and Postman
    - Note what worked well, what broke, and what still needs improvement


!!! tip
    At every step, ask: "If someone new joins this project tomorrow, could they understand and use this API without guessing?"


## Prompt patterns you can reuse


These prompts follow the 5-step process above.  
Pick the group that matches your current stage, fill in your project details, and refine the result until the API becomes clear, consistent, and usable.


### Group 1 - Requirements → API shape


Start here with product requirements or feature descriptions.  
These prompts help you turn business needs into resources, routes, and expected behavior.


=== "Requirements → endpoints"
    **Use when:** turning feature requirements into API structure.


    ```text
    Turn these functional requirements into an API plan: "[REQUIREMENTS]"

    Identify:
    1. Main resources
    2. Key actions users or systems need to perform
    3. Suggested endpoints
    4. HTTP methods for each endpoint
    5. Required inputs and expected outputs
    6. Validation rules and error cases

    Output format:
    - Resource
    - Endpoint
    - Method
    - Purpose
    - Inputs
    - Outputs
    - Error cases
    ```


=== "Business rules → validation"
    **Use when:** defining what the API should accept or reject.


    ```text
    Extract validation and business rules for this API feature: "[FEATURE DESCRIPTION]"

    Produce:
    1. Required fields
    2. Optional fields
    3. Invalid cases
    4. Field-level constraints
    5. Business rule checks
    6. Error messages or response ideas

    Keep the rules concrete and implementation-ready.
    ```


=== "User actions → methods"
    **Use when:** mapping real actions to HTTP behavior.


    ```text
    Map these product actions to API behavior: "[USER ACTIONS OR FLOW]"

    For each action, provide:
    1. The best resource name
    2. The route
    3. The HTTP method
    4. The request data needed
    5. The expected success response
    6. Likely failure responses

    Keep naming predictable and consistent.
    ```


### Group 2 - OpenAPI contract


Now turn the API shape into a formal contract.  
Use this stage to define request and response models, errors, and reusable schemas.


=== "OpenAPI spec"
    **Use when:** generating a full API contract.


    ```text
    Create an OpenAPI specification for this API: "[API DESCRIPTION OR REQUIREMENTS]"

    Include:
    1. API title and description
    2. Paths and operations
    3. Parameters
    4. Request bodies
    5. Response schemas
    6. Error responses
    7. Reusable components
    8. Authentication section if needed

    Output the result in OpenAPI YAML.
    ```


=== "YAML → JSON"
    **Use when:** converting one spec format into another.


    ```text
    Convert this OpenAPI YAML into valid OpenAPI JSON: "[YAML SPEC]"

    Requirements:
    1. Preserve all paths and operations
    2. Preserve schemas and examples
    3. Preserve error responses
    4. Preserve security definitions
    5. Return clean, valid JSON only
    ```


=== "Schemas + errors"
    **Use when:** defining data models and failure behavior clearly.


    ```text
    Design request, response, and error schemas for this API: "[ENDPOINT OR FEATURE]"

    Create:
    1. Request body schema
    2. Success response schema
    3. Validation error schema
    4. Not found error schema
    5. Authorization error schema if relevant
    6. Example payloads for each

    Keep field names realistic and consistent.
    ```


=== "Auth design"
    **Use when:** deciding how the API should protect routes.


    ```text
    Propose an authentication approach for this API: "[API CONTEXT]"

    Compare and recommend:
    1. JWT
    2. Session-based auth
    3. API keys
    4. Role-based access needs

    For the chosen approach, define:
    - Protected routes
    - Required headers
    - Error responses
    - Token or credential flow
    ```


### Group 3 - Implementation


Turn the contract into working code.  
Keep this stage focused on route behavior, validation, and consistency with the spec.


=== "FastAPI scaffold"
    **Use when:** building a Python version of the API.


    ```text
    Create a FastAPI scaffold for this API contract: "[OPENAPI OR ENDPOINT DESCRIPTION]"

    Include:
    1. Route definitions
    2. Pydantic models
    3. Request validation
    4. Example success responses
    5. Error handling structure
    6. Clear file organization

    Keep the code simple, readable, and aligned with the contract.
    ```


=== "Express.js scaffold"
    **Use when:** building a Node.js version of the API.


    ```text
    Create an Express.js scaffold for this API contract: "[OPENAPI OR ENDPOINT DESCRIPTION]"

    Include:
    1. Route definitions
    2. Request validation structure
    3. Controller placeholders
    4. Example success responses
    5. Error handling middleware
    6. Clear file organization

    Keep the code simple, readable, and aligned with the contract.
    ```


=== "Validation + errors"
    **Use when:** improving route quality after the first version works.


    ```text
    Improve validation and error handling for this API implementation: "[CODE OR ENDPOINT DESCRIPTION]"

    Review:
    1. Missing required field checks
    2. Invalid input handling
    3. Status code consistency
    4. Error response shape
    5. Repeated logic that should be centralized

    Suggest specific fixes and example code.
    ```


### Group 4 - Testing and docs


Once the API works, prove it works.  
These prompts help you cover behavior, publish docs, and make the API easy to explore.


=== "Unit tests"
    **Use when:** testing core logic in isolation.


    ```text
    Write unit tests for this API logic: "[FUNCTION, CONTROLLER, OR SERVICE]"

    Cover:
    1. Expected success cases
    2. Invalid input cases
    3. Boundary conditions
    4. Error handling
    5. Mocked dependencies if needed

    Return clean, runnable test code.
    ```


=== "Integration tests"
    **Use when:** testing full request-response behavior.


    ```text
    Write integration tests for these API endpoints: "[ENDPOINTS OR APP DESCRIPTION]"

    Include:
    1. Successful requests
    2. Validation failures
    3. Not found cases
    4. Unauthorized cases if relevant
    5. Response body assertions
    6. Status code assertions

    Use a practical structure suitable for automated test runs.
    ```


=== "Swagger docs"
    **Use when:** preparing interactive API documentation.


    ```text
    Create Swagger-ready API documentation content for this project: "[API DESCRIPTION OR OPENAPI SPEC]"

    Include:
    1. API summary
    2. Endpoint descriptions
    3. Parameter descriptions
    4. Example requests
    5. Example responses
    6. Authentication notes
    7. Common error cases

    Keep the language short, clear, and developer-friendly.
    ```


=== "Postman examples"
    **Use when:** creating testable API examples for manual review.


    ```text
    Create Postman-ready request examples for this API: "[OPENAPI SPEC OR ENDPOINT LIST]"

    Include for each endpoint:
    1. Method
    2. URL
    3. Headers
    4. Request body if needed
    5. Example success response
    6. Example error response

    Keep the examples realistic and easy to test manually.
    ```


### Group 5 - Review and reflection


Use these prompts as your final quality check.  
They help you find mismatches between the contract, the code, the tests, and the docs.


=== "Contract vs implementation"
    **Use when:** checking whether the code matches the spec.


    ```text
    Compare this implementation against the API contract.

    Contract:
    "[OPENAPI SPEC OR SUMMARY]"

    Implementation:
    "[CODE OR ENDPOINT SUMMARY]"

    Check:
    1. Missing routes
    2. Wrong status codes
    3. Missing validation
    4. Schema mismatches
    5. Error handling differences
    6. Documentation gaps

    Report the mismatches clearly and suggest fixes.
    ```


=== "Testing gaps"
    **Use when:** finding what your test suite still misses.


    ```text
    Review this API test coverage for gaps: "[TEST FILES OR TEST SUMMARY]"

    Identify:
    1. Untested success cases
    2. Untested validation failures
    3. Untested edge cases
    4. Untested error responses
    5. Weak assertions
    6. Missing integration coverage

    Prioritize the missing tests from highest risk to lowest.
    ```


=== "Reflection"
    **Use when:** capturing what you learned from the process.


    ```text
    Help me reflect on this API prototyping workflow.

    Context:
    - Requirements: "[REQUIREMENTS]"
    - Contract: "[OPENAPI SUMMARY]"
    - Implementation: "[EXPRESS OR FASTAPI SUMMARY]"
    - Tests: "[TEST SUMMARY]"
    - Documentation: "[SWAGGER OR POSTMAN SUMMARY]"

    Write a short reflection covering:
    1. What became clearer during the process
    2. What was easy to generate
    3. What still required careful manual thinking
    4. What problems appeared during testing
    5. What I would improve in the next version
    ```
    

## Design habits that make APIs better


Small habits make a huge difference when you turn requirements into routes.


- Start with the contract before writing a lot of code
- Name resources and fields consistently
- Keep response shapes predictable
- Treat errors as part of the design, not an afterthought
- Test both success and failure paths
- Keep documentation close to the real implementation


## Do's and Don'ts


Simple rules that help you build APIs other people can trust.  
Follow them and your endpoints become easier to build, test, and use.



!!! tip "Do's"
    - Define the contract before building too much
    - Use clear route names and consistent schemas
    - Validate input early
    - Return useful status codes and error messages
    - Keep tests close to the behavior you promise
    - Make docs easy to explore and reuse


!!! warning "Don'ts"
    - Build endpoints with no clear contract
    - Return different response shapes for similar routes
    - Ignore invalid input and edge cases
    - Hide useful errors behind generic failures
    - Treat testing as optional
    - Let the docs drift away from the code


## 60-second API checklist


| Area | Check | Pass? |
|------|-------|-------|
| **Purpose** | Is each endpoint's job clear? | ☐ |
| **Contract** | Are inputs, outputs, and errors defined clearly? | ☐ |
| **Consistency** | Do names, schemas, and status codes follow a pattern? | ☐ |
| **Validation** | Are invalid and missing inputs handled properly? | ☐ |
| **Testing** | Are success and failure cases covered? | ☐ |
| **Docs** | Can another developer try the API without guessing? | ☐ |


## Quick validation ladder


Test your API in 5 steps, from fast to useful:


1. **One read**: Can someone understand the routes and payloads from the contract alone?
2. **One request**: Can the main endpoint complete a successful request correctly?
3. **One failure**: What happens when required input is missing or invalid?
4. **One doc check**: Do the docs match the actual behavior?
5. **One reflection**: What did you assume at first that testing proved wrong?


!!! tip
    A good API is not just one that works once.
    It is one that behaves clearly, consistently, and predictably.

> "If people have to guess how your API behaves, the design is not finished."
