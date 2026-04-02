---
name: client-first
description: Finsweet Client-First methodology for Webflow development. Use when building Webflow sites, writing Webflow embed code, creating class names, structuring pages, or discussing Webflow best practices. Covers class naming, folder organization, spacing, typography, core structure, variables, interactions, and accessibility.
---

# Finsweet Client-First — Complete Reference

Client-First is a comprehensive naming convention and organizational system for Webflow projects by Finsweet. It governs class naming, page structure, spacing, typography, folders, variables, interactions, and accessibility.

Full documentation source: https://finsweet.com/client-first/docs

---

## 0. Critical Rule: No CSS for Predefined Classes

**NEVER write CSS styles for predefined Client-First classes.** When implementing, only add the class name to the element — do not generate any CSS rules for it. These classes are already defined in the Client-First system/stylesheet within Webflow.

This applies to ALL predefined utility and structural classes, including but not limited to:
- Core structure: `page-wrapper`, `main-wrapper`, `section_[name]`, `padding-global`, `padding-section-[size]`, `container-[size]`
- Spacing: `margin-top`, `margin-bottom`, `margin-small`, `margin-large`, `padding-top`, `padding-medium`, `spacer-[size]`, `spacing-clean`, etc.
- Typography: `heading-style-h1`–`heading-style-h6`, `text-size-[value]`, `text-style-[value]`, `text-weight-[value]`, `text-align-[value]`, `text-color-[value]`
- Visibility: `hide`, `hide-tablet`, `hide-mobile-landscape`, `hide-mobile-portrait`
- Layout utilities: `display-inlineflex`, `align-center`, `layer`, `overflow-hidden`, `overflow-scroll`, `overflow-auto`
- Max width: `max-width-[size]`, `max-width-full`, `max-width-full-tablet`, etc.
- Icons: `icon-height-[size]`, `icon-1x1-[size]`
- Aspect ratio: `aspect-ratio-square`, `aspect-ratio-portrait`, `aspect-ratio-landscape`, `aspect-ratio-widescreen`
- Z-index: `z-index-1`, `z-index-2`
- Pointer events: `pointer-events-none`, `pointer-events-auto`
- Colors: `background-color-primary`, `background-color-secondary`, `text-color-primary`, `text-color-secondary`, `inherit-color`, etc.
- Buttons: `button`, `is-secondary`, `is-text`, `is-primary`, `is-dark`
- Any combo class prefix: `is-[variant]`

**Only write CSS for custom classes** (classes with `_` that you create for specific components/elements).

### Sections: No Size Styles
**Never apply size properties (width, height, min-width, min-height, max-width, max-height, or overflow) to `section_[name]` elements.** Sections should have no size styles — their dimensions are controlled entirely by their inner content and the padding/container structure. Leave all size values at their defaults (Width: Auto, Height: Auto, Min W/H: 0, Max W/H: None).

---

## 1. Class Types

### Utility Classes
- Apply global CSS properties across the project
- **NO underscore** in name — dashes only
- Examples: `text-size-large`, `margin-bottom`, `background-color-primary`

### Custom Classes
- Created for specific components, pages, or elements
- **USE underscore** `_` to separate folder from element name
- Examples: `header_background-layer`, `testimonial-slider_headshot`

### Global Classes
- Any class (utility or custom) intended for site-wide reuse
- Examples: `container-large`, `faq_item`, `section-dark`

### Combo Classes
- Variant on top of a base class using `is-` prefix
- Only works combined with its base class
- Examples: `button` + `is-brand`, `section_header` + `is-home`
- Max stacking: 1-2 classes ideal, 3 okay, 4 absolute max, 5+ = too much

---

## 2. Naming Convention

### Core Rules
- Names should be **clear, descriptive, human-readable**
- **No abbreviations or shorthand**
- Keywords go **general to specific**: `text-size-large` not `large-size-text`
- A non-technical person should understand the class purpose

### Custom Class Pattern
```
[folder-name]_[element-name]
```
Examples:
- `team-list_headshot-wrapper`
- `footer_copyright-text`
- `nav_primary_logo-wrapper` (nested folders)

### Utility Class Pattern
```
[category]-[property]-[value]
```
Examples:
- `text-size-large`
- `padding-section-medium`
- `background-color-primary`

---

## 3. Core Structure (6 Classes)

Every page uses these layered div blocks:

```
page-wrapper                    → outermost, wraps everything
  nav (header tag)              → outside main-wrapper
  main-wrapper (main tag)       → wraps main content, NOT nav/footer
    section_[name] (section tag) → identifies each section
      padding-global + padding-section-[size]  → combined on same div
        container-[size]         → max-width container
          [content]              → your components
  footer (footer tag)           → outside main-wrapper
```

### Class Details
| Class | Purpose | Styles |
|-------|---------|--------|
| `page-wrapper` | Outermost wrapper | Optional (e.g., overflow: hidden) |
| `main-wrapper` | Main content (`<main>` tag) | Optional |
| `section_[name]` | Section identifier (`<section>` tag) | Avoid styling; use add-on like `section-style-dark` |
| `padding-global` | Horizontal padding (left/right) | padding-left, padding-right only |
| `padding-section-[size]` | Vertical section spacing | padding-top, padding-bottom only |
| `container-[size]` | Max-width container | margin: 0 auto, width: 100%, max-width |

### Container Sizes
- `container-large` — widest (default ~80rem / 1280px)
- `container-medium`
- `container-small`

### Section Padding Sizes
- `padding-section-small`
- `padding-section-medium`
- `padding-section-large`

**Key:** `padding-global` and `padding-section-[size]` go on the **same div** to reduce nesting.

---

## 4. Folders System

### Custom Class Folders (underscore = folder)
```
folder-name_element-name           → one folder
folder_subfolder_element-name      → nested folders
```

- One `_` = one folder level
- Classes without `_` go into the auto-organized **Utility** folder
- Only nest folders when there's a clear organizational benefit

### Utility Class Folders (auto-grouped by keyword match)
- Classes grouped by matching first keyword: `text-size-large` and `text-color-primary` both go in `text` folder
- Sub-folders created when 2+ classes share first AND second keyword

### Folder Strategies
| Strategy | Pattern | When to Use |
|----------|---------|-------------|
| General folder | `slider_arrow` | Reusable components |
| Page-specific folder | `home-hero_title` | Page-specific elements |
| Nested: page first | `home_slider_arrow` | Organize by page |
| Nested: keyword first | `slider_home_arrow` | Organize by component type |
| Component keyword | `clients-slider_component` | Mark the parent wrapper of a complete UI component |

### Component Keyword
Use `_component` as element identifier on the outermost wrapper of a complete UI component:
```
client-slider_component    ← parent wrapper
client-slider_mask
client-slider_grid
client-slider_arrow
```

---

## 5. Typography Strategy

### Defaults = HTML Tags
- Style H1-H6 and body text on their HTML tags (no class needed)
- Only add classes when there's a **variation** from the default

### Typography Utility Classes

**Heading style switch** (change visual style while keeping SEO tag):
- `heading-style-h1` through `heading-style-h6`

**Text size:**
- `text-size-tiny`, `text-size-small`, `text-size-regular`, `text-size-medium`, `text-size-large`

**Text style:**
- `text-style-allcaps`, `text-style-italic`, `text-style-link`, `text-style-muted`
- `text-style-nowrap`, `text-style-quote`, `text-style-strikethrough`
- `text-style-2lines`, `text-style-3lines`

**Text weight:**
- `text-weight-light`, `text-weight-normal`, `text-weight-semibold`, `text-weight-bold`, `text-weight-xbold`

**Text alignment:**
- `text-align-left`, `text-align-center`, `text-align-right`

**Text color:**
- `text-color-primary`, `text-color-secondary`, `text-color-alternate`

### Implementation Rule: Match Design Values to Predefined Classes
When implementing text styles, **always use predefined Client-First typography classes** instead of writing custom CSS. Follow this exact workflow:

