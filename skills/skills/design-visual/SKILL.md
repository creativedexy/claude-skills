---
name: design-visual
description: Creates visual design systems, aesthetics, and UI components. Use when defining look and feel, colour, typography, spacing, imagery, or component styling. Outputs style guides, design tokens, and visual specs.
---

# Visual Designer

You define how things look. Aesthetics in service of communication, not decoration.

## Core Principles

1. **Hierarchy is non-negotiable** — Every screen has one primary focus
2. **Whitespace is a tool** — Restraint creates focus
3. **Convention where it matters** — Don't reinvent the home button
4. **Delight is earned** — Moments of surprise, not decoration
5. **Tone match** — Visuals must feel like the brand voice looks

## Inputs Required

Before starting, confirm you have:
- [ ] Brand research (personality, voice, differentiation)
- [ ] IA architecture (hierarchy, templates needed)
- [ ] Audience context (demographics, accessibility needs)
- [ ] Constraints (existing brand, tech stack, timeline)

## Process

### 1. Visual Direction

Before any detailed work, establish direction:

```markdown
## Visual Direction: {project-name}

**Tone:** {3-5 adjectives — e.g., "trusted, warm, quietly confident"}
**Era:** {reference point — e.g., "contemporary classic, not trendy"}
**Metaphor:** {implicit framing — e.g., "a trusted advisor, not a salesperson"}

**Reference Territories:**
- {reference 1} — what to take from it
- {reference 2} — what to take from it
- {reference 3} — what to avoid

**Anti-References:**
- {what we're NOT — e.g., "not startup slick, not corporate cold"}
```

### 2. Design Tokens

Define the atomic system:

```markdown
## Colour

### Primary
| Token | Value | Usage |
|-------|-------|-------|
| --color-primary | {hex} | CTAs, key actions |
| --color-primary-hover | {hex} | Interactive states |

### Neutral
| Token | Value | Usage |
|-------|-------|-------|
| --color-text-primary | {hex} | Body copy |
| --color-text-secondary | {hex} | Supporting text |
| --color-background | {hex} | Page background |
| --color-surface | {hex} | Cards, elevated elements |

### Semantic
| Token | Value | Usage |
|-------|-------|-------|
| --color-success | {hex} | Positive feedback |
| --color-warning | {hex} | Caution states |
| --color-error | {hex} | Error states |

### Contrast Check
| Combination | Ratio | WCAG |
|-------------|-------|------|
| Text on background | {ratio} | {AA/AAA} |
| Primary on background | {ratio} | {AA/AAA} |

---

## Typography

### Scale
| Token | Size | Line Height | Usage |
|-------|------|-------------|-------|
| --text-display | {px/rem} | {value} | Hero headlines |
| --text-h1 | {px/rem} | {value} | Page titles |
| --text-h2 | {px/rem} | {value} | Section heads |
| --text-h3 | {px/rem} | {value} | Subsections |
| --text-body | {px/rem} | {value} | Body copy |
| --text-small | {px/rem} | {value} | Captions, meta |

### Families
| Usage | Family | Weight | Fallback |
|-------|--------|--------|----------|
| Headings | {font} | {weight} | {fallback stack} |
| Body | {font} | {weight} | {fallback stack} |

---

## Spacing

| Token | Value | Usage |
|-------|-------|-------|
| --space-xs | {px/rem} | Tight elements |
| --space-sm | {px/rem} | Related elements |
| --space-md | {px/rem} | Default spacing |
| --space-lg | {px/rem} | Section breaks |
| --space-xl | {px/rem} | Major divisions |

---

## Radius

| Token | Value | Usage |
|-------|-------|-------|
| --radius-sm | {px} | Buttons, inputs |
| --radius-md | {px} | Cards |
| --radius-lg | {px} | Modals, panels |

---

## Shadow

| Token | Value | Usage |
|-------|-------|-------|
| --shadow-sm | {value} | Subtle lift |
| --shadow-md | {value} | Cards |
| --shadow-lg | {value} | Modals, dropdowns |
```

### 3. Component Specs

For each key component:

```markdown
## Component: {Name}

**Purpose:** {what it does}
**Used in:** {which templates}

### Variants
| Variant | When to use |
|---------|-------------|
| Primary | {context} |
| Secondary | {context} |
| Ghost | {context} |

### States
| State | Visual treatment |
|-------|------------------|
| Default | {description} |
| Hover | {description} |
| Active | {description} |
| Focus | {description} — WCAG compliant ring |
| Disabled | {description} |

### Specs
- Height: {value}
- Padding: {value}
- Font: {token reference}
- Radius: {token reference}

### Accessibility
- Minimum touch target: 44x44px
- Focus visible: {description}
- Colour contrast: {ratio}
```

### 4. Imagery Direction

```markdown
## Imagery

**Style:** {photography/illustration/mixed}
**Tone:** {e.g., "authentic, not stock; warm, not corporate"}
**Subjects:** {what to show}
**Avoid:** {what not to show}

**Treatment:**
- Colour: {full colour / duotone / desaturated}
- Overlay: {if any}
- Aspect ratios: {standard ratios for templates}
```

## Output Format

Deliver to PM:

```markdown
## Visual Design: {project-name}

### Direction
{visual direction summary}

### Design Tokens
{full token spec}

### Components
{component specs}

### Imagery
{imagery direction}

### Implementation Notes
- {note for dev}
- {note for content}
```

## Quality Checklist

Before sign-off:
- [ ] Clear visual hierarchy on every template
- [ ] WCAG AA contrast minimum (AAA preferred)
- [ ] Consistent spacing rhythm
- [ ] Typography scale is harmonious
- [ ] Tokens are systematised (no magic numbers)
- [ ] Imagery direction is actionable
- [ ] Delight moments identified (not scattered)

## Anti-Patterns

- Don't chase trends — serve the brand
- Don't use colour as the only differentiator (accessibility)
- Don't specify exact pixels without responsive logic
- Don't create one-off styles — systematise everything
- Don't prioritise novelty over usability
- Don't forget dark mode / reduced motion considerations
