# Chotot Design System Rules

Rules for implementing UI from the **Chotot DS** Figma file using the Figma MCP server.

---

## Figma MCP Integration — Required Flow

For every Figma-driven change, follow these steps in order. Do not skip.

1. Run `get_design_context` first to fetch the structured representation for the exact node(s)
2. If the response is too large or truncated, run `get_metadata` to get the high-level node map, then re-fetch only the required node(s) with `get_design_context`
3. Run `get_screenshot` for a visual reference of the node being implemented
4. Only after you have both `get_design_context` and `get_screenshot`, download any assets and start implementation
5. Validate the final UI against the Figma screenshot for 1:1 visual parity before marking complete

---

## Design Token System

Tokens follow the pattern: `var(--[category]/[variant], fallback)`

### Color Tokens

#### Text
| Token | Value |
|-------|-------|
| `--text/text-primary` | `#222` |
| `--text/text-tertiary` | `#8c8c8c` |

#### Background
| Token | Value |
|-------|-------|
| `--background/light/background-primary` | `#ffffff` |

#### Border
| Token | Value |
|-------|-------|
| `--border/border-thin` | `#e8e8e8` |

### Branding Color Palettes

Each Chotot product has its own color scale (50–900):

#### Chợ Tốt & Chợ Tốt Xe — Yellow
| Token | Hex |
|-------|-----|
| `--yellow/yellow-50` | `#fff8d6` |
| `--yellow/yellow-75` | `#ffed9f` |
| `--yellow/yellow-100` | `#ffd400` |
| `--yellow/yellow-200` | `#ffc800` |
| `--yellow/yellow-300` | `#ffba00` |
| `--yellow/yellow-400` | `#cc8f00` |
| `--yellow/yellow-500` | `#9e6c00` |
| `--yellow/yellow-600` | `#7f5500` |
| `--yellow/yellow-700` | `#603f00` |
| `--yellow/yellow-800` | `#4f3200` |
| `--yellow/yellow-900` | `#432900` |

#### Việc Làm Tốt — Blue
| Token | Hex |
|-------|-----|
| `--blue/blue-50` | `#f2f6fc` |
| `--blue/blue-75` | `#e4ecfb` |
| `--blue/blue-100` | `#cadbf7` |
| `--blue/blue-200` | `#a3c0f5` |
| `--blue/blue-300` | `#7fa7f0` |
| `--blue/blue-400` | `#548af0` |
| `--blue/blue-500` | `#306bd9` |
| `--blue/blue-600` | `#1952ba` |
| `--blue/blue-700` | `#113b8a` |
| `--blue/blue-800` | `#0b2f70` |
| `--blue/blue-900` | `#0b234f` |

#### Nhà Tốt — Orange
| Token | Hex |
|-------|-----|
| `--orange/orange-50` | `#fff4e0` |
| `--orange/orange-75` | `#ffe9c2` |
| `--orange/orange-100` | `#ffd494` |
| `--orange/orange-200` | `#ffb057` |
| `--orange/orange-300` | `#ff8800` |
| `--orange/orange-400` | `#e56700` |
| `--orange/orange-500` | `#c74c00` |
| `--orange/orange-600` | `#9f3504` |
| `--orange/orange-700` | `#752506` |
| `--orange/orange-800` | `#5e1a03` |
| `--orange/orange-900` | `#451608` |

---

## Typography System

Font family: **Reddit Sans** (primary for all styles), Helvetica (branding page headers only)
Font weights used: Bold (700), SemiBold (600), Medium (500), Regular (400)
Letter spacing: `0px` for all styles unless specified otherwise

Token pattern: `var(--[category]/[level]/[category]-[level]-[property], fallback)`
Sub-keys: `-font-family`, `-font-weight`, `-font-size`, `-line-height`, `-letter-spacing`

### Display — Bold (700)

| Style | Token Prefix | Size | Line Height |
|-------|-------------|------|-------------|
| Display / Page | `--display/page/display-page-` | 32px | 40px |
| Display / Section | `--display/section/display-section-` | 24px | 32px |

### Header — SemiBold (600)

| Style | Token Prefix | Size | Line Height |
|-------|-------------|------|-------------|
| Header / Page | `--header/page/header-page-` | 20px | 28px |
| Header / Section | `--header/section/header-section-` | 16px | 24px |
| Header / Caption | `--header/caption/header-caption-` | 14px | 20px |

### Body — Regular (400)

| Style | Token Prefix | Size | Line Height |
|-------|-------------|------|-------------|
| Body / Page | `--body/page/body-page-` | 16px | 24px |
| Body / Section | `--body/section/body-section-` | 14px | 20px |
| Body / Caption | `--body/caption/body-caption-` | 12px | 18px |
| Body / Annotation | `--body/annotation/body-annotation-` | 10px | 16px |

