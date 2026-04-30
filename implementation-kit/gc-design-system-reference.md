# GC Design System Reference

This document is the implementation-facing reference for the current `Rhythm Web` token export. It is now aligned to `gc-tokens.zip` in the project root instead of older screenshot-based notes.

## Sync Status

- Last verified in repo: `2026-04-20`
- Source export archive: `gc-tokens.zip`
- Export timestamp inside archive: `2026-04-04 04:35`
- Reference status: this markdown file reflects the April 4 export
- Implementation status: [`styles/rhythm-web-tokens.css`](./styles/rhythm-web-tokens.css) still reflects an older token translation and should not be treated as the canonical source for current token names or values

## Source Of Truth

- Token archive: `gc-tokens.zip`
- Export timestamp inside archive: `2026-04-04 04:35`
- Token sets in export order:
  - `Color Primitives/Mode 1`
  - `Color/Light`
  - `Color/Dark`
  - `Components/Mode 1`
  - `Responsive/Mobile`
  - `Responsive/Tablet`
  - `Responsive/Desktop`
  - `Typography Primitives/Mode 1`
  - `Typography/Mode 1`
  - `Size/Mode 1`
- Figma file: [Rhythm Web - Styles](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=3677-1944&t=UAGdfjIM21J8aOTb-1)
- Figma component properties define component existence, variants, sizes, states, and icon options.
- Token exports define reusable styling values such as color, typography, spacing, radius, stroke, and component tokens.

## How To Use This Doc

- Treat `gc-tokens.zip` and the Figma file as the source of truth.
- Use Figma component properties to validate component variants, sizes, states, and icon options.
- Use the token export to validate reusable styling values.
- Prefer semantic tokens before primitive tokens.
- Component tokens override semantic tokens when both apply.
- Prefer component tokens before inventing one-off component values.
- Tokens do not have to define every valid component variant.
- Do not require a component-specific token for an intentionally absent value. If a Figma component variant intentionally has no fill, no border, or no icon, map that to transparent, none, native HTML behavior, or markup structure instead of inventing a new token.
- Do not rely on older names from prior docs when a different exported token name exists now.
- If a value is shown here as a token reference, preserve that indirection in implementation when possible.

## Implementation Decision Hierarchy

When implementing UI in this repo:

1. Use an existing component variant, size, state, or icon option when it exists as a Figma component property or in code.
2. Else compose from approved primitives and documented tokens for reusable styling values.
3. Else reuse an existing repo pattern.
4. Else stop and report the mismatch.

Never:

- create new component variants
- introduce new tokens
- derive implementation values directly from raw Figma primitives when a system mapping exists
- invent new APIs or props just to match a one-off design detail

## Figma Interpretation Rules

Figma expresses visual intent, not literal implementation structure.

Do not implement literally:

- arbitrary spacing values
- raw hex values
- frame nesting
- layer naming
- one-off shadows or radii

Always map Figma output to:

- component properties for variants, sizes, states, and icon options
- component tokens first
- semantic tokens second
- approved primitives only when no higher-level token applies

## Invention Policy

The agent must not:

- create new component variants
- define new tokens
- introduce new props or APIs to support one-off styling
- create custom responsive role names that duplicate exported responsive aliases

If no exact mapping exists:

- use the closest valid system pattern
- document the mismatch explicitly
- do not invent a new system concept to close the gap

## Required Implementation Process

1. Identify the component type and nearest valid variant, size, state, and icon option from Figma component properties or code.
2. Map styling values to component tokens, semantic tokens, or approved primitives.
3. Identify intentional absences such as no fill, no border, or no icon.
4. Identify which Figma details should be ignored because they are not system-backed.
5. Implement using the closest valid system-compliant pattern.
6. Validate before finalizing.

## Mismatch Handling

If a design does not map cleanly:

1. Select the nearest valid system pattern.
2. Do not invent a new structure, token, variant, or API.
3. Document the difference between the design and the system-backed implementation.
4. Continue with the system-compliant implementation unless the mismatch blocks usability or correctness.

## Validation Checklist

Before finalizing implementation, confirm:

- components, variants, sizes, states, and icon options exist in Figma component properties or the code contract
- no hardcoded values are used where a documented token exists
- component tokens are used before semantic tokens when both apply
- semantic tokens are used before primitives when both apply
- intentionally absent fills, borders, or icons are represented as absence instead of invented tokens
- no new variants, tokens, or one-off APIs were introduced
- typography uses role tokens and responsive aliases instead of hardcoded breakpoint-specific sizes
- implementation follows existing repo patterns where available

