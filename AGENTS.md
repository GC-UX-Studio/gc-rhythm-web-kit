# AGENTS

This repo is intended to help implementation agents produce `Rhythm Web`-aligned code with minimal drift.

## Primary References

- Use [`docs/gc-design-system-reference.md`](./docs/gc-design-system-reference.md) as the design-system contract.
- Treat `gc-tokens.zip` as the source-backed token export.
- Do not treat [`styles/rhythm-web-tokens.css`](./styles/rhythm-web-tokens.css) as canonical when it conflicts with the reference doc.

## Required Working Style

For UI implementation tasks:

1. Classify the component or pattern before coding.
2. Map the implementation to existing component tokens, semantic tokens, and approved primitives.
3. Ignore non-system Figma details such as arbitrary spacing, raw hex values, or one-off shadows.
4. Implement the closest valid system-backed pattern.
5. Validate before finalizing.

## Required Output Structure

For substantial UI implementation responses, include:

1. `Mapping`: how the design maps to components, tokens, and existing patterns
2. `Mismatches`: any places where the design and system do not match exactly
3. `Code`: the implementation
4. `Validation`: a short confirmation that tokens, variants, and existing patterns were respected

For small requests, this structure can be compressed, but the same reasoning order should still be followed.

## Non-Negotiables

- Do not invent new tokens.
- Do not invent new component variants.
- Do not introduce one-off props or APIs just to match a single mock.
- Do not hardcode values where a documented token exists.
- Do not recreate Figma structure literally when a simpler system-backed implementation exists.

## When To Escalate

Pause and call out the issue if:

- no existing token or component pattern maps to a required behavior
- the requested design depends on undefined tokens such as elevation
- a system-compliant implementation would materially change usability or meaning
