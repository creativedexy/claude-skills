# Tufte's Ten Rules + Kill List

These are Edward Tufte's data-visualization principles, preserved verbatim in intent.
**Do not modify them.** Apply every rule to every visual the `tufte` skill produces.

## Ten Rules

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
