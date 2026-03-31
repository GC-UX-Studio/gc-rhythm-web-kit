# Agent Prompts

Use these prompts when asking coding agents to generate HTML/CSS/JS for GC experiments, merchandising surfaces, or low-governance implementation environments.

## General UI Prompt

```text
Build this using the Guitar Center Rhythm Web design system. Prefer documented semantic tokens over arbitrary values. Reuse existing component patterns before inventing new ones. Do not introduce one-off spacing, colors, radii, or typography. If guidance is missing, choose the most conservative system-consistent option and label any unresolved gap.
```

## Experiment Prompt

```text
Generate copy-pasteable HTML/CSS/JS for a low-governance environment such as Monetate. Use Rhythm Web styling conventions, semantic tokens, and existing component behavior. Avoid framework-specific assumptions and avoid snowflake visual solutions.
```

## Refactor Prompt

```text
Refactor this markup toward the GC Rhythm Web system. Replace arbitrary values with documented tokens, preserve the existing behavior, and minimize design drift. Do not redesign the experience unless explicitly asked.
```
