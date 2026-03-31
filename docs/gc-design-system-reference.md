# GC Design System Reference

This document is a shareable touchpoint for AI agents and teammates working from the Guitar Center `Rhythm Web` Figma file. It is intended to answer three questions quickly:

1. What are the core tokens and semantic mappings?
2. How are style decisions described in Figma?
3. Which component patterns are already documented?

Primary source: [Rhythm Web - Styles](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=3677-1944&t=UAGdfjIM21J8aOTb-1)

## How To Use This Doc

- Treat Figma as the source of truth and this file as an implementation-oriented reference.
- Prefer semantic tokens over primitive values when building UI.
- Use primitive tokens only when defining or extending the system itself.
- When component guidance and token guidance conflict, confirm the latest component frame in Figma.
- Elevation is still being defined and should not be treated as stable.

## Agent Guidance

This section is intended to reduce design drift when AI agents generate UI in open-ended or weakly constrained environments.

### Core Rule

- Default to the GC design system. Do not invent new visual patterns, token values, or component behavior when an existing system pattern can satisfy the need.

### Token Discipline

- Prefer semantic tokens before primitive tokens.
- Do not hardcode arbitrary colors, spacing, radii, font sizes, line heights, or breakpoint values when a documented token exists.
- Do not introduce one-off values unless the task explicitly requires a system extension.
- If a needed token is missing, use the nearest documented system value and clearly mark the gap for follow-up.

### Component Discipline

- Prefer documented components and variants over bespoke UI constructions.
- Reuse existing component anatomy, states, and size patterns before creating new compositions.
- Do not create new variants, states, or interactions unless they are explicitly requested or already present in Figma.
- If a design need falls between two existing patterns, choose the closer system pattern instead of blending multiple patterns into a new snowflake solution.

### Typography Discipline

- Use documented text roles and responsive text mappings.
- Do not invent new type scales, marketing display treatments, or ad hoc font pairings.
- Preserve the existing split between `UI / UX` typography and `Promo / Marketing` typography.
- Use `Instrument Sans` unless a source-backed exception is documented.

### Color Discipline

- Use semantic color roles for UI implementation whenever possible.
- Do not assign colors based on personal preference, generic accessibility heuristics alone, or model-generated aesthetic guesses.
- Do not repurpose status or sale colors for decorative emphasis.
- Treat the palette as a constrained brand system, not an open creative palette.

### Layout And Spacing Discipline

- Use the documented spacing scale and breakpoint ranges.
- Prefer consistent spacing relationships over locally optimized visual tweaks.
- Avoid introducing near-miss spacing values that sit outside the scale.
- Use documented radius mappings for buttons, pills, sections, and cards.

### Decision Rules For Ambiguity

- When guidance is explicit in Figma, follow it.
- When semantic tokens exist but usage is ambiguous, prefer the most conservative system interpretation.
- When no explicit guidance exists, choose the option that introduces the least novelty.
- When novelty is unavoidable, isolate it, name it clearly, and treat it as a proposed extension rather than an established system rule.

### Anti-Drift Rules

- Do not optimize for novelty when consistency is the goal.
- Do not "improve" the design system by silently modernizing, embellishing, or simplifying it.
- Do not replace branded decisions with generic SaaS patterns.
- Do not infer missing guidance from unrelated design systems.
- Do not use arbitrary fallback values that are close to, but different from, documented system values.

### Expected Agent Output

- Generated UI should feel like a continuation of the GC system, not a reinterpretation of it.
- When making choices, agents should be able to trace them back to:
  - a documented token
  - a documented style role
  - a documented component pattern
  - or a clearly labeled gap in the current system

## Source Index

### Core Style Pages

- `Styles`: [3677:1944](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=3677-1944&t=UAGdfjIM21J8aOTb-1)
- `Typography`: [8838:145](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=8838-145&t=UAGdfjIM21J8aOTb-1)
- `Text Variants UI/UX`: [8838:1593](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=8838-1593&t=UAGdfjIM21J8aOTb-1)
- `Text Variants Promo/Marketing`: [8838:2106](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=8838-2106&t=UAGdfjIM21J8aOTb-1)
- `Colors`: [3677:2839](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=3677-2839&t=UAGdfjIM21J8aOTb-1)
- `Radius`: [9216:21272](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=9216-21272&t=UAGdfjIM21J8aOTb-1)
- `Breakpoints`: [10211:2115](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=10211-2115&t=UAGdfjIM21J8aOTb-1)

