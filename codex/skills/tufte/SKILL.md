---
name: tufte
description: >-
  Apply Edward Tufte's data-visualization principles to turn information into clear, honest
  visuals — and proactively use those visuals to reason through complex decisions. TRIGGER
  when the user asks to produce, design, critique, or improve a chart, graph, dashboard, KPI
  tile, table-with-data, sparkline, small multiple, time series, distribution plot, or
  infographic; when the user uses words like "visualize", "viz", "data viz", "chart", "graph",
  "dashboard", "infographic", or "Tufte"; OR when the user is weighing a complex decision,
  comparing options, evaluating trade-offs, or says things like "help me decide", "I need to
  understand this", "compare these", "what are the trade-offs", "is it worth it", "explain
  this visually", or "show me". SKIP for logos, decorative graphics, flowcharts, UI mockups,
  purely textual/narrative tasks with no comparison in them, or a decision with one obvious
  answer. Outputs Tufte-compliant designs as a self-contained HTML/SVG file (default) or a
  React component (Recharts/D3) when working in a React project. Defaults to Tufte rules; the
  user can opt out per chart.
---

# Tufte (Codex)

You make information legible. Data and the decision it informs come first; everything else is overhead to be earned or erased. The design principles below are Edward Tufte's and are not to be modified — your judgement applies only to *when* and *how* you reach for a visual.

## When to Use

Two modes. The principles are identical in both; only the trigger differs.

**1. Explicit visualization requests** — the user asks for a chart, graph, dashboard, infographic, sparkline, small multiple, or asks you to critique/improve an existing visual.

**2. Decision support (implicit trigger)** — the user is facing a complex decision and would understand it faster with a picture than with prose. Watch for:
- Comparing 2+ options, vendors, designs, architectures, or strategies
- Weighing trade-offs across multiple dimensions (cost vs. speed vs. risk)
- Reasoning about change over time, thresholds, or "what happens if…"
- Phrases: "help me decide", "I need to understand", "compare", "what are the trade-offs", "is it worth it", "show me", "explain this visually"

Codex can invoke this skill implicitly. In mode 2, **offer or produce a visual proactively** rather than waiting to be asked — but keep it lightweight. A small honest chart written to a file, plus a short paragraph, beats a wall of text. If the decision is trivial or genuinely clearer as prose, say so and don't force a chart.

## When NOT to Use

- Purely textual, narrative, or non-quantitative tasks with no comparison in them
- Logos, decorative graphics, flowcharts, or UI mockups
- A "decision" with one obvious answer — don't manufacture a chart to look thorough

## Core Principles — Ten Rules (do not modify)

These are Tufte's principles, preserved verbatim in intent. Apply them to every visual you produce.

1. **Show the Data** — "Above all else show the data." Data deserves prominence over decorative elements like gridlines, titles, and frames. Each design choice should serve clarity. When uncertain, remove it — aggressive editing typically yields superior charts.

2. **Maximize the Data-Ink Ratio** — "Maximize the data-ink ratio, within reason." Data-ink changes when underlying values shift; everything else competes needlessly. For every visual component ask: would it change if the data did? If no, consider deleting it.

3. **Erase Non-Data-Ink** — "Erase non-data-ink, within reason." Eliminating borders, gridlines, ticks, and unnecessary axes typically removes half of a chart's ink while retaining all information. Substitute faded lines for prominent ones; replace cross-hatching with subtle gray.

4. **Erase Redundant Data-Ink** — "Erase redundant data-ink, within reason." Each value warrants a single encoding. Bar charts often repeat one measurement many ways — height, position, shading, labels. Select one method per quantity; don't combine bars *and* printed values *and* gridlines *and* axis labels.

5. **Graphical Integrity** — Visual representation must match numerical reality. The "lie factor" — ratio of graphic effect to actual effect — should stay between 0.95–1.05. Avoid truncated axes that exaggerate change, area encoding of a single dimension, 3D perspective distortion, inconsistent scales, and dual-axis false correlations.

6. **Small Multiples** — "At the heart of quantitative reasoning is a single question: Compared to what?" Six overlaid lines confuse; six aligned small charts clarify. Parallelism reads faster than untangled overlap. Replace second lines, stacked bars, and dual axes with side-by-side charts.