### Label — Bold (700)

| Style | Token Prefix | Size | Line Height |
|-------|-------------|------|-------------|
| Label / Page | `--label/page/label-page-` | 16px | 24px |
| Label / Section | `--label/section/label-section-` | 14px | 20px |
| Label / Caption | `--label/caption/label-caption-` | 12px | 18px |
| Label / Annotation | `--label/annotation/label-annotation-` | 10px | 16px |

### Tagline — Medium (500)

| Style | Token Prefix | Size | Line Height |
|-------|-------------|------|-------------|
| Tagline / Section | `--tagline/section/tagline-section-` | 16px | 20px |
| Tagline / Caption | `--tagline/caption/tagline-caption-` | 14px | 20px |
| Tagline / Annotation | `--tagline/annotation/tagline-annotation-` | 12px | 18px |
| Tagline / Footext | `--tagline/footext/tagline-footext-` | 10px | 16px |

---

## Elevation / Shadow

| Name | Value |
|------|-------|
| `shadow-floating` | `box-shadow: 0px 4px 16px 0px rgba(34, 34, 34, 0.12)` |
| `shadow-below` | `box-shadow: 0px 4px 8px 0px rgba(89, 89, 89, 0.15)` |

---

## Color Rules (Critical)

- **IMPORTANT:** Never hardcode hex color values. Always use design tokens: `var(--yellow/yellow-100, #ffd400)`
- **IMPORTANT:** Always provide a fallback hex value in the `var()` call as shown above
- Match the color token to the correct product brand (Yellow → Chợ Tốt, Blue → Việc Làm Tốt, Orange → Nhà Tốt)
- Use `--text/text-primary` (`#222`) for main body text, `--text/text-tertiary` (`#8c8c8c`) for secondary/supporting text
- Use `--border/border-thin` (`#e8e8e8`) for all card/container borders

## Typography Rules

- **IMPORTANT:** Never hardcode font sizes, weights, or line-heights. Always use the CSS token variables
- **IMPORTANT:** Use `Header/Section` (`--header/section/header-section-*`, SemiBold 600, 16px) as the default token for **Title text** in UI components, cards, and section headings
- **IMPORTANT:** Use `Body/Page` (`--body/page/body-page-*`, Regular 400, 16px) as the default token for **Body text** in paragraphs, descriptions, and content areas
- **Display** styles are for page/section titles only — never use for body content
- **Header** styles are for component headings, card titles, and UI labels
- **Body** styles are for paragraphs, descriptions, and supporting text
- **Label** styles are for button text, tags, badges, and interactive element labels
- **Tagline** styles are for supplementary inline text, meta info, and footnotes
- Use the correct **level** (Page/Section/Caption/Annotation) based on the visual hierarchy:
  - Page → largest/most prominent
  - Section → mid-level groupings
  - Caption → small supporting labels
  - Annotation → smallest, fine print / footnotes
- Letter spacing is `0px` for all styles; never add custom tracking unless explicitly in the token

## Component & Layout Rules

- Cards use: white background, 1px `--border/border-thin` border, `border-radius: 12px`, `shadow-floating` shadow
- Card internal layout: text info (flex column, 12px padding) + color swatch block (fixed width)
- Color swatch blocks: 200px wide, 100px height (or 104px when label overflows to 2 lines)
- Page-level sections use 100px left offset from canvas edge
- Section titles use Display/Page typography, `--text/text-primary` color

## Asset Rules

- **IMPORTANT:** If the Figma MCP server returns a localhost source for an image or SVG, use that source directly
- **IMPORTANT:** Do NOT install new icon packages — use assets from the Figma payload
- **IMPORTANT:** Do NOT create placeholder assets if a localhost source is provided

## Implementation Rules

- Treat the Figma MCP output (React + Tailwind) as a design reference, not final code
- Adapt all Tailwind classes to the project's own styling system
- Reuse existing components from the project's component library when available
- Strive for 1:1 visual parity with the Figma design screenshot
- Validate the final UI against the Figma screenshot before marking complete

---

## Button Component

### Button Variants

| Variant | Token | Fallback | Text Color |
|---------|-------|----------|------------|
| **Primary** | `--button/solid/button-primary` | `#ffd400` | `--text/text-on-background` (`#222`) |
| **Primary - Success** | `--button/solid/button-primary-success` | green | `--text/text-on-background` |
| **Black - Primary** | `--button/solid/button-black` | `#000` | white — **landing page only** |
| **Secondary** | `--button/tonal/button-tonal-neutral` | `#f4f4f4` | `--text/text-primary` (`#222`) |
| **Tertiary** | `--button/solid/button-blank` | `white` | `--text/text-primary` — has `1px border: --border/border-regular (#ddd)` |
| **Ghost** | none (transparent) | — | `--text/text-primary` — no background, no border |

