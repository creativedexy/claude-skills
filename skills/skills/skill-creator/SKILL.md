---
name: skill-creator
description: Creates new Claude skills from scratch. Use when building skills, refining existing skills, or teaching Claude new workflows. Outputs properly formatted SKILL.md files with YAML frontmatter, structured instructions, and anti-patterns.
---

# Skill Creator

You build skills that teach Claude to do specific things well. Meta-instruction for instruction.

## What Makes a Good Skill

### Structure
```
skill-name/
└── SKILL.md
    ├── YAML frontmatter (name, description)
    └── Markdown body (instructions)
```

### The Two Parts

**1. Frontmatter (triggers the skill)**
```yaml
---
name: kebab-case-name
description: What it does. Use when [specific triggers]. Outputs [deliverables].
---
```

**2. Body (executes the skill)**
- Core principles
- Process steps
- Output formats
- Quality checks
- Anti-patterns

## Skill Creation Process

### 1. Define the Job

```markdown
## Skill Definition

**Name:** {kebab-case}
**Purpose:** {one sentence — what does this skill enable?}

**Triggers (when to use):**
- {user says X}
- {context includes Y}
- {task requires Z}

**Outputs:**
- {deliverable 1}
- {deliverable 2}

**NOT for:**
- {what this skill doesn't do}
```

### 2. Map the Workflow

Before writing instructions, map what an expert would do:

```markdown
## Expert Workflow

Step 1: {what they do first}
    ↓
Step 2: {what comes next}
    ↓
Step 3: {decision point — if X then Y}
    ↓
Step 4: {output creation}
    ↓
Step 5: {quality check}
```

### 3. Extract Principles

What rules does the expert follow?

```markdown
## Core Principles

1. **{Principle}** — {why it matters}
2. **{Principle}** — {why it matters}
3. **{Principle}** — {why it matters}
```

Good principles are:
- Actionable (Claude can follow them)
- Memorable (stick in context)
- Non-obvious (not just "do good work")

### 4. Define Inputs

What does Claude need before starting?

```markdown
## Inputs Required

Before starting, confirm you have:
- [ ] {input 1}
- [ ] {input 2}
- [ ] {input 3}
```

### 5. Structure the Process

Break workflow into repeatable steps with templates:

```markdown
## Process

### Step 1: {Name}

{Explanation of what to do}

```markdown
## Template for Output

**Field:** {value}
**Field:** {value}
```

### Step 2: {Name}
...
```

### 6. Define Output Format

What does the final deliverable look like?

```markdown
## Output Format

Deliver to [recipient]:

```markdown
## {Deliverable Name}: {project-name}

### Section 1
{content}

### Section 2
{content}
```
```

### 7. Add Quality Gates

What must be true before delivery?

```markdown
## Quality Checklist

Before delivery:
- [ ] {check 1}
- [ ] {check 2}
- [ ] {check 3}
```

### 8. Document Anti-Patterns

What should Claude NOT do?

```markdown
## Anti-Patterns

- Don't {bad thing} — {why it fails}
- Don't {bad thing} — {why it fails}
```

## Skill Quality Criteria

### Good Skills

| Quality | Test |
|---------|------|
| **Triggerable** | Description includes specific phrases users would say |
| **Scoped** | Clear boundaries — what it does AND doesn't do |
| **Actionable** | Every instruction is something Claude can execute |
| **Templated** | Output formats are structured, not vague |
| **Testable** | Quality checklist has observable criteria |

### Bad Skills

| Problem | Example | Fix |
|---------|---------|-----|
| Vague trigger | "Helps with design" | "Use when defining visual tokens, component specs, or style guides" |
| Impossible instruction | "Never repeat across sessions" | Claude has no cross-session memory — remove |
| Subjective quality | "Make it beautiful" | Define what beautiful means in this context |
| No anti-patterns | — | Add common failure modes |
| Wall of text | 5000 words of prose | Use headers, bullets, templates |

## Output Format

When creating a skill, output:

```markdown
## Skill: {name}

### Validation
- [ ] Name is kebab-case
- [ ] Description includes triggers
- [ ] Process is step-by-step
- [ ] Templates are provided
- [ ] Anti-patterns documented

### SKILL.md

---
name: {name}
description: {description with triggers}
---

# {Title}

{Full skill content}
```

## Skill Iteration

After testing a skill:

```markdown
## Skill Review: {name}

### What Worked
- {observation}

### What Failed
- {observation} → {fix}

### Updates Needed
- {change}
```

## Anti-Patterns

- Don't write skills for things Claude already does well
- Don't include instructions Claude can't follow (cross-session memory)
- Don't use vague quality words without definitions
- Don't skip anti-patterns — failure modes teach more than success
- Don't write prose when templates work better
- Don't forget the "NOT for" section — scope matters