### Component Pages

- `Button (WIP)`: [10011:9015](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=10011-9015&t=UAGdfjIM21J8aOTb-1)
- `Card`: [2699:18290](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=2699-18290&t=UAGdfjIM21J8aOTb-1)

## System Summary

### Design Intent

- Typography is treated as a core system for readability, hierarchy, and consistency.
- Color is used to reinforce brand identity, interaction feedback, and information hierarchy.
- Rhythm uses a conservative radius system to preserve a sharp branded edge.
- Responsive behavior is breakpoint-driven, with named ranges from `sm` through `2xl`.

### Current Stability

- Typography, colors, radius, breakpoints, and core semantic mappings are documented enough to guide implementation.
- Buttons and cards have useful component documentation, but both should still be verified in Figma during build work.
- Elevation is not yet stable enough to operationalize.

## Tokens

### Semantic Tokens

#### Breakpoints

Source: [Breakpoints](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=10211-2115&t=UAGdfjIM21J8aOTb-1)

| Token | Value | Label |
| --- | --- | --- |
| `sm` | `375` | `SM (Mobile >=375)` |
| `md` | `768` | `MD (Tablet >=768)` |
| `lg` | `1024` | `LG (Desktop >=1024)` |
| `xl` | `1280` | `XL (Desktop >=1280)` |
| `2xl` | `1540` | `2XL (Desktop >=1500)` |

#### Spacing Scale

Note: the original screenshot showed token names only; values are inferred to match the scale names.

| Token | Value |
| --- | --- |
| `0` | `0` |
| `2` | `2` |
| `4` | `4` |
| `8` | `8` |
| `12` | `12` |
| `16` | `16` |
| `20` | `20` |
| `24` | `24` |
| `32` | `32` |
| `40` | `40` |
| `48` | `48` |
| `56` | `56` |
| `64` | `64` |
| `72` | `72` |
| `80` | `80` |
| `96` | `96` |
| `112` | `112` |

#### Semantic Color Mappings

| Token | Primitive Reference |
| --- | --- |
| `text-primary` | `color/gray/600` |
| `text-secondary` | `color/gray/500` |
| `text-disabled` | `color/gray/400` |
| `text-link-active` | `color/blue/200` |
| `text-link-hover` | `color/blue/300` |
| `text-status-positive` | `color/green/200` |
| `text-status-neutral` | `color/orange/300` |
| `text-status-error` | `color/red-orange/300` |
| `text-sale` | `color/red/200*` |
| `text-inverse` | `color/gray/white` |
| `btn-text-hover` | `color/red/300` |
| `btn-text-enabled` | `color/red/200*` |
| `bg-primary` | `color/gray/white` |
| `bg-container` | `color/gray/50` |
| `bg-product` | `color/gray/100` |
| `bg-inverse` | `color/gray/600` |
| `border-container` | `color/gray/300` |
| `border-divider` | `color/gray/300` |

#### Semantic Typography

##### Leading

| Token | Primitive Reference |
| --- | --- |
| `xs` | `text/line-height/18` |
| `sm` | `text/line-height/20` |
| `base` | `text/line-height/22` |
| `lg` | `text/line-height/24` |
| `xl` | `text/line-height/26` |
| `2xl` | `text/line-height/28` |
| `3xl` | `text/line-height/30` |
| `4xl` | `text/line-height/32` |
| `5xl` | `text/line-height/34` |
| `6xl` | `text/line-height/38` |
| `7xl` | `text/line-height/40` |
| `8xl` | `text/line-height/42` |
| `9xl` | `text/line-height/40` |
| `10xl` | `text/line-height/42` |

##### Font Weight

