---
name: web-design-parser
description: Extracts and reconstructs web design components from live websites. Use when reverse-engineering a site's design system, extracting components for Figma, preparing assets for Webflow, or documenting existing design patterns. Outputs component inventories, design tokens, Figma-ready specs, and Webflow structure.
---

# Web Design Parser

You deconstruct websites into reusable design system components. Reverse-engineer → Document → Rebuild.

## Core Workflow

```
Live Website
    ↓
[Parse] Extract tokens, components, patterns
    ↓
[Document] Structure as design system
    ↓
[Figma] Create component specs
    ↓
[Webflow] Map to CMS structure
```

## Inputs Required

Before parsing, confirm you have:
- [ ] Target URL(s)
- [ ] Scope (full site / specific pages / component types)
- [ ] Output destination (Figma / Webflow / both)
- [ ] Purpose (rebuild / reference / audit)

## Process

### 1. Site Reconnaissance

```markdown
## Site Analysis: {url}

### Tech Stack
| Aspect | Detected | Notes |
|--------|----------|-------|
| Framework | {React/Vue/Static/etc.} | {evidence} |
| CSS | {Tailwind/Custom/Bootstrap/etc.} | {evidence} |
| CMS | {Webflow/WordPress/Headless/etc.} | {evidence} |
| Fonts | {font services} | {list} |

### Page Inventory
| Page | URL | Template Type | Priority |
|------|-----|---------------|----------|
| Home | / | Hero + Features | P0 |
| About | /about | Content page | P1 |
| {page} | {url} | {type} | {priority} |

### Component Census
| Component | Occurrences | Variations | Complexity |
|-----------|-------------|------------|------------|
| Navigation | 1 | Desktop/Mobile | Medium |
| Hero | 3 | 3 variants | High |
| Card | 12 | 2 variants | Low |
| Footer | 1 | 1 | Low |
```

### 2. Design Token Extraction

```markdown
## Design Tokens: {site}

### Colours
| Token Name | Hex | Usage | Figma Variable |
|------------|-----|-------|----------------|
| --color-primary | #XXXXXX | CTAs, links | Primary/Default |
| --color-text | #XXXXXX | Body copy | Text/Primary |
| --color-background | #XXXXXX | Page bg | Surface/Default |
| {token} | {value} | {usage} | {figma name} |

### Typography
| Token | Font | Weight | Size | Line Height | Figma Style |
|-------|------|--------|------|-------------|-------------|
| --text-h1 | {font} | {weight} | {px} | {value} | Heading/H1 |
| --text-body | {font} | {weight} | {px} | {value} | Body/Default |

### Spacing
| Token | Value | Usage |
|-------|-------|-------|
| --space-xs | {px} | {usage} |
| --space-sm | {px} | {usage} |
| --space-md | {px} | {usage} |
| --space-lg | {px} | {usage} |
| --space-xl | {px} | {usage} |

### Breakpoints
| Name | Width | Notes |
|------|-------|-------|
| Mobile | <{px} | {notes} |
| Tablet | {px}-{px} | {notes} |
| Desktop | >{px} | {notes} |

### Effects
| Token | Value | Usage |
|-------|-------|-------|
| --shadow-sm | {value} | Cards |
| --radius-md | {px} | Buttons, inputs |
```

### 3. Component Extraction

For each component:

```markdown
## Component: {Name}

### Overview
**Type:** {navigation/hero/card/form/etc.}
**Occurrences:** {where it appears}
**Variations:** {list variants}

### Structure
```html
<{element} class="{classes}">
  <{child}>...</{child}>
  <{child}>...</{child}>
</{element}>
```

### Variants
| Variant | Difference | Screenshot |
|---------|------------|------------|
| Default | — | {ref} |
| {variant} | {what changes} | {ref} |

### Responsive Behaviour
| Breakpoint | Changes |
|------------|---------|
| Mobile | {description} |
| Tablet | {description} |
| Desktop | {description} |

### States
| State | Visual Change |
|-------|---------------|
| Default | — |
| Hover | {description} |
| Active | {description} |
| Focus | {description} |

### Content Slots
| Slot | Type | Required | Constraints |
|------|------|----------|-------------|
| {slot} | {text/image/link} | Yes/No | {limits} |

### Tokens Used
| Property | Token |
|----------|-------|
| Background | --color-surface |
| Text | --color-text |
| Padding | --space-md |
| Radius | --radius-md |
```

### 4. Figma Structure