### Button Sizes

| Size | Height | Icon size |
|------|--------|-----------|
| XL | 48px | 20px |
| L | 40px | 20px |
| M *(default)* | 32px | 20px |
| S | 24px | 16px |

### Button Shape
- Default: `border-radius: var(--radius/radius-card-small, 8px)`
- Pill: `border-radius: 999px` (when `isPill=Yes`)

### Button Anatomy & Spacing
- Padding: `px: var(--padding/padding-small-12, 12px)`, `py: var(--padding/padding-2x-small-4, 4px)`
- Icon-to-label gap: `var(--spacing/gap-2x-small-4, 4px)`
- Label typography: **Label / Section** (`--label/section/label-section-*`, Bold 700, 14px, 20px line-height)
- Optional icon left (20px) — sourced from Figma MCP payload, do not install icon packages

### Button States
All variants support: `Active`, `Hover`, `Pressed`, `Loading`, `Disabled`, `Skeleton`

### Icon Button
Same variants, sizes and states as Button but **icon-only** (square):
- XL: 48×48px, L: 40×40px, M: 32×32px, S: 24×24px

### Button Rules
- **IMPORTANT:** Use `Primary` for the main CTA — it uses the Chợ Tốt yellow brand color
- **IMPORTANT:** `Black - Primary` is for landing pages only — do not use in app UI
- **IMPORTANT:** Never hardcode button background/border colors — always use `--button/*` tokens
- Use `Label/Section` typography for all button labels — never `Body` or `Header` styles
- Maintain the exact padding and gap tokens — do not adjust spacing manually
- Icon buttons must be square — width = height = size value

### New Tokens (from Button)
| Token | Value |
|-------|-------|
| `--button/solid/button-primary` | `#ffd400` |
| `--button/tonal/button-tonal-neutral` | `#f4f4f4` |
| `--button/solid/button-blank` | `white` |
| `--text/text-on-background` | `#222` |
| `--border/border-regular` | `#ddd` |
| `--radius/radius-card-small` | `8px` |
| `--padding/padding-small-12` | `12px` |
| `--padding/padding-2x-small-4` | `4px` |
| `--spacing/gap-2x-small-4` | `4px` |
| `--stroke/stroke-divider` | `1px` |

---

## Input Field Components

### Input Types

| Type | Figma name | Notes |
|------|-----------|-------|
| **Input** | `Input-field/Input` | Standard single-line text input |
| **Input with Placeholder** | `Input-field/Input with Placeholder` | Shows placeholder before focus |
| **Currency** | `Input-field/Currency` | Numeric input for currency values |
| **Text-area** | `Input-field/Text-area` | Multi-line, flexible height |
| **Text-area with Placeholder** | `Input-field/Text-area with Placeholder` | Textarea with placeholder |
| **Dropdown** | `Input-field/Dropdown` | Single/multi-select dropdown |
| **Multi-select Dropdown** | `Input-field/MultiSelectDropdown` | Dropdown with chip tags |
| **Search Input** | `Input-field/Search-input` | Search with leading search icon |
| **Input Group** | `Input-field/Input-group` | Input + unit dropdown + action button combined |
| **Input Range** | `Input-field/Input - Range` | Numeric range (min/max pair) |

### Input States

| State | Border color token | Border fallback |
|-------|--------------------|----------------|
| Default / Out Focus | `--border/border-thin` | `#e8e8e8` |
| Hover | `--border/border-thin` | `#e8e8e8` |
| Focus On | `--border/border-black` | `#222` |
| Warning | `--border/border-warning` | orange |
| Error | `--border/border-error` | `#f0325e` |
| Success | `--border/border-success` | green |
| Disable | `--border/border-thin` | `#e8e8e8` (reduced opacity) |

Border width is always `var(--stroke/stroke-action, 2px)` for all states.

### Input Anatomy & Sizing

**Container (wrapper):**
- Layout: `flex-col`, gap `var(--spacing/gap-2x-small-4, 4px)`
- Default width: 300px (adapt to layout)

**Input field box:**
- Height: `48px` (single-line), flexible for textarea
- Background: `var(--background/light/background-primary, white)`
- Border: `2px solid [state-border-color]`
- Border radius: `var(--radius/radius-card, 12px)`
- Padding: `px: var(--padding/padding-medium-16, 16px)`, `py: var(--padding/padding-min-2, 2px)`
- Icon-to-text gap: `var(--spacing/gap-x-small-8, 8px)`