| Token | Primitive Reference |
| --- | --- |
| `regular` | `text/weight/regular` |
| `medium` | `text/weight/medium` |
| `bold` | `text/weight/bold` |
| `black` | `text/weight/black` |

##### Responsive Text

| Token | `sm` | `md` | `lg` | `xl` | `2xl` |
| --- | --- | --- | --- | --- | --- |
| `xs` | `text/size/12` | `text/size/12` | `text/size/12` | `text/size/12` | `text/size/12` |
| `sm` | `text/size/14` | `text/size/14` | `text/size/14` | `text/size/14` | `text/size/14` |
| `base` | `text/size/16` | `text/size/16` | `text/size/16` | `text/size/16` | `text/size/16` |
| `lg` | `text/size/18` | `text/size/18` | `text/size/18` | `text/size/18` | `text/size/18` |
| `xl` | `text/size/20` | `text/size/20` | `text/size/20` | `text/size/20` | `text/size/20` |
| `2xl` | `text/size/22` | `text/size/22` | `text/size/24` | `text/size/24` | `text/size/24` |
| `3xl` | `text/size/24` | `text/size/24` | `text/size/26` | `text/size/26` | `text/size/26` |
| `4xl` | `text/size/26` | `text/size/26` | `text/size/28` | `text/size/28` | `text/size/28` |
| `5xl` | `text/size/28` | `text/size/28` | `text/size/32` | `text/size/32` | `text/size/32` |
| `6xl` | `text/size/32` | `text/size/32` | `text/size/36` | `text/size/36` | `text/size/36` |
| `7xl` | `text/size/34` | `text/size/34` | `text/size/44` | `text/size/44` | `text/size/44` |
| `8xl` | `text/size/36` | `text/size/36` | `text/size/58` | `text/size/58` | `text/size/58` |
| `9xl` | `text/size/34` | `text/size/34` | `text/size/44` | `text/size/44` | `text/size/44` |
| `10xl` | `text/size/36` | `text/size/36` | `text/size/58` | `text/size/58` | `text/size/58` |

### Primitive Tokens

Note: primitive extraction is partial and based on Variables screenshots shared in this workspace.

#### Color Primitives

##### `color / gray`

| Token | Value |
| --- | --- |
| `white` | `hsba(0, 0%, 100%, 1)` |
| `50` | `hsba(0, 0%, 98%, 1)` |
| `100` | `hsba(0, 0%, 96%, 1)` |
| `200` | `hsba(0, 0%, 93%, 1)` |
| `300` | `hsba(0, 0%, 87%, 1)` |
| `400` | `hsba(0, 0%, 73%, 1)` |
| `500` | `hsba(0, 0%, 40%, 1)` |
| `600` | `hsba(0, 0%, 9%, 1)` |

##### `color / red`

| Token | Value |
| --- | --- |
| `50` | `hsba(353, 4%, 100%, 1)` |
| `100` | `hsba(356, 22%, 100%, 1)` |
| `200*` | `hsba(358, 88%, 93%, 1)` |
| `300` | `hsba(356, 100%, 79%, 1)` |

##### `color / red-orange`

| Token | Value |
| --- | --- |
| `50` | `hsba(6, 4%, 100%, 1)` |
| `100` | `hsba(10, 40%, 100%, 1)` |
| `200` | `hsba(10, 80%, 100%, 1)` |
| `300` | `hsba(10, 100%, 80%, 1)` |

##### `color / orange`

| Token | Value |
| --- | --- |
| `50` | `hsba(48, 4%, 100%, 1)` |
| `100` | `hsba(53, 42%, 99%, 1)` |
| `200` | `hsba(44, 97%, 96%, 1)` |
| `300` | `hsba(28, 100%, 95%, 1)` |

##### `color / green`

| Token | Value |
| --- | --- |
| `50` | `hsba(120, 4%, 100%, 1)` |
| `100` | `hsba(114, 40%, 80%, 1)` |
| `200` | `hsba(118, 79%, 53%, 1)` |
| `300` | `hsba(118, 79%, 40%, 1)` |

##### `color / blue`