If any item fails, revise once before final output.

## Anti-Patterns

Do not:

- recreate Figma structure literally
- introduce slight variations of existing components
- hardcode spacing or typography values when tokens exist
- create single-use wrapper components just to preserve a one-off frame structure
- derive tokens from raw values instead of mapping to an existing system token

## Decision Examples

### Example: Button From Figma

Figma shows:

- `18px` horizontal padding
- a custom shadow

Correct implementation:

- use the nearest spacing token such as `space-16` or `space-20` based on the existing button pattern
- ignore the shadow unless and until shadow tokens are exported

Why:

- spacing must align to the documented scale
- elevation is not yet tokenized in the export

### Example: Heading At Desktop

Figma shows:

- a larger desktop heading size
- a smaller mobile heading size

Correct implementation:

- use the matching role token such as `Heading.size-base` or `Heading.size-large`
- do not hardcode separate mobile and desktop font-size values

Why:

- responsive aliases already encode the breakpoint behavior
- role tokens are the semantic entry point for implementation

### Example: Card Surface

Figma shows:

- a card with a subtle background and rounded corners
- a radius that looks visually close to `6px`

Correct implementation:

- use `bg-subtle` or the nearest documented surface token
- use `radius-large` for the card unless the component reference shows a specific override

Why:

- cards are currently treated as compositions, not a fully tokenized component family
- implementation should stay on the documented radius scale instead of copying visual approximation

## What Changed In This Sync

- Re-verified the reference against the checked-in April 4 export on `2026-04-17`.
- Added an explicit note that this document is newer than the generated CSS token file.
- Token sections are now based on the exported JSON, not inferred screenshots.
- Color semantics now reflect both `Light` and `Dark` modes.
- Size tokens now include the missing `space-28`, `space-36`, `stroke-small`, and `stroke-base` entries.
- Component token names now match the export, including `text-promotion`, `border-default`, and `text-action-*`.
- Responsive guidance now reflects the exported `Mobile`, `Tablet`, and `Desktop` sets instead of the older `sm` through `2xl` framing.

## Current Repo Drift

The April 4 export and the checked-in CSS token file are not in the same state right now.

| Area | Export / Reference | Current CSS File |
| --- | --- | --- |
| Link token naming | `text-link`, `text-link-hover` | `--gc-text-link-active`, `--gc-text-link-hover` |
| Status token naming | `text-success`, `text-warning`, `text-danger` | `--gc-text-status-positive`, `--gc-text-status-neutral`, `--gc-text-status-error` |
| Promotion token naming | `text-promotion` | `--gc-text-sale` |
| Background token naming | `bg-subtle`, `bg-strong` | `--gc-bg-container`, `--gc-bg-product` |
| Border token naming | `border-default`, `border-divider` | `--gc-border-container`, `--gc-border-divider` |
| Responsive typography scale | Mobile / Tablet / Desktop aliases from export | Static `--gc-text-size-*` values from an older scale |
| Spacing scale | Includes `space-28` and `space-36` | Omits both tokens |

Treat this document and `gc-tokens.zip` as canonical until the CSS file is regenerated or manually brought forward.

## Token Naming Notes

- Exported color family names use title case, for example `Gray.600` and `Red.200*`.
- Exported semantic color tokens use kebab case, for example `text-primary` and `bg-subtle`.
- The `*` in `Red.200*` is part of the exported token name.
- The export includes `Light` and `Dark` token sets, but `$themes.json` is empty. Mode mapping is therefore documented by token set, not by a separate theme file.

## Semantic Tokens

### Color Semantics