7. **Layering and Separation** — Order visual layers by importance: data foremost, labels secondary, scaffolding faintest. When elements create unintended visual noise, reduce one's weight. Use white gridlines on gray, thin gray axes, solid black or accent-color data, clean sans-serif type at 11–13px.

8. **Micro/Macro Readings** — "To clarify, add detail." Excellent charts work at distance and up close — one shape from afar, legible points nearby. Use range frames that fill the actual data extent; show all points unless a summary line also appears. Label salient values directly.

9. **The Smallest Effective Difference** — "Make all visual distinctions as subtle as possible, but still clear and effective." Contrast between elements should meet the distinction requirement minimally. Light-gray-vs-dark-gray often replaces red-vs-blue. Reserve high-contrast color for focal values.

10. **Word-Data Integration** — Charts belong within sentences, not isolated boxes. Numbers live beside their visual forms. Sparklines fit tables, paragraphs, and dashboards. One row combining number, label, and tiny sparkline is a complete graphic needing no frame.

## Kill List (remove unless explicitly requested)

3D effects · pie charts · donut charts · dual-axis charts · rainbow/spectral scales for ordered data · heavy gridlines · chartjunk borders and frames · drop shadows · redundant legends · moiré patterns · gradient fills that don't encode data.

If the user explicitly wants one of these (e.g. a pie chart), produce it, then add a brief note in the code/output explaining the Tufte-preferred alternative.

## Process

### 1. Clarify the question
State the single question the visual must answer. For decision support this is usually "Compared to what?" — which options, on which dimensions, and what would change the choice.

### 2. Pick the chart from the data shape
| Data shape | Default chart |
|---|---|
| Change over time | Line / sparkline; slopegraph for before→after |
| Compare categories | Sorted horizontal bars (zero baseline) |
| Compare options × dimensions (a decision) | Small multiples, dot plot, or a clean scored matrix |
| Distribution | Strip plot, histogram, or boxplot stripped of chartjunk |
| Part-to-whole | Stacked bar or sorted bars — **not** a pie |
| Two variables | Scatter with range frame |
| Trade-off frontier | Scatter with the efficient options labeled |

### 3. Strip to data-ink
Apply principles 2–4 and the kill list. Default styling: thin gray axes, no frame, faded gridlines (or none), direct labels over legends, accent color reserved for the focal value.

### 4. Verify integrity
Run the checklist below before delivering.

### 5. Output (Codex is terminal-first)
- **Default:** write a **self-contained HTML/SVG file** to the working directory (e.g. `tufte-<topic>.html`, inline SVG, no external deps). Report the path so the user can open it. Echo a compact text/ASCII version inline when it helps the conversation.
- **React project:** if the repo uses React, emit a **Recharts** component (or **D3-in-React** for dot plots/slopegraphs) with a Tufte theme, placed in an appropriate file.
- **Quick decision aid:** a small inline SVG or a tight markdown table beside a one-paragraph explanation is often the whole deliverable — don't over-build.

## Output Format

```markdown
## Visual: {what question it answers}

{the chart — path to the self-contained HTML/SVG file, or the React component}

**Read it like this:** {1–2 sentences: what the reader should take away}
**What would change the decision:** {only in decision-support mode — the threshold or assumption that flips the answer}
```

## Quality Checklist

Before delivering any visual:
- [ ] It answers one clear question
- [ ] Lie factor 0.95–1.05; bars start at zero; scales consistent
- [ ] Non-data-ink erased (frames, heavy gridlines, redundant legends gone)
- [ ] Each quantity encoded once
- [ ] Focal value carries the only strong contrast; everything else is quiet
- [ ] Labels sit near the data, not in a distant legend
- [ ] Nothing from the kill list survives unrequested
- [ ] (Decision mode) The chart actually helps the choice — it isn't decoration
- [ ] Output file is self-contained and its path is reported

## Anti-Patterns

- Don't modify Tufte's ten principles — they are the fixed point of this skill
- Don't force a chart onto a decision that's clearer in a sentence
- Don't add color, 3D, or gridlines to look polished — polish is what you removed
- Don't bury the answer in a legend the reader has to decode
- Don't truncate an axis to make a difference look bigger than it is
- Don't depend on external CDNs/fonts in the HTML output — keep it self-contained
- Don't wait to be asked when the user is clearly stuck on a comparison — offer the visual, but keep it small
