# GC Rhythm Web Kit

Agent guidance, design tokens, and copy-paste snippets for implementing the GC Rhythm Web design system.

## What This Repo Is For

- Give implementation partners a fast path to Rhythm Web-aligned output
- Prioritize AI agent alignment in low-governance environments like experiments, merchandising tools, and embedded surfaces
- Reduce design drift by centering implementation around the documented Rhythm system instead of one-off visual interpretation

## Implementation Kit

The implementation kit centers on the Rhythm design-system reference and the materials that help people or agents produce compliant implementation quickly.

- [`implementation-kit/gc-design-system-reference.md`](./implementation-kit/gc-design-system-reference.md): source-backed design-system contract for Rhythm Web tokens, components, and implementation rules
- [`implementation-kit/styles/`](./implementation-kit/styles/): shared CSS token and baseline style files
- [`implementation-kit/prompts/`](./implementation-kit/prompts/agent-prompts.md): starter prompts for codegen agents
- [`implementation-kit/snippets/`](./implementation-kit/snippets/README.md): copy-paste UI patterns for low-governance implementation environments
- [`AGENTS.md`](./AGENTS.md): repo-wide agent guidance for staying inside Rhythm constraints

## Figma Node To Code

<a href="https://gc-ux-studio.github.io/gc-rhythm-web-kit/figma-node-to-code/" target="_blank" rel="noopener noreferrer">Hosted site</a>

## Operating Principles

- Prefer semantic tokens over primitive values
- Prefer documented components over bespoke constructions
- Avoid arbitrary values and one-off visual solutions
- Treat Figma and the token export as the source of truth and this repo as the easiest path to compliant implementation

## First Targets

- Buttons
- Cards
- Promo blocks
- Section shells
- Product merchandising patterns