| Token | Light | Dark | Web Variable | Notes |
| --- | --- | --- | --- | --- |
| `text-primary` | `Gray.600` | `Gray.white` | `var(--text-primary)` | Primary text |
| `text-secondary` | `Gray.500` | `Gray.400` | `var(--text-secondary)` | Secondary text |
| `text-disabled` | `Gray.400` | `Gray.500` | `var(--text-disabled)` | Disabled text |
| `text-inverse` | `Gray.white` | `Gray.600` | `var(--text-inverse)` | Inverse text |
| `text-link` | `Blue.300` | `Blue.300` | `var(--text-link)` | Default link |
| `text-link-hover` | `Blue.400` | `Blue.400` | `var(--text-link-hover)` | Hover link |
| `text-success` | `Green.200` | `Green.200` | `var(--text-success)` | Success text |
| `text-warning` | `Orange.300` | `Orange.300` | `var(--text-warning)` | Warning text |
| `text-danger` | `Red-Orange.300` | `Red-Orange.300` | `var(--text-danger)` | Danger or error text |
| `text-promotion` | `Red.200*` | `Red.200*` | `var(--text-promotion)` | Promotional text |
| `bg-primary` | `Gray.white` | `Gray.600` | `var(--bg-primary)` | Primary page or surface background |
| `bg-subtle` | `Gray.50` | `Gray.500` | `var(--bg-subtle)` | Subtle surface |
| `bg-strong` | `Gray.100` | `Gray.400` | `var(--bg-strong)` | Stronger surface |
| `bg-inverse` | `Gray.600` | `Gray.white` | `var(--bg-inverse)` | Inverse background |
| `border-default` | `Gray.300` | `Gray.300` | `var(--border-default)` | Default border |
| `border-divider` | `Gray.300` | `Gray.300` | `var(--border-divider)` | Divider border |

### Component Tokens

#### Button

| Token | Value | Notes |
| --- | --- | --- |
| `Button.bg-action-primary` | `Red.200*` | Primary button background |
| `Button.bg-action-primary-hover` | `Red.300` | Primary hover background |
| `Button.bg-action-secondary` | `Gray.white` | Secondary button background |
| `Button.bg-action-secondary-hover` | `Gray.50` | Secondary hover background |
| `Button.bg-action-tertiary` | `Gray.200` | Tertiary button background |
| `Button.bg-action-tertiary-hover` | `Gray.300` | Tertiary hover background |
| `Button.bg-action-disabled` | `Gray.200` | Disabled button background |
| `Button.border-action-primary` | `Gray.0` | Primary stroke token |
| `Button.border-action-secondary` | `Red.200*` | Secondary stroke token |
| `Button.border-action-secondary-hover` | `Red.300` | Secondary hover stroke |
| `Button.text-action-enabled` | `Red.200*` | Web: `var(--text-btn-enabled)` |
| `Button.text-action-hover` | `Red.300` | Web: `var(--text-btn-hover)` |
| `Button.text-action-disabled` | `text-disabled` | Export also maps this to `var(--text-btn-hover)`; verify if code should keep or correct that |
| `Button.radius` | `radius-base` | Shared corner radius |

#### AI Chip

| Token | Value |
| --- | --- |
| `AI Chip.bg-primary` | `Blue.100` |
| `AI Chip.bg-primary-hover` | `Blue.200` |
| `AI Chip.text-primary` | `Blue.300` |
| `AI Chip.border-primary-hover` | `Blue.400` |
| `AI Chip.text-primary-disabled` | `Blue.0` |
| `AI Chip.bg-secondary` | `Gray.200` |
| `AI Chip.bg-secondary-hover` | `Gray.300` |
| `AI Chip.text-secondary` | `text-secondary` |
| `AI Chip.text-secondary-disabled` | `text-disabled` |
| `AI Chip.border-secondary-hover` | `Gray.600` |
| `AI Chip.icon` | `Gray.500` |
| `AI Chip.icon-disabled` | `Gray.400` |

#### Shared Component Heights

| Token | Value |
| --- | --- |
| `height-small` | `space-28` |
| `height-medium` | `space-36` |
| `height-large` | `space-48` |

### Responsive Tokens

The export currently defines explicit responsive sets for `Mobile`, `Tablet`, and `Desktop`.

| Token | Mobile | Tablet | Desktop | Web Variable |
| --- | --- | --- | --- | --- |
| `device` | `mobile` | `tablet` | `desktop` | `var(--gc-responsive-device)` |
| `breakpoint-width` | `375` | `768` | `1024` | `var(--gc-breakpoint-width)` |
| `margin` | `space-16` | `space-16` | `space-20` | `var(--gc-margin)` |
| `2xl` | `size-22` | `size-22` | `size-24` | `var(--text-2xl)` |
| `3xl` | `size-24` | `size-24` | `size-26` | `var(--text-3xl)` |
| `4xl` | `size-26` | `size-26` | `size-28` | `var(--text-4xl)` |
| `5xl` | `size-28` | `size-28` | `size-32` | `var(--text-5xl)` |
| `6xl` | `size-32` | `size-32` | `size-36` | `var(--text-6xl)` |
| `7xl` | `size-36` | `size-36` | `size-44` | `var(--text-7xl)` |
| `8xl` | `size-44` | `size-44` | `size-58` | `var(--text-8xl)` |
| `leading-2xl` | `leading-28` | `leading-28` | `leading-30` |  |
| `leading-3xl` | `leading-30` | `leading-30` | `leading-32` |  |
| `leading-4xl` | `leading-32` | `leading-32` | `leading-34` |  |
| `leading-5xl` | `leading-34` | `leading-34` | `leading-38` |  |
| `leading-6xl` | `leading-38` | `leading-38` | `leading-42` |  |
| `leading-7xl` | `leading-42` | `leading-42` | `leading-50` |  |
| `leading-8xl` | `leading-50` | `leading-50` | `leading-64` |  |