**Icons:**
- Icon Left: `24×24px`
- Icon Right: `20×20px`
- Search icon: `24×24px` (leading, always present in search variant)

### Input Typography

| Element | Style | Token | Color |
|---------|-------|-------|-------|
| Floating label (filled state) | Label / Annotation | `--label/annotation/label-annotation-*` | `--text/text-primary` (`#222`) |
| Placeholder / unfilled label | Body / Section | `--body/section/body-section-*` | `--text/text-secondary` (`#595959`) |
| Input text (user value) | Body / Section | `--body/section/body-section-*` | `--text/text-primary` (`#222`) |
| Help text | Body / Annotation | `--body/annotation/body-annotation-*` | `--text/text-secondary` (`#595959`) |
| Error help text | Body / Annotation | `--body/annotation/body-annotation-*` | `--text/text-error` (`#f0325e`) |
| Required asterisk `*` | — | — | `--text/text-error` (`#f0325e`) |

**Help text padding:** `px: var(--padding/padding-small-12, 12px)`

### Input Group Specifics
- Combines: text input + unit dropdown (chevron) + primary action button
- Internal divider separates sections
- Embedded button uses `Header/Section` typography (SemiBold 600, 16px) with `--button/solid/button-primary` background
- Dropdown section uses `Body/Section` with `--text/text-secondary`