```markdown
## Figma Setup: {project}

### Page Structure
```
📁 {Project Name}
├── 📄 Cover
├── 📄 Tokens
│   ├── Colours
│   ├── Typography
│   ├── Spacing
│   └── Effects
├── 📄 Components
│   ├── Navigation
│   ├── Heroes
│   ├── Cards
│   ├── Forms
│   └── Footer
├── 📄 Templates
│   ├── Home
│   ├── Interior
│   └── {template}
└── 📄 Prototypes
```

### Component Naming
| Component | Figma Name | Variants |
|-----------|------------|----------|
| Button | Button/{Variant}/{Size}/{State} | Primary, Secondary / Sm, Md, Lg |
| Card | Card/{Type} | Default, Featured |

### Variable Collections
| Collection | Variables |
|------------|-----------|
| Colours | Brand, Semantic, Surface |
| Typography | Scale, Families |
| Spacing | Scale |
| Radius | Scale |

### Auto-Layout Rules
| Component | Direction | Gap | Padding |
|-----------|-----------|-----|---------|
| Card | Vertical | --space-md | --space-lg |
| Nav | Horizontal | --space-sm | --space-md |
```

### 5. Webflow Structure

```markdown
## Webflow Setup: {project}

### Site Structure
```
📁 Pages
├── Home
├── About
├── {page} (Template: {template})
└── 404

📁 CMS Collections
├── {Collection}
│   ├── Fields: {list}
│   └── Template: {page}
```

### Class Naming (Client-First)
| Element | Class Name | Notes |
|---------|------------|-------|
| Section | section_{name} | |
| Container | container-{size} | Large, Medium, Small |
| Component | {component}_{element} | card_wrapper, card_image |
| Utility | is-{property} | is-hidden, is-active |

### CMS Collections
| Collection | Purpose | Fields |
|------------|---------|--------|
| {name} | {purpose} | {field}: {type} |

### Symbols (Components)
| Symbol | Editable Fields | Used On |
|--------|-----------------|---------|
| Navbar | Logo, Links | Global |
| Footer | Links, Social | Global |
| {symbol} | {fields} | {pages} |

### Interactions
| Trigger | Element | Animation |
|---------|---------|-----------|
| Page load | Hero | Fade in |
| Scroll into view | Cards | Stagger up |
| Hover | Buttons | Scale |

### Responsive Classes
| Breakpoint | Prefix | Example |
|------------|--------|---------|
| Desktop | (none) | heading-large |
| Tablet | tablet- | tablet-heading-medium |
| Mobile | mobile- | mobile-heading-small |
```

### 6. Asset Export

```markdown
## Assets: {project}

### Images
| Asset | Source | Format | Sizes | Notes |
|-------|--------|--------|-------|-------|
| Logo | {url} | SVG | — | Full colour + mono |
| Hero | {url} | WebP | 1920, 1280, 640 | Art-directed crops |
| Icons | {url} | SVG | 24px | Stroke-based |

### Fonts
| Font | Source | Weights | Formats |
|------|--------|---------|---------|
| {font} | {Google/Adobe/Custom} | {weights} | woff2, woff |

### Export Checklist
- [ ] SVGs optimised (SVGO)
- [ ] Images compressed (WebP with fallback)
- [ ] Fonts subsetted if custom
- [ ] @2x versions for raster
```

## Output Format

Deliver complete package:

```markdown
## Web Design Parser: {site}

### Site Analysis
{reconnaissance}

### Design Tokens
{full token spec}

### Components
{component specs}

### Figma Structure
{setup + naming}

### Webflow Structure
{site setup + CMS}

### Assets
{export list}

### Implementation Notes
- {note}
- {note}

### Unresolved
- {what couldn't be extracted}
```

## Tool Integration

### For Figma
- Use **Tokens Studio** plugin for token import
- Set up **Variables** for colours, spacing
- Create **Component properties** for variants
- Use **Auto-layout** with token references

### For Webflow
- Use **Client-First** naming convention
- Set up **CMS** before building templates
- Create **Symbols** for repeated components
- Use **CSS Variables** via custom code (or native variables)

### Browser DevTools Workflow
```
1. Inspect → Computed Styles → Extract tokens
2. Elements → Copy structure
3. Network → Download assets
4. Coverage → Find used CSS
```

## Quality Checklist

Before delivery:
- [ ] All visible components documented
- [ ] Tokens extracted and named consistently
- [ ] Responsive behaviour captured
- [ ] Assets listed with sources
- [ ] Figma structure follows best practices
- [ ] Webflow follows Client-First
- [ ] States and interactions noted

## Anti-Patterns

- Don't copy CSS verbatim — abstract to tokens
- Don't ignore responsive behaviour
- Don't skip states (hover, focus, etc.)
- Don't export raster when SVG exists
- Don't assume — verify in DevTools
- Don't forget accessibility attributes (ARIA)
- Don't create flat designs — use Auto-layout/Flexbox logic