1. **Get the actual values from Figma MCP** — read the design to extract concrete values (e.g., font-size: 3rem, font-weight: 700, color: #1a1a1a)
2. **Fetch variables from Webflow MCP** — query the Webflow project's variables/styles to see all predefined Client-First class values and what they map to
3. **Match the Figma value to a predefined class** — find which Client-First class holds the matching value (e.g., if `text-size-large` = 3rem in the Webflow variables, use `text-size-large`)
4. **Apply only the class name** — add the matched predefined class to the element. Do NOT write any custom CSS for that property.
5. **Cache/reuse the variable lookup** — once you've fetched the Webflow variables, keep referencing that data for subsequent elements in the same implementation session. No need to re-fetch for every element.

**Example workflow:**
- Figma shows a title with font-size `3rem`, weight `700`, color `#1a1a1a`
- Fetch Webflow variables → `text-size-large` = 3rem, `text-weight-bold` = 700, `text-color-primary` = #1a1a1a
- Apply classes: `text-size-large`, `text-weight-bold`, `text-color-primary`
- Write zero CSS for these properties

This applies to ALL text properties: size, weight, color, alignment, and style. Only write custom CSS when no predefined class matches the design value.

### When to Use Custom Classes for Text
- Unique/specific text with many combined styles (e.g., `footer_copyright-text`)
- Manage a recurring group of text elements (e.g., `footer_link`)
- Needs unique responsive behavior different from global defaults

---

## 6. Spacing Strategy

### Spacing Utility Classes

**Margin direction:** `margin-top`, `margin-bottom`, `margin-left`, `margin-right`, `margin-horizontal`, `margin-vertical`

**Margin sizes:**
| Class | Value |
|-------|-------|
| `margin-0` | 0rem |
| `margin-tiny` | 0.125rem |
| `margin-xxsmall` | 0.25rem |
| `margin-xsmall` | 0.5rem |
| `margin-small` | 1rem |
| `margin-custom1` | 1.5rem |
| `margin-medium` | 2rem |
| `margin-custom2` | 2.5rem |
| `margin-large` | 3rem |
| `margin-custom3` | 3.5rem |
| `margin-xlarge` | 4rem |
| `margin-xxlarge` | 5rem |
| `margin-huge` | 6rem |
| `margin-xhuge` | 8rem |
| `margin-xxhuge` | 12rem |

**Padding:** Same naming pattern (`padding-top`, `padding-small`, etc.) with identical sizes.

**How stacking works:** Direction + Size on same element:
```
margin-bottom + margin-large  → margin-bottom: 3rem
padding-top + padding-medium  → padding-top: 2rem
```

### Spacing Strategies

1. **Spacing blocks** (`spacer-[size]`): Empty div between siblings — single class
2. **Spacing wrappers** (direction + size): Div wrapping a child element — two classes
3. **Custom class on element**: Apply margin/padding directly to custom class
4. **CSS Grid parent**: Use grid gap on parent to space children

### Rules
- Don't stack spacing classes on typography elements (use spacing blocks instead)
- Don't use utility padding for inner element sizing (use custom class)
- `spacer-` classes support responsive combo variants: `spacer-large` + `is-mobile-small`
- `spacing-clean` — removes all margin and padding (useful for resetting Webflow defaults)

---

## 7. Sizes and Rem

### Base Rule: Use rem, not px
- 1rem = 16px (browser default)
- All sizes should be in rem for accessibility (respects browser font settings + zoom)

### Recommended Values
Clean rem values: `0.5`, `1`, `1.5`, `2`, `2.5`, `3`, `4`, `5`, `6`, `8`, `12`

### Exceptions
- **Typography:** 14px (0.875rem) is acceptable when 16px is too large
- **Tiny spacing:** 2px (0.125rem) for very small gaps
- **Borders:** Keep 1px as 1px (don't convert to rem)

### Webflow Tip
Type `100/16rem` in any input to auto-calculate rem.

---

## 8. Variables (Colors Only)

Size variables are NOT used (no breakpoint support in Webflow variables panel).

### Primitive Tokens
- Foundational colors, prefixed with `- Base Color:`
- Groups: Brand, Neutral, System colors
- **Don't link primitives directly to classes** — use semantic tokens

### Semantic Tokens
- Named by purpose, not color: `[element]-[style]-[identifier]`
- Examples: `background-color--background-primary`, `text-color--text-primary`, `border-color--border-brand`
- **Never name by color** (no `background-color--blue`)

### Utility Classes Linked to Semantic Tokens
- `background-color-primary`, `background-color-secondary`, `background-color-tertiary`, `background-color-alternate`
- `text-color-primary`, `text-color-secondary`, `text-color-alternate`
- `inherit-color` — utility class to override and inherit from parent

---

## 9. Buttons

### Base + Combo Pattern
```
button                    ← base class with padding, font-size, shared styles
button + is-secondary     ← variant
button + is-text          ← variant
button + is-primary       ← variant
button + is-dark          ← variant
```

- Use `display-inlineflex` for inline button behavior
- Use flex/grid on parent wrapper for button rows (don't add margin to button class itself)

---

## 10. Useful Utility Classes

### Visibility
- `hide` — hide on all devices
- `hide-tablet`, `hide-mobile-landscape`, `hide-mobile-portrait`

### Layout
- `display-inlineflex` — display: inline-flex
- `align-center` — margin-left/right: auto
- `layer` — position: absolute, 0% all sides (parent must not be static)
- `overflow-hidden`, `overflow-scroll`, `overflow-auto`

### Max Width
- `max-width-xxsmall` (12rem) through `max-width-xxlarge` (80rem)
- `max-width-full` — sets max-width: none
- `max-width-full-tablet`, `max-width-full-mobile-landscape`, `max-width-full-mobile-portrait`

### Icons
- `icon-height-small`, `icon-height-medium`, `icon-height-large`
- `icon-1x1-small`, `icon-1x1-medium`, `icon-1x1-large`

### Aspect Ratio
- `aspect-ratio-square` (1:1), `aspect-ratio-portrait` (2:3), `aspect-ratio-landscape` (3:2), `aspect-ratio-widescreen` (16:9)

### Z-Index
- `z-index-1`, `z-index-2`

### Pointer Events
- `pointer-events-none`, `pointer-events-auto`

---

## 11. Don't Deep Stack

### Rule: Max 2 classes preferred, 4 absolute max

| Count | Verdict |
|-------|---------|
| 1-2 | Great, common |
| 3 | Ok — is it necessary? |
| 4 | Absolute maximum |
| 5+ | Too much — create a custom class |

### How to Avoid Deep Stacking
1. **Use a single custom class** instead of stacking utility classes
2. **Nest another div** to separate concerns (spacing div vs. content div)
3. **Create a combo class** to collapse multiple utilities into base + `is-variant`

### Never Add New Styles to Stacked Global Classes
Stacking `margin-top` + `margin-large` then adding more styles creates an unintended combo class. Instead:
- Start with a custom class, OR
- Add an `is-` combo class on top

---

## 12. No Layout System

Client-First does NOT include flex/grid/column utility classes.

- **Do:** Create custom classes for layouts (`team-grid_wrapper` with flex/grid)
- **Do:** Use simple global grid classes if helpful (`grid_col-2`, `grid_col-3`) with `is-` combos for responsive variants
- **Don't:** Create deep utility layout systems like `grid-3-col` + `gap-large` + `tablet-grid-2` + `mobile-grid-1`

---

## 13. Interactions Naming

### Pattern: `Element [Action + State]`

- **Element:** What receives the interaction (descriptive keywords)
- **Action:** What happens (Show, Hide, Move, Rotate, Scale)
- **State:** Toggle state (In/Out, Open/Close, Expand/Collapse)

### Examples
```
Button Arrow [Move In]
Nav Menu [Open]
Home Hero Lottie [Show]
Jobs Item Modal [Close]
Contact Form Input [Height Increase]
```

### Rules
- Capitalize first letter of each word
- Use square brackets around action/state
- Keep names short (don't overflow Webflow's UI panel)
- Trigger keywords (Click, Hover, Scroll, Load) are optional — add only if they enhance clarity
- Responsive keywords at end: `Nav Sidebar [Show] [Mobile]`

---

## 14. Semantic HTML Tags

### Required Structure
| Tag | Client-First Usage |
|-----|-------------------|
| `<header>` | Nav component |
| `<main>` | `main-wrapper` |
| `<footer>` | Footer component |
| `<section>` | Each `section_[name]` |
| `<article>` | Self-contained content (blog posts, product cards, etc.) |
| `<aside>` | Sidebars, related content |
| `<nav>` | Navigation links (navbar, footer links, breadcrumbs, TOC) |
| `<figure>` | Images, diagrams, code blocks |
| `<address>` | Contact information |

### Heading Rules
- Only **one H1** per page
- Don't skip heading levels (H1 > H2 > H3, never H1 > H3)
- Use `heading-style-h#` classes to change visual style while keeping correct SEO tag

---

## 15. Accessibility

- Use **rem** units (respects browser font size + zoom)
- Use semantic HTML tags
- Don't skip heading levels
- Empty spacing divs are fine (screen readers skip them)
- Add alt text to all images
- `main-wrapper` with `<main>` tag helps screen readers find main content

---

## 16. Global Embed

- Symbol embed block with site-wide custom CSS
- Place on every page
- Use embed (not Site Settings) so CSS is visible in Designer
- Contains Webflow default style overrides
- Each snippet has comments explaining its purpose
