# OPERATIONAL GUIDELINES

## Workflow

- After work done,
  - Review the entire change set, rethink if the implementation can be further simplified or improved, and make necessary adjustments.
  - Ensure all new code is properly documented, including function/component purposes and any complex logic.
  - Check diagnostics and resolve all errors.
  - When diagnostics include clearly safe and relevant fixes, apply them directly without asking the same confirmation question again.
  - Include a draft commit message, following the Conventional Commits format. The message should be in English and wrapped in a code block.

## Development Guidelines

### Thinking Principles

- **Simplicity First**: Strive for simplicity in both design and implementation. **Think, design, and plan with an MVP mindset.** Avoid over-engineering.
- **Think Beyond**: Shift perspective from "how" to "why". Deeply analyze the underlying **business motivations**, **performance implications**, and edge cases. **Avoid passive execution**—proactively propose optimized solutions or alternatives and seek confirmation if the original request can be improved.
- **Design for Evolution**: Adhere to **High Cohesion and Low Coupling**. Build modular components with clear abstractions and boundaries (following SOLID principles). Ensure code is readable, maintainable, and extensible, **not merely functional**.

### Coding Style

- **Limit Indentation**: Aim for a maximum of 6 indentation levels. Utilize local variables or extract functions to achieve this.
- **Extract Content**: Move large inline strings (e.g., prompts, templates, constants) into dedicated utility functions for readability.
- **Delegate Formatting**: Do NOT fix formatting or indentation issues; these will get handled by specialized tools.
- **CSS-first UI Effects**: Prefer CSS-driven UI effects and styling over JavaScript when feasible to reduce JS code complexity.

### TypeScript / React Requirements

- **Language**: Use **TypeScript**. Avoid `any` where possible. Enable `"strict": true`.
- **Style**: Use a no-semicolon style.
- **CSS-in-JS**: Use styled-jsx for React components, no tailwind.
- **Complexity**: Avoid using ternary operators with more than three lines, use local components or functions to simplify.
- **Local Components**: Define and use local components within the same file if only used by the parent.
- **No example files**: Do not create example files, just output the usage example in chat for newly created api/components.
- Prefer type-safe alternatives (like type guards or generics) over as (type assertion); use as only when you are certain of the type and no safer typing mechanism is available, typically for interoperability with untyped code or when TypeScript's inference is insufficient.

### Documentation Requirements

- Document component/function purposes, avoid comments that merely describe current change (e.g., "Import X, Add Y, Update Z").
- For TypeScript type annotations, use the single-line format (/\*\* \*/) whenever possible.
- Use TSDoc comments for exported items (`@param`, `@returns`, etc.).
- Keep comments and `README.md` updated.
- Use English.

### Use Latest Language / Framework Features

- Nodejs builtin test runner (https://nodejs.org/api/test.html)
- React 19 features (actions, use, ref as props)
- TypeScript features (template literal types, conditional types, etc.)
- Latest JavaScript features (`??=`, `||=`, `?.`, `?.[]`, etc.)
  - ES2023 (Array.groupBy, Array.groupByToMap, Array.toSorted, Array.toReversed, Array.toSpliced, Array.with)
  - ES2024 (Atomic waitSync, Top-level await, Decorators, Temporal API)
- Chrome features (new APIs, improved performance, etc.)
  - Responsive Design: Container Queries, Style Queries, Logical Properties
  - Animation & Transitions: Scroll-driven Animations, View Transitions, Cross-document View Transitions
  - UI Components: Popover API, Anchor Positioning, position-area
  - CSS Features: Relative Color, Custom Properties, CSS if() function

When in doubt, check the reference documentation:

- React 19 (actions, use, ref as props)
  - https://react.dev/blog/2024/12/05/react-19
- ES 2023 (Array.groupBy(), Array.groupByToMap(), Array.toSorted(), Array.toReversed(), Array.toSpliced(), Array.with())
  - https://medium.com/@dhrumitpatell/a-complete-guide-to-javascript-es2023-features-and-enhancements-520f42213131
- ES 2024 (Atomic waitSync, Top-level await, Decorators, Temporal API)
  - https://dev.to/hkp22/unwrapping-javascript-es2024-key-features-every-developer-should-know-46c8
- Chrome
  - https://developer.chrome.com/blog/new-in-web-ui-io-2024
  - https://web.dev/blog/whats-new-in-web-io2025
  - https://developer.chrome.com/blog/web-at-io25

## Commit Message Guidelines (for generated commits)

- Use Conventional Commit prefixes (`feat:`, `fix:`, `chore:`, etc.).
- Keep the subject to one line, <= 50 characters, and focus on the key change.
- For small/simple diffs: a single concise subject is enough; omit trivial details.
- For large/complex changes (>300 lines): include a short body (max 3 bullets), wrap at
  72 characters per line.

## How to write technical design

The structure of a technical design document should be like a three-layer onion. The first layer includes the problem statement, goals, non-goals, and both functional and non-functional requirements. The second layer is the functional specification, detailing how the system will work from an external perspective. The third and final layer is the technical specification, describing the internal workings of the system. Each section must flow logically from the previous one to ensure the document is coherent and comprehensive.

It's crucial to address any flaws in the earlier sections before moving forward. If the problem statement is incorrect, the functional spec will likely be flawed. Similarly, if the functional spec does not meet the requirements, the implementation will be ineffective. Each layer must build upon and justify the previous one, ensuring that the entire design addresses the initial problem comprehensively.

Many technical design documents fail by presenting only the final technical specification, making it difficult for reviewers to provide meaningful feedback. The document should outline the various choices considered and justify the final decisions made. The design process involves selecting among different possibilities, and a well-structured design document will clearly explain the alternatives considered and the rationale behind the chosen solutions.