### Input Rules
- **IMPORTANT:** Always use `2px` border (`--stroke/stroke-action`) — never `1px` for input fields
- **IMPORTANT:** Border color must change per state — use the correct state token, not a hardcoded color
- **IMPORTANT:** Use floating label pattern on Focus On + filled states: label shrinks to `Label/Annotation` (10px/Bold) and moves above the input text
- Unfilled/placeholder label uses `Body/Section` (14px/Regular) centered in the field
- Help text sits below the field with 12px horizontal padding, using `Body/Annotation` (10px)
- Error help text must use `--text/text-error` (#f0325e) — same color as the error border
- Required fields show `*` in `--text/text-error` color next to the label

### New Tokens (from Input Fields)
| Token | Value |
|-------|-------|
| `--border/border-black` | `#222` |
| `--border/border-error` | `#f0325e` |
| `--text/text-secondary` | `#595959` |
| `--text/text-error` | `#f0325e` |
| `--radius/radius-card` | `12px` |
| `--stroke/stroke-action` | `2px` |
| `--padding/padding-medium-16` | `16px` |
| `--padding/padding-min-2` | `2px` |
| `--spacing/gap-x-small-8` | `8px` |
| `--spacing/gap-min-2` | `2px` |

---

## Icon System

### Icon Overview

- **Size:** All icons are `24×24px` (standard). Use `16×16px` for small contexts (e.g., S-size buttons).
- **Source:** Icons are served from the Figma MCP asset endpoint — do **NOT** install third-party icon packages.
- **IMPORTANT:** If the Figma MCP server returns a localhost URL for an icon SVG, use that URL directly. Never use placeholders.

### Icon Naming Convention

Icons follow the pattern: `[Name]-[variant]`

| Variant suffix | Style |
|----------------|-------|
| `-fill` | Solid / filled |
| `-outline` | Stroked / outline |
| `-duotone` | Two-tone (foreground + muted background layer) |
| `-stroke` | Stroke-only (no fill) |
| `-circle` | Icon enclosed in a filled circle |
| `-circle-outline` | Icon enclosed in a stroked circle |

### Icon Catalog (269 icons)

#### Navigation & Direction
`Arrowup-fill`, `Arrowup-outline`, `Arrowdown-fill`, `Arrowdown-outline`, `Arrowleft-fill`, `Arrowleft-outline`, `Arrowright-fill`, `Arrowright-outline`, `Chevronup-fill`, `Chevronup-outline`, `Chevrondown-fill`, `Chevrondown-outline`, `Chevronleft-fill`, `Chevronleft-outline`, `Chevronright-fill`, `Chevronright-outline`

#### Actions & Controls
`Search-fill`, `Search-outline`, `Filter-fill`, `Filter-outline`, `Sort-Ascending`, `Sort-Default`, `Sort-Descending`, `Edit-fill`, `Edit-outline`, `Trashbin-fill`, `Trashbin-outline`, `Share-fill`, `Share-outline`, `Close-fill`, `Close-outline`, `Plus-fill`, `Plus-outline`, `Check-fill`, `Check-outline`, `Menu-fill`, `Menu-outline`, `Setting-fill`, `Setting-outline`, `Refresh-fill`, `Refresh-outline`, `Download-fill`, `Download-outline`, `Upload-fill`, `Upload-outline`, `Copy-fill`, `Copy-outline`, `Link-fill`, `Link-outline`, `Crop-fill`, `Crop-outline`

#### Communication
`Chat-fill`, `Chat-outline`, `Chat-duotone`, `Notification-fill`, `Notification-outline`, `Notification-duotone`, `Phone-fill`, `Phone-outline`, `Mail-fill`, `Mail-outline`, `Send-fill`, `Send-outline`

#### User & Profile
`User-fill`, `User-outline`, `User-circle`, `User-circle-outline`, `Group-fill`, `Group-outline`

#### Media & Content
`Camera-fill`, `Camera-outline`, `Image-fill`, `Image-outline`, `Video-fill`, `Video-outline`, `Play-fill`, `Play-outline`, `Pause-fill`, `Pause-outline`, `Livestream-fill`, `Livestream-outline`, `Mic-fill`, `Mic-outline`, `Volume-fill`, `Volume-outline`

#### Status & Feedback
`Star-fill`, `Star-outline`, `Heart-fill`, `Heart-outline`, `Warning-fill`, `Warning-outline`, `Info-fill`, `Info-outline`, `Check-circle`, `Check-circle-outline`, `Close-circle`, `Close-circle-outline`, `Question-fill`, `Question-outline`

#### Location & Map
`Location-fill`, `Location-outline`, `Map-fill`, `Map-outline`, `Compass-fill`, `Compass-outline`

#### Commerce & Finance
`Wallet-fill`, `Wallet-outline`, `Wallet-duotone`, `Cart-fill`, `Cart-outline`, `Tag-fill`, `Tag-outline`, `Gift-fill`, `Gift-outline`, `Discount-fill`, `Discount-outline`, `Coin-fill`, `Coin-outline`, `Bank-fill`, `Bank-outline`

#### Chotot-Specific
`CTFeed-fill`, `CTFeed-outline`, `GoiPro-fill`, `GoiPro-outline`, `Dongtot-fill`, `Dongtot-outline`, `Bump-fill`, `Bump-outline`, `Bumpdays-fill`, `Bumpdays-outline`, `SDA-fill`, `SDA-outline`

#### Brand / Social
`Facebook-fill`, `Facebook-outline`, `Zalo-fill`, `Zalo-outline`, `Apple-fill`, `Apple-outline`, `Google-fill`, `Google-outline`

#### Misc
`Home-fill`, `Home-outline`, `Category-fill`, `Category-outline`, `List-fill`, `List-outline`, `Grid-fill`, `Grid-outline`, `Bookmark-fill`, `Bookmark-outline`, `Calendar-fill`, `Calendar-outline`, `Clock-fill`, `Clock-outline`, `Lock-fill`, `Lock-outline`, `Unlock-fill`, `Unlock-outline`, `Eye-fill`, `Eye-outline`, `Eye-close-fill`, `Eye-close-outline`, `Document-fill`, `Document-outline`, `Folder-fill`, `Folder-outline`, `Attach-fill`, `Attach-outline`, `QR-fill`, `QR-outline`, `Flash-fill`, `Flash-outline`, `Fire-fill`, `Fire-outline`, `Shield-fill`, `Shield-outline`, `Support-fill`, `Support-outline`

### Icon Usage Rules

- **IMPORTANT:** Always source icons from the Figma MCP payload — never import `react-icons`, `heroicons`, `lucide-react`, or any other icon library
- **IMPORTANT:** Use `-fill` variant for primary interactive icons (buttons, tabs, active states)
- Use `-outline` variant for secondary or inactive states
- Use `-duotone` for emphasis icons (notifications, wallet, featured highlights)
- Use `-circle` / `-circle-outline` for avatar-style or badge contexts
- Default render size is `24×24px`; use `20×20px` inside M/L buttons, `16×16px` inside S buttons
- Icons inherit text color by default — use `currentColor` for SVG fill/stroke so they respond to context

---

## Figma File Reference

- **File:** Chotot DS — Claude testing
- **File Key:** `SRUHvROMbepxaPHpeNF6rG`
- **Pages:**
  - `0:1` — Color (full neutral + semantic palette)
  - `10:578` — Branding Color (product-specific palettes)
  - `10:2303` — Typography (full type scale and token definitions)
  - `10:4327` — Button component (variants, sizes, states, icon button)
  - `10:8406` — Input Field components (input, textarea, dropdown, search, input-group, range)
  - `10:11838` — Icon System (269 icons, 24×24px, fill/outline/duotone/stroke variants)