#### Responsive Typography Interpretation

This is the important implementation detail that is easy to miss when reading the token files in isolation:

- role tokens like `Display.size-*`, `Heading.size-*`, and `Title.size-*` do not include the word `responsive` in their names
- instead, they point to shared scale aliases like `2xl` through `8xl`
- those aliases are the responsive layer
- the active `Responsive/Mobile`, `Responsive/Tablet`, or `Responsive/Desktop` set determines what those aliases resolve to at each breakpoint

In practice, that means responsiveness is carried by the referenced alias, not by the role token name itself.

Examples:

- `Display.size-small -> 6xl`
- `Display.size-base -> 7xl`
- `Display.size-large -> 8xl`
- `Heading.size-small -> 3xl`
- `Heading.size-base -> 4xl`
- `Heading.size-large -> 5xl`
- `Title.size-large -> 2xl`

Those aliases then ladder through the responsive token sets:

- `2xl` resolves to `size-22` on mobile and tablet, then `size-24` on desktop
- `6xl` resolves to `size-32` on mobile and tablet, then `size-36` on desktop
- `8xl` resolves to `size-44` on mobile and tablet, then `size-58` on desktop

This should be read with the same mental model Tailwind uses for responsive typography and layout:

- unprefixed styling is the base or mobile default
- larger breakpoints override that base value
- you should think in terms of `base -> lg+ override`, not separate unrelated token stacks

For Rhythm, that means:

- mobile and tablet usually inherit the same base role size
- desktop introduces the larger override through the `Responsive/Desktop` token set
- the role token stays stable while the referenced alias changes by breakpoint

Developer translation:

- use the role token as the semantic entry point
- let the referenced size alias resolve responsively
- do not create separate ad hoc role names just to express breakpoint changes already encoded in the `Responsive/*` sets

### Typography Semantics

#### Base Semantic Scale

| Token | Value |
| --- | --- |
| `xs` | `size-12` |
| `sm` | `size-14` |
| `base` | `size-16` |
| `lg` | `size-18` |
| `xl` | `size-20` |
| `2xl` | `size-22` |
| `3xl` | `size-24` |
| `4xl` | `size-26` |
| `5xl` | `size-28` |
| `6xl` | `size-32` |
| `7xl` | `size-36` |
| `8xl` | `size-44` |
| `9xl` | `size-58` |
| `leading-xs` | `leading-18` |
| `leading-sm` | `leading-20` |
| `leading-base` | `leading-22` |
| `leading-lg` | `leading-24` |
| `leading-xl` | `leading-26` |

#### Role Tokens

##### Label

| Property | Value |
| --- | --- |
| `family` | `family-sans` |
| `size` | `xs` |
| `weight-medium` | `weight-medium` |
| `weight-bold` | `weight-bold` |
| `leading` | `leading-xs` |
| `single-line` | `leading-12` |

##### Body

| Property | Value |
| --- | --- |
| `family` | `family-sans` |
| `size-small` | `sm` |
| `size-base` | `base` |
| `weight-regular` | `weight-regular` |
| `weight-medium` | `weight-medium` |
| `weight-bold` | `weight-bold` |
| `leading-small` | `leading-sm` |
| `leading-base` | `leading-base` |
| `single-line-small` | `leading-14` |
| `single-line-base` | `leading-16` |

##### Title

| Property | Value |
| --- | --- |
| `family` | `family-sans` |
| `size-small` | `lg` |
| `size-base` | `xl` |
| `size-large` | `2xl` |
| `weight-regular` | `weight-regular` |
| `weight-medium` | `weight-medium` |
| `weight-bold` | `weight-bold` |
| `leading-small` | `leading-lg` |
| `leading-base` | `leading-xl` |
| `leading-large` | `leading-2xl` |

##### Heading

