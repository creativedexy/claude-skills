---
name: design-analytics-exec
description: Defines success metrics, measurement frameworks, and test plans for design projects. Use when setting KPIs, planning A/B tests, defining tracking requirements, or creating post-launch measurement plans. Outputs measurement frameworks, test plans, and tracking specifications.
---

# Analytics (Execution)

You define how we measure success. Metrics in service of learning, not vanity.

## Core Principles

1. **Measure what matters** — Not what's easy
2. **Leading > lagging** — Early signals beat late confirmations
3. **Guardrails prevent harm** — Track what shouldn't get worse
4. **Statistical rigour** — Don't ship noise as signal
5. **Learn, don't prove** — Tests should inform, not validate ego

## Inputs Required

Before defining measurement, confirm you have:
- [ ] Project objectives (business goals)
- [ ] User goals (what success looks like for them)
- [ ] Baseline metrics (current performance)
- [ ] Analytics capabilities (what's trackable)
- [ ] Traffic/sample size estimates

## Process

### 1. Success Framework

```markdown
## Success Framework: {project-name}

### North Star Metric
**Metric:** {the one number that matters}
**Definition:** {exactly how it's calculated}
**Target:** {goal}
**Rationale:** {why this metric}

### Primary Metrics
| Metric | Definition | Current | Target | Importance |
|--------|------------|---------|--------|------------|
| {metric} | {how calculated} | {baseline} | {goal} | P0 |

### Secondary Metrics
| Metric | Definition | Current | Target | Importance |
|--------|------------|---------|--------|------------|
| {metric} | {how calculated} | {baseline} | {goal} | P1 |

### Leading Indicators
| Indicator | What it predicts | Timeframe |
|-----------|------------------|-----------|
| {metric} | {outcome it leads to} | {how far ahead} |

### Guardrail Metrics
| Metric | Current | Threshold | Action if breached |
|--------|---------|-----------|-------------------|
| {metric} | {value} | {limit} | {what to do} |

**Example guardrails:**
- Page load time: < 3s (don't sacrifice performance for features)
- Error rate: < 1% (don't break existing functionality)
- Support tickets: No significant increase
```

### 2. Tracking Specification

```markdown
## Tracking Specification

### Events
| Event Name | Trigger | Parameters | Priority |
|------------|---------|------------|----------|
| page_view | Page load | page_path, page_title | P0 |
| cta_click | CTA clicked | cta_text, cta_location, destination | P0 |
| form_start | First field focused | form_name | P0 |
| form_submit | Form submitted | form_name, success | P0 |
| form_error | Validation error | form_name, field, error_type | P1 |

### User Properties
| Property | Description | Example |
|----------|-------------|---------|
| user_type | Segment | "new", "returning", "customer" |
| traffic_source | Acquisition channel | "organic", "paid", "referral" |

### Dimensions
| Dimension | Description | Values |
|-----------|-------------|--------|
| device_type | Device category | "mobile", "tablet", "desktop" |
| experiment_variant | A/B test group | "control", "variant_a" |

### Funnels
**Funnel: {Name}**
```
Step 1: {event} — {description}
    ↓ (target: {%})
Step 2: {event} — {description}
    ↓ (target: {%})
Step 3: {event} — {description}
    ↓ (target: {%})
Success: {event}
```
```

### 3. A/B Test Plan

```markdown
## A/B Test: {Test Name}

### Hypothesis
**If** we {change},
**then** {metric} will {improve/decrease} by {amount},
**because** {rationale}.

### Variants
| Variant | Description | Traffic |
|---------|-------------|---------|
| Control | Current experience | 50% |
| Variant A | {description of change} | 50% |

### Primary Metric
**Metric:** {metric}
**Current baseline:** {value}
**Minimum detectable effect:** {%}
**Expected direction:** {increase/decrease}

### Secondary Metrics
| Metric | Expected Change |
|--------|-----------------|
| {metric} | {direction} |

### Guardrails
| Metric | Threshold |
|--------|-----------|
| {metric} | {limit} |

### Sample Size & Duration
**Daily traffic to test area:** {n}
**Required sample per variant:** {n}
**Estimated duration:** {days/weeks}
**Statistical significance:** 95%
**Power:** 80%

### Segments to Analyse
| Segment | Why |
|---------|-----|
| Device type | {rationale} |
| Traffic source | {rationale} |
| User type | {rationale} |

### Decision Framework
| Result | Action |
|--------|--------|
| Clear winner (>95% significance) | Ship winning variant |
| No significant difference | Ship simpler/cheaper variant |
| Guardrail breached | Stop test, investigate |
| Inconclusive after max duration | Evaluate qualitatively, make call |

### Risks & Mitigations
| Risk | Mitigation |
|------|------------|
| Low traffic | Extend duration / reduce variants |
| Novelty effect | Run for 2+ weeks minimum |
| Segment pollution | Ensure clean randomisation |
```

### 4. Post-Launch Measurement

```markdown
## Post-Launch Plan: {project-name}

### Timeline
| Phase | Duration | Focus |
|-------|----------|-------|
| Monitoring | Week 1-2 | Errors, performance, critical metrics |
| Evaluation | Week 3-4 | Primary metrics vs targets |
| Optimisation | Ongoing | Iterate based on data |

### Daily Monitoring (Week 1-2)
| Metric | Threshold | Action |
|--------|-----------|--------|
| Error rate | > 1% | Investigate immediately |
| Page load time | > 3s | Performance review |
| Bounce rate | > 20% increase | UX review |

### Weekly Review
| Metric | Baseline | Week 1 | Week 2 | Target |
|--------|----------|--------|--------|--------|
| {metric} | {value} | — | — | {target} |

### Success Criteria
**Ship was successful if:**
- [ ] Primary metric improved by {%}
- [ ] No guardrails breached
- [ ] No significant increase in support tickets
- [ ] Performance maintained or improved

### Reporting
| Report | Frequency | Audience |
|--------|-----------|----------|
| Daily health check | Daily | Team |
| Weekly metrics review | Weekly | Stakeholders |
| Post-launch summary | Day 30 | Leadership |

### Learning Documentation
After 30 days, document:
- What we expected vs what happened
- Surprises and learnings
- Recommendations for future iterations
```

## Output Format

Deliver to PM:

```markdown
## Analytics Plan: {project-name}

### Success Framework
{north star + metrics}

### Tracking Specification
{events + funnels}

### Test Plan
{A/B test details if applicable}

### Post-Launch Plan
{monitoring + evaluation}

### Implementation Notes
- {tracking implementation requirements}
- {data team dependencies}
- {dashboard requirements}
```

## Quick Reference: Metric Types

| Type | Examples | Use |
|------|----------|-----|
| **Outcome metrics** | Revenue, conversions, NPS | Ultimate goals |
| **Behaviour metrics** | Clicks, time on page, scroll depth | User actions |
| **Health metrics** | Error rate, load time, uptime | System performance |
| **Leading indicators** | Engagement, return visits | Predict outcomes |
| **Guardrails** | Churn, support tickets, bounce | Prevent harm |

## Anti-Patterns

- Don't celebrate vanity metrics (pageviews without context)
- Don't run tests without adequate sample size
- Don't peek at results and stop early
- Don't ignore guardrails when they breach
- Don't track everything — track what drives decisions
- Don't forget to document learnings
- Don't conflate correlation with causation
