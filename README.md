# GC Rhythm Web Kit

Toolkit for turning Figma and agent-assisted implementation into Rhythm Web-aligned output without drifting from the design system.

## What This Repo Is For

- Give pseudo-developers and implementation partners a fast path to Rhythm Web-aligned output
- Reduce design drift in low-governance environments like experiments, merchandising tools, and embedded surfaces
- Host lightweight workflow tools that help teams move from Figma inspection to system-aligned code generation

## Two Tracks

### Implementation Kit

The implementation kit is the system-facing part of the repo. It centers on the design-system reference and everything that helps people or agents produce compliant code.

- [`implementation-kit/gc-design-system-reference.md`](./implementation-kit/gc-design-system-reference.md): source-backed design-system contract for Rhythm Web tokens, components, and implementation rules
- [`implementation-kit/styles/`](./implementation-kit/styles/): shared CSS token and baseline style files
- [`implementation-kit/prompts/`](./implementation-kit/prompts/agent-prompts.md): starter prompts for codegen agents
- [`implementation-kit/snippets/`](./implementation-kit/snippets/README.md): copy-paste UI patterns for low-governance implementation environments
- [`AGENTS.md`](./AGENTS.md): repo-wide agent guidance for staying inside Rhythm constraints

### Hosted Tools

The hosted-tools track contains workflow surfaces that help teams operate the implementation kit.

- [`hosted-tools/figma-node-to-code/`](./hosted-tools/figma-node-to-code/index.html): source for the Figma node to code workflow playbook
- [`docs/figma-node-to-code/`](./docs/figma-node-to-code/index.html): GitHub Pages-ready published copy of that playbook
- [`docs/index.html`](./docs/index.html): redirect entry point for the published Pages site

## GitHub Pages

This repo uses the `docs/` folder as the GitHub Pages output only. Treat `hosted-tools/` as the editable source for hosted workflow surfaces and `docs/` as the published static copy.

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
