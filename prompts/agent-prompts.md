# Agent Prompts

Use these prompts when asking coding agents to generate HTML/CSS/JS for GC experiments, merchandising surfaces, or low-governance implementation environments.

## General UI Prompt

```text
Build this using the Guitar Center Rhythm Web design system.

Before writing code, identify the nearest valid Rhythm pattern and implement from that pattern rather than from raw visual appearance.

Priority order:
1. Reuse an existing documented component or variant
2. Else compose from approved Rhythm primitives
3. Else reuse the closest existing repo pattern
4. Else stop short of invention and clearly label the mismatch

Rules:
- Prefer semantic tokens over primitive values
- Do not introduce one-off spacing, color, radius, border, or typography values
- Do not create new variants, props, abstractions, or wrappers unless explicitly requested
- Do not copy unsupported visual details literally if they are not backed by the system
- Choose the most conservative system-consistent solution when guidance is incomplete

Output:
- Brief mapping summary
- Any mismatch or assumption
- Final implementation
```

## Experiment Prompt

```text
Generate copy-pasteable HTML, CSS, and JS for a low-governance environment such as Monetate.

Before writing code, identify the nearest valid Rhythm pattern and implement from that pattern rather than from raw visual appearance.

Priority order:
1. Reuse an existing documented Rhythm pattern that can work without framework dependencies
2. Else compose from approved tokens and simple portable primitives
3. Else use the closest conservative repo pattern that can survive a hostile host page
4. Else stop short of invention and clearly label the mismatch

Constraints:
- Do not assume React, build tooling, module imports, or design-system runtime dependencies
- Keep the implementation portable, self-contained, and safe to embed in an existing page
- Prefer documented tokens and patterns over arbitrary values
- Avoid inventing new component variants or snowflake visual solutions
- Minimize risk of host-page CSS and JS collisions
- Preserve accessibility and interaction clarity within the limits of the environment

Mismatch behavior:
- If the environment cannot support a documented pattern exactly, use the closest conservative system-consistent implementation
- Label the gap instead of faking parity

Output:
- Brief mapping summary
- Any environment limitation or mismatch
- Final copy-pasteable implementation
```

## Refactor Prompt

```text
Refactor this markup toward the GC Rhythm Web system.

Before writing code, identify the nearest valid Rhythm pattern and implement from that pattern rather than from raw visual appearance.

Goals:
- Replace arbitrary values with documented tokens or approved system patterns
- Preserve existing user-facing behavior
- Reduce design drift without redesigning the experience

Rules:
- Prefer semantic tokens over primitive values
- Reuse existing Rhythm component patterns before introducing new structure
- Do not redesign layout, hierarchy, or interaction unless explicitly asked
- Do not preserve incidental markup if it conflicts with stronger system alignment
- Do not introduce new variants, abstractions, or one-off styling

Output:
- Short summary of what changed
- Any behavior or structure intentionally preserved
- Any unresolved mismatch
- Refactored markup
```

## Optional Suffixes

Use these as add-ons when a task needs extra control without expanding the base prompt too much.

### Mapping Suffix

```text
First, identify:
- the nearest valid component or pattern
- the tokens to use
- any unsupported details to ignore
```

### Safety Suffix

```text
Do not invent new variants, tokens, APIs, or wrappers unless explicitly requested.
```

### Environment Suffix

```text
Assume this will run in a hostile existing page with unknown CSS and JS. Avoid fragile selectors, leaky styles, and unnecessary dependencies.
```