| Token | Value |
| --- | --- |
| `50` | `hsba(216, 4%, 100%, 1)` |
| `100` | `hsba(210, 27%, 100%, 1)` |
| `200` | `hsba(214, 92%, 91%, 1)` |
| `300` | `hsba(228, 83%, 71%, 1)` |

#### Text Primitives

##### `text / size`

| Token | Value |
| --- | --- |
| `12` | `12` |
| `14` | `14` |
| `16` | `16` |
| `18` | `18` |
| `20` | `20` |
| `22` | `22` |
| `24` | `24` |
| `26` | `26` |
| `28` | `28` |
| `32` | `32` |
| `34` | `34` |
| `36` | `36` |
| `44` | `44` |
| `58` | `58` |

##### `text / weight`

| Token | Value |
| --- | --- |
| `regular` | `400` |
| `medium` | `500` |
| `bold` | `700` |
| `black` | `900` |

##### `text / line-height`

| Token | Value |
| --- | --- |
| `12` | `12` |
| `14` | `14` |
| `16` | `16` |
| `18` | `18` |
| `20` | `20` |
| `22` | `22` |
| `24` | `24` |
| `26` | `26` |
| `28` | `28` |
| `30` | `30` |
| `32` | `32` |
| `34` | `34` |
| `36` | `36` |
| `38` | `38` |
| `40` | `40` |
| `42` | `42` |
| `44` | `44` |
| `50` | `50` |
| `58` | `58` |
| `64` | `64` |

#### Element Primitives

##### `element / gap`

| Token | Value |
| --- | --- |
| `2` | `2` |
| `4` | `4` |
| `8` | `8` |
| `12` | `12` |
| `16` | `16` |
| `20` | `20` |
| `24` | `24` |
| `32` | `32` |
| `40` | `40` |
| `64` | `64` |
| `128` | `128` |

## Style Guidance

### Typography

Source: [Typography](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=8838-145&t=UAGdfjIM21J8aOTb-1)

- Primary font family is `Instrument Sans`.
- Weight usage is split by domain:
  - `400`, `500`, `700` for `UI / UX`
  - `900` for `Promo / Marketing`
- The type system is split between:
  - a base scale for mobile and tablet
  - larger responsive mappings at `lg`

#### Typography Color Roles

- `primary` -> `text-gray-600`
- `secondary` -> `text-gray-500`
- `disabled` -> `text-gray-400`
- `link-enabled` -> `text-blue-200`
- `link-hover` -> `text-blue-300`
- `error` -> `text-red-orange-300`
- `status` -> `text-green-200`
- `inverse` -> `text-white`

### Text Variants

#### UI / UX

Source: [Text Variants UI/UX](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=8838-1593&t=UAGdfjIM21J8aOTb-1)

Visible role groups:

- `Label`
- `Body Copy`
- `Titles`
- `Headings`

Guidance:

- These are role-based abstractions over the base type scale.
- The page documents size, line height, letter spacing, weight, and color together.
- Some roles have both `Base` and `Large` breakpoint presentations.
- Primary and secondary emphasis are both demonstrated in samples.

#### Promo / Marketing

Source: [Text Variants Promo/Marketing](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=8838-2106&t=UAGdfjIM21J8aOTb-1)

Visible role group:

- `Display`

Guidance:

- Used in promotional hero sections and marketing landing pages.
- The display system is intentionally narrow and centered on large editorial moments.
- All documented examples use:
  - `font-bold` / `700`
  - `text-std-gray-600`
  - width value `75`

Display mapping:

| Breakpoint | Token | Label |
| --- | --- | --- |
| `base` | `text-6xl` | `Small Display` |
| `base` | `text-7xl` | `Medium Display` |
| `base` | `text-8xl` | `Large Display` |
| `lg` | `text-7xl` | `Small Display` |
| `lg` | `text-8xl` | `Medium Display` |
| `lg` | `text-9xl` | `Large Display` |

### Colors

Source: [Colors](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=3677-2839&t=UAGdfjIM21J8aOTb-1)

Visible palette families:

- `Gray`
- `Red`
- `Red-Orange`
- `Orange`
- `Green`
- `Blue`

Guidance:

- `Gray` is the neutral UI and typography scale.
- `Red` includes the GC brand color family.
- `Red-Orange`, `Orange`, `Green`, and `Blue` support status and interaction use cases.

#### Utility Color Roles

Backgrounds:

- `primary`: default background for pages and containers
- `secondary`: hierarchy and emphasis against primary
- `product`: overlay treatment on product images

Borders:

- `container`: separates containers from same-color backgrounds
- `divider`: separates sections when whitespace alone is insufficient

Font colors:

- `primary`
- `secondary`
- `disabled`
- `link-enabled`
- `link-hover`
- `positive`
- `status-info`
- `status-error`
- `error`
- `inverse`

### Radius

Source: [Radius](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=9216-21272&t=UAGdfjIM21J8aOTb-1)

System principle:

- Rhythm uses a conservative radius approach to maintain a branded edge.

Usage mapping:

| Token | Size | Usage |
| --- | --- | --- |
| `radius-2` | `2 px` | `Stickers` |
| `radius-4` | `4 px` | `Buttons` |
| `radius-full` | `Object Height` | `Pills` |
| `radius-6` | `6 px` | `Sections`, `Cards` |

### Elevation

Status: intentionally left blank for now. Elevation is still being defined and should not be treated as stable guidance.

## Components

### Button

Source: [Button (WIP)](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=10011-9015&t=UAGdfjIM21J8aOTb-1)

#### Summary

- Variants: `Primary`, `Secondary`, `Tertiary`
- Sizes: `Large`, `Medium`, `Small`
- States: `Enabled`, `Hover`, `Disabled`, `Focused`
- Icon options: `None`, `Leading`, `Trailing`

#### Anatomy

- container
- label
- optional leading icon
- optional trailing icon
- focus ring in focused state

#### Documented Constraints

- Enabled and hover are shown for all three variants.
- Focused is shown for all three variants.
- Disabled is only shown for `Primary` in the current frame and should not be assumed for all variants without re-checking Figma.
- Icon-only buttons are not documented in this frame.

#### Dimensions

Base sizes:

| Size | No Icon | With Icon |
| --- | --- | --- |
| `Large` | `85 x 48` | `113 x 48` |
| `Medium` | `77 x 36` | `97 x 36` |
| `Small` | `57 x 28` | `77 x 28` |

Focused sizes:

| Size | No Icon | With Icon |
| --- | --- | --- |
| `Large` | `89 x 52` | `117 x 52` |
| `Medium` | `81 x 40` | `101 x 40` |
| `Small` | `61 x 32` | `81 x 32` |

#### Implementation Notes

- Model as one component with `variant`, `size`, and `iconPlacement`.
- Treat focus as interaction state, not a public API when possible.
- Radius guidance should use `radius-4`.

### Card

Source: [card](https://www.figma.com/design/y1urmpM4BinDTzrvnQkhyB/Rhythm-Web?node-id=2699-18290&t=UAGdfjIM21J8aOTb-1)

#### Summary

Card should be treated as a component family, not a single component.

Visible families:

- `Global Product Card`
- `Global Promo Card`
- `Tiles & Pills`
- `Contained Cards`
- `Building Blocks`

#### Family Characteristics

- Product cards support commerce-heavy layouts with image, price, rating, financing, and CTA.
- Promo cards support editorial layouts with message-first composition and optional imagery.
- Tiles and pills compress card behavior into navigational or merchandising surfaces.
- Contained cards support denser action-led layouts, including checkbox and add-to-cart patterns.

#### Building Blocks

Visible reusable subcomponents:

- image
- rating
- price
- adhoc message
- financing
- condition
- store
- card content
- promo image

#### Implementation Notes

- Split reusable card subcomponents from composed card patterns.
- Use `radius-6` for cards and sections unless a more specific variant is documented.
- Do not assume one responsive card model; the family uses multiple orientations and formats.

## Gaps

- Elevation is still undefined.
- Primitive extraction is partial and does not yet cover the full variables set.
- Icons, creative assets, and product image library are not yet documented deeply enough for build automation.
- Additional component pages should be added before treating this as a complete system map.