| Property | Value |
| --- | --- |
| `family` | `family-sans` |
| `size-small` | `3xl` |
| `size-base` | `4xl` |
| `size-large` | `5xl` |
| `weight` | `weight-bold` |
| `leading-small` | `leading-3xl` |
| `leading-base` | `leading-4xl` |
| `leading-large` | `leading-5xl` |

##### Display

| Property | Value |
| --- | --- |
| `family` | `family-sans` |
| `size-small` | `6xl` |
| `size-base` | `7xl` |
| `size-large` | `8xl` |
| `weight` | `weight-bold` |
| `leading-small` | `leading-6xl` |
| `leading-base` | `leading-7xl` |
| `leading-large` | `leading-8xl` |

## Primitive Tokens

### Color Primitives

#### Gray

| Token | Value | Notes |
| --- | --- | --- |
| `Gray.0` | `#dddddd99` | Alpha gray |
| `Gray.50` | `#f9f9f9` | Surface fill |
| `Gray.100` | `#f5f5f5` | Surface fill |
| `Gray.200` | `#eeeeee` | Surface fill |
| `Gray.300` | `#dddddd` | Border or subtle fill |
| `Gray.400` | `#bbbbbb` | Border or disabled state |
| `Gray.500` | `#676767` | Secondary neutral |
| `Gray.600` | `#161616` | Primary dark neutral |
| `Gray.white` | `#ffffff` | Inverse text or white surface |

#### Red

| Token | Value | Notes |
| --- | --- | --- |
| `Red.50` | `#fff6f7` | Low-emphasis background |
| `Red.100` | `#ffc8cc` | Medium-emphasis background |
| `Red.200*` | `#ed1c24` | GC Red |
| `Red.300` | `#c9000c` | Hover |

#### Red-Orange

| Token | Value | Notes |
| --- | --- | --- |
| `Red-Orange.50` | `#fff6f5` | Low-emphasis background |
| `Red-Orange.100` | `#ffaa99` | Low-emphasis background |
| `Red-Orange.200` | `#ff5533` | Medium-emphasis background |
| `Red-Orange.300` | `#cc2200` | Hover |

#### Orange

| Token | Value | Notes |
| --- | --- | --- |
| `Orange.50` | `#fffdf5` | Low-emphasis background |
| `Orange.100` | `#fcef93` | Medium-emphasis background |
| `Orange.200` | `#f5b707` | Tertiary color |
| `Orange.300` | `#f17200` | Hover |

#### Green

| Token | Value | Notes |
| --- | --- | --- |
| `Green.50` | `#f5fff5` | Low-emphasis background |
| `Green.100` | `#82cc7a` | Medium-emphasis background |
| `Green.200` | `#1f871c` | Alert color |
| `Green.300` | `#186615` | Hover |

#### Blue

| Token | Value | Notes |
| --- | --- | --- |
| `Blue.0` | `#136ee780` | Alpha blue |
| `Blue.50` | `#f5f9ff` | Low-emphasis background |
| `Blue.100` | `#b9dcff` | Medium-emphasis background |
| `Blue.200` | `#99ccff` | Medium-emphasis background |
| `Blue.300` | `#136ee7` | Secondary color |
| `Blue.400` | `#1e3bb5` | Hover |

### Typography Primitives

| Token | Value |
| --- | --- |
| `family-sans` | `Instrument Sans` |
| `line-height-small` | `100%` |
| `line-height-base` | `120%` |
| `line-height-large` | `140%` |
| `weight-regular` | `400` |
| `weight-medium` | `500` |
| `weight-bold` | `700` |

#### Font Size Primitives

| Token | Value |
| --- | --- |
| `size-12` | `12` |
| `size-14` | `14` |
| `size-16` | `16` |
| `size-18` | `18` |
| `size-20` | `20` |
| `size-22` | `22` |
| `size-24` | `24` |
| `size-26` | `26` |
| `size-28` | `28` |
| `size-32` | `32` |
| `size-36` | `36` |
| `size-44` | `44` |
| `size-58` | `58` |

#### Line Height Primitives

| Token | Value |
| --- | --- |
| `leading-12` | `12` |
| `leading-14` | `14` |
| `leading-16` | `16` |
| `leading-18` | `18` |
| `leading-20` | `20` |
| `leading-22` | `22` |
| `leading-24` | `24` |
| `leading-26` | `26` |
| `leading-28` | `28` |
| `leading-30` | `30` |
| `leading-32` | `32` |
| `leading-34` | `34` |
| `leading-38` | `38` |
| `leading-42` | `42` |
| `leading-50` | `50` |
| `leading-64` | `64` |

