<details>
<summary>Example prompt if you are stuck</summary>

You are a senior frontend architect performing a deep architectural review.

I will provide:

- A repository structure (folders/files)
- Key configuration files (package.json, tsconfig, vite/webpack config, etc.)
- Selected representative source files
- Optional: README, ADRs, documentation

Your task is to produce a structured architectural assessment.

## 1. Architectural Overview

- Identify the architectural style (e.g. layered, feature-based, domain-driven, component-driven, micro-frontend, etc.)
- Determine implicit boundaries (features, domains, technical layers)
- Describe dependency direction and coupling patterns
- Identify the state management approach and data flow model
- Evaluate how side effects are handled

Be explicit. If something is unclear, state assumptions.

## 2. Critical Architectural Topics

Evaluate and rate (Low / Moderate / High Risk):

### A. Modularity

- Are modules cohesive?
- Are boundaries enforced?
- Is there cross-feature leakage?
- Are shared modules well-defined or chaotic?

### B. Dependency Management

- Circular dependencies?
- UI → domain → infrastructure separation?
- Inversion of control or tight coupling?

### C. State Management

- Centralized vs distributed?
- Predictable data flow?
- Hidden mutable state?

### D. Scalability

- Can new features be added without modifying unrelated areas?
- Is there a clear extension mechanism?
- Are abstractions reusable or duplicated?

### E. Testability

- Separation of concerns?
- Mocking boundaries?
- Side-effect isolation?

### F. Build & Tooling Architecture

- Complexity of config
- Custom tooling vs conventions
- Risk of configuration drift

## 3. Recurring Architectural Patterns

Identify patterns such as:

- Container / Presentational
- Hooks as service layer
- Smart vs dumb components
- Feature folders
- Barrel exports
- Context overuse
- Singleton services
- Global event buses

For each:

- Where it appears
- Whether it is consistently applied
- Whether it is appropriate
- Whether it creates long-term risk

## 4. Architectural Snowflakes

Identify inconsistencies such as:

- Multiple state management paradigms
- One-off abstractions
- Special-case directories
- Custom patterns used in only one feature
- Inconsistent error handling
- Different async handling styles

For each snowflake:

- Where it occurs
- Why it likely emerged
- Whether it is accidental or intentional
- Risk level
- Refactoring recommendation

## 5. Known and Latent Architectural Issues

Identify:

- Hidden coupling
- God components
- Implicit global state
- Side-effect leakage
- Violations of unidirectional data flow
- Boundary erosion
- Abstraction inversion

Classify issues:

- Structural risk
- Maintainability risk
- Performance risk
- Organizational risk

## 6. Architectural Smell Detection

Look for:

- Over-engineering
- Premature abstraction
- Excessive indirection
- Under-abstracted duplication
- Accidental monolith
- Framework lock-in risk

## 7. Long-Term Evolution Assessment

Answer:

- Can this architecture support 2x team size?
- Can this support 3x feature growth?
- Where will entropy accumulate?
- What will break first?

## Output Format

Use:

- Structured sections
- Bullet points
- Clear risk indicators
- No generic advice
- No beginner explanations
- No framework marketing language

Be direct and critical.
Assume the audience is senior engineers.

</details>
