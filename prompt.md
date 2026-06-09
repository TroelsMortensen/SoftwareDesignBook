I need to write a new chapter about the Functional Core Imperative Shell architectural style.

There is a folder for this chapter in the parts/architectural-styles/functional-core-imperative-shell folder, it contains a .tex file.

I have also included a file with sources for this chapter in the parts/architectural-styles/functional-core-imperative-shell/Sources.md file. Do explore these sources, and use them to write the chapter.

I need initially a brief introduction to some functional programming concepts, before we dive into the Functional Core Imperative Shell architectural style.

I need definitions for the following terms:
- Functional Programming
- Imperative Programming
- Honest functions
- Impure and pure functions
- Immutable and mutable data
- Side effects
- How to apply these ideas in Java

I want to use an example based on the Abyssal Watch case study for the book. It should be an example, which highlights the benefits of the Functional Core Imperative Shell architectural style. I think this works best with data transformations, or calculations, and such, where functional programming concepts shine.

I need pros and cons, like in the other chapters.

Use the dirtree for package layout diagrams.

Include placeholder images where relevant, and add a latex todo command (see the main.tex) to remind to add the images later.

I need examples of when this architectural style is beneficial, and when it is not.

I need an explanation of the "imperim sandwich", with a diagram (or placeholder image) to illustrate the concept.


You may find further inspiration from the following conversation:

The "Functional Core, Imperative Shell" (also known as the "Functional Shell, Imperative Core" pattern, though the former is the standard terminology) is a software architecture pattern designed to maximize the testability and maintainability of code. It achieves this by strictly separating business logic—which is kept pure and deterministic—from the side-effect-heavy infrastructure code.

This pattern is a foundational concept in modern software architecture, popularized largely by Gary Bernhardt in his influential "Boundaries" talk.

Core Concept: The Separation
The pattern divides your system into two distinct zones:

1. The Functional Core
This is where your business rules live.

Pure Functions: Methods or functions that take inputs and return outputs without modifying any external state.

Deterministic: Given the same input, they always produce the same output.

No Side Effects: They do not talk to databases, APIs, file systems, or change global variables.

Highly Testable: Because they have no dependencies, you can write unit tests that cover complex logic without needing mocks or stubs.

2. The Imperative Shell
This is the "glue" that interfaces with the outside world.

Side-Effect Heavy: This layer performs the "impure" tasks: fetching data from a database, calling an API, reading a configuration file, or updating a UI.

Orchestration: It gathers the necessary data, calls the functions in the Functional Core, and takes the resulting data to update the state of the system or return a response.

Minimal Logic: The goal is to keep this layer as thin as possible. If it contains complex conditional logic or calculations, that logic should be refactored into the Core.

Why Use This Architecture?
Benefit	Description
Testability	You can test 90% of your complex business logic using simple, fast unit tests without complex setup.
Maintainability	When business rules change, you modify the Core, confident that it won't break your external integrations.
Readability	It forces a clean separation of concerns. You don't have to parse database calls to understand the business logic.
Concurrency	Since the core is pure and avoids shared mutable state, it is naturally safer in concurrent environments.
Conceptual Flow
The flow of a request in this architecture usually follows a predictable three-step pattern:

Read (Imperative): The shell fetches data from the outside world (Database, API, User input).

Process (Functional): The shell passes that data into the functional core. The core calculates the result (e.g., a new state, a decision, or a transformation).

Write (Imperative): The shell takes the result from the core and performs the necessary side effects (e.g., saving to the DB, rendering a screen).

A Simple Example (Pseudocode)
Imperative Shell (The "Dirty" Part):

Python
def process_order(order_id):
    # Fetch from database (Side effect)
    order = db.find(order_id)
    
    # Call the Functional Core
    new_status = calculate_next_status(order.status, order.amount)
    
    # Save to database (Side effect)
    db.update_status(order_id, new_status)
Functional Core (The "Pure" Part):

Python
def calculate_next_status(status, amount):
    # Pure logic: No DB access, just math and conditionals
    if status == 'PENDING' and amount > 100:
        return 'REVIEW_REQUIRED'
    return 'APPROVED'
Implementation Tips for Students
Don't Pass Objects: In the Functional Core, prefer passing simple data structures (DTOs, dictionaries, or records) rather than complex objects that might have methods that trigger side effects.

The "Push" Rule: Try to push all decision-making logic out of the shell and into the core. If you find an if statement in your shell, ask yourself: "Can this be calculated by a pure function?"

Language Agnostic: While this pattern shines in functional languages (like Haskell or Elixir), it is incredibly effective in object-oriented languages like Java, C#, or Python, where it helps keep "fat services" from becoming unmaintainable.

Would you like me to expand on how to apply this pattern specifically to a particular programming language, or perhaps discuss the trade-offs when dealing with large, legacy codebases?