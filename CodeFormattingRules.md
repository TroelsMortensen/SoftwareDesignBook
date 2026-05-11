# Code Formatting Rules for PDF Listings

These rules are optimized for Java snippets rendered in LaTeX/PDF where
line numbers and code box width can cause awkward auto-wrapping.

## 1) Line Length and Wrapping Strategy

- Hard maximum: 65 characters per line.
- Soft maximum: 55 to 60 characters; proactively wrap before hitting 65.
- Never rely on automatic PDF line wrapping for readability.
- Prefer "narrow and tall" code over dense horizontal code.

## 2) Indentation and Spacing

- Use 4 spaces per indentation level (no tabs).
- Continuation lines get one extra indent level (+4 spaces).
- Use one blank line between logical phases in a method body.
- Keep one statement per line.

## 3) Braces and Block Shape

- Use Allman style everywhere:
  - Classes/interfaces/enums
  - Methods/constructors
  - if/else, loops, switch, try/catch/finally
- Always use braces for control flow blocks, even single-line bodies.

## 4) Declarations and Signatures

- If a class declaration is long, break before `implements`/`extends`.
- One field declaration per line.
- If field type + name is long, split type and name across lines.
- For method signatures:
  - If more than one parameter, or one long parameter, use multiline.
  - Put one parameter per line.
  - Put closing `)` on its own line.
- Keep annotations on separate lines above the declaration.

## 5) Method Calls and Chains

- Keep short method calls inline only if comfortably below soft limit.
- For long argument lists:
  - Break after `(`.
  - One argument per line.
  - Closing `)` on its own line.
- For chained calls, break before each dot and align chain segments.

## 6) Assignments and Expressions

- For long assignments, break after `=`.
- For long constructor/factory calls, place arguments vertically.
- For long boolean expressions, wrap across lines consistently
  (prefer breaking before `&&`/`||`).
- Avoid complex ternaries in book snippets; prefer `if/else`.

## 7) Generics and Complex Types

- Keep simple generics inline (`List<String>`).
- For complex nested generics, break inside `<...>` at comma boundaries.
- If needed, simplify shown type shapes to improve pedagogical readability.

## 8) Lambdas and Functional Style

- Keep tiny single-expression lambdas inline.
- For non-trivial lambdas, use block form with normal brace rules.
- Prefer method references when they reduce visual noise.

## 9) Comments and Teaching Clarity

- Comments explain intent ("why"), not syntax ("what").
- Use short phase comments before non-obvious logic sections.
- Group method body into readable chunks:
  - Load/validate
  - Build object
  - Persist
  - Publish/integrate
  - Return

## 10) Imports and Member Ordering (Full-File Snippets)

- Import grouping:
  - JDK imports
  - Third-party imports
  - Project imports
- Sort imports alphabetically within each group.
- Class member order:
  - Constants
  - Fields
  - Constructors
  - Public methods
  - Protected/package methods
  - Private helpers

## 11) PDF-Specific Safety Rules

- Manually split long literals (URLs, SQL, JSON, regex) for readability.
- Avoid "almost too long" lines; small edits can trigger ugly auto-wrap.
- Re-check visual output in PDF after formatting changes.

## 12) Quick Decision Checklist

For each line/snippet, ask:

1. Is this line over 55 characters?
2. Is this a signature, declaration, call, or chain that can be verticalized?
3. Will this render cleanly with line numbers in the PDF box?
4. Are logical steps separated with blank lines?
5. Would a new reader parse this in one pass?