### Size Primitives

#### Space

| Token | Value | Web Variable |
| --- | --- | --- |
| `space-2` | `2` | `var(--gc-space-2)` |
| `space-4` | `4` | `var(--gc-space-4)` |
| `space-8` | `8` | `var(--gc-space-8)` |
| `space-12` | `12` | `var(--gc-space-12)` |
| `space-16` | `16` | `var(--gc-space-16)` |
| `space-20` | `20` | `var(--gc-space-20)` |
| `space-24` | `24` | `var(--gc-space-24)` |
| `space-28` | `28` | `var(--gc-space-28)` |
| `space-32` | `32` | `var(--gc-space-32)` |
| `space-36` | `36` | `var(--gc-space-36)` |
| `space-40` | `40` | `var(--gc-space-40)` |
| `space-48` | `48` | `var(--gc-space-48)` |
| `space-56` | `56` | `var(--gc-space-56)` |
| `space-64` | `64` | `var(--gc-space-64)` |
| `space-72` | `72` | `var(--gc-space-72)` |
| `space-80` | `80` | `var(--gc-space-80)` |
| `space-96` | `96` | `var(--gc-space-96)` |
| `space-112` | `112` | `var(--gc-space-112)` |

#### Radius And Stroke

| Token | Value | Web Variable |
| --- | --- | --- |
| `radius-small` | `2` | `var(--radius-small)` |
| `radius-base` | `4` | `var(--radius-base)` |
| `radius-large` | `6` | `var(--radius-large)` |
| `radius-full` | `48` | `var(--radius-full)` |
| `stroke-small` | `1` | `var(--stroke-small)` |
| `stroke-base` | `2` | `var(--stroke-base)` |

## Implementation Guidance

### Token Discipline

- Use semantic color tokens for UI work before reaching for primitive colors.
- Use component tokens before semantic tokens when both apply to the same property.
- Use the responsive token sets for typography shifts instead of inventing extra breakpoints.
- Use `radius-base` for buttons and `radius-large` for cards or larger surfaces unless Figma shows a specific override.
- Preserve the exported naming exactly in docs and code comments.

### Typography Guidance

- `Instrument Sans` is the exported family token for all documented roles.
- `Label`, `Body`, and `Title` support multiple weights.
- `Heading` and `Display` are exported as bold-only roles.
- Display sizing is split into `small`, `base`, and `large`, not ad hoc marketing sizes.
- The responsive aliases in this document are source-backed; do not infer typography values from the current CSS file where those values disagree.
- Do not hardcode breakpoint-specific font sizes; use role tokens and let responsive aliases resolve automatically.

### Known Notes

- `Gray.0` and `Blue.0` are alpha tokens, not normal opaque scale steps.
- The export has no dedicated elevation token set yet.
- The export has no separate theme file content beyond the `Light` and `Dark` token sets themselves.
- `Button.text-action-disabled` currently points to `text-disabled` but exposes the same web variable string as hover in the export. Treat that as a source-backed quirk worth verifying before implementation changes.
- `styles/rhythm-web-tokens.css` in `implementation-kit/styles/` appears to predate this export and should be updated in a separate pass.

## Component Reference Still Useful From Figma

These patterns are not fully described by the token export alone, so the Figma component pages are still the reference for anatomy and variant coverage.

### Button

Source: [Button (WIP)](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=10011-9015&t=UAGdfjIM21J8aOTb-1)

- Variants shown: `Primary`, `Secondary`, `Tertiary`
- Sizes shown: `Large`, `Medium`, `Small`
- States shown: `Enabled`, `Hover`, `Disabled`, `Focused`
- Icon positions shown: `None`, `Leading`, `Trailing`
- Shared tokenized height values align to `height-large`, `height-medium`, and `height-small`

### Card

Source: [Card](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=2699-18290&t=UAGdfjIM21J8aOTb-1)

- The token export does not provide a dedicated card token set.
- Continue treating cards as a family of compositions rather than a single component.
- Use `radius-large` as the default card radius unless a Figma variant specifies otherwise.

## Current Gaps

- Elevation is still undefined in the token export.
- Card-specific semantic tokens are not exported yet.
- `$themes.json` is empty, so theme wiring must be inferred from token set names.
- Component behavior, interaction rules, and layout anatomy still need to be validated in Figma frames, not from tokens alone.
