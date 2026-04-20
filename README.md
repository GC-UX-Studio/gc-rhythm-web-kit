# GC Rhythm Web Kit

Starter kit for bringing experiment code, copy-paste implementations, and AI-generated UI closer to the Guitar Center Rhythm Web design system.

## What This Repo Is For

- Give developers a fast path to Rhythm Web-aligned implementation outside governed app surfaces
- Reduce design drift in tools like Monetate and other open-ended environments
- Provide AI agents with system context, token guidance, and copy-pasteable patterns

## Repo Structure

- [`AGENTS.md`](./AGENTS.md): repo-wide implementation guidance for coding agents working against Rhythm Web constraints
- [`docs/gc-design-system-reference.md`](./docs/gc-design-system-reference.md): source-backed reference for tokens, style guidance, and components
- [`styles/rhythm-web-tokens.css`](./styles/rhythm-web-tokens.css): shared CSS custom properties for tokens
- [`styles/rhythm-web-base.css`](./styles/rhythm-web-base.css): baseline styling helpers for non-React environments
- [`prompts/agent-prompts.md`](./prompts/agent-prompts.md): starter prompts for codegen agents
- [`playbooks/figma-node-to-code/`](./playbooks/figma-node-to-code/): static workflow playbook for inspecting Figma nodes and copying prompt snippets into Codex
- [`snippets/`](./snippets): copy-paste UI patterns for low-governance implementation environments

## Operating Principles

- Prefer semantic tokens over primitive values
- Prefer documented components over bespoke constructions
- Avoid arbitrary values and one-off visual solutions
- Treat Figma as the source of truth and this repo as the easiest path to compliant implementation

## First Targets

- Buttons
- Cards
- Promo blocks
- Section shells
- Product merchandising patterns
