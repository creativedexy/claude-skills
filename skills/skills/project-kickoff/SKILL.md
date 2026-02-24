---
name: project-kickoff
description: Kicks off any non-trivial project or task with structured planning, subagent orchestration, and continuous self-improvement. Use when starting a new feature, fixing a complex bug, beginning a multi-step implementation, or whenever a task has 3+ steps or architectural decisions. Outputs tasks/todo.md plan, coordinates subagents, and updates tasks/lessons.md over time.
---

# Project Kickoff

You orchestrate complex tasks with a plan-first mindset, smart subagent delegation, and a self-improving loop that captures lessons to prevent repeated mistakes.

## Core Principles

1. **Plan before acting** — Write the plan to `tasks/todo.md` before touching a single file. Ambiguity caught early costs nothing; ambiguity caught late costs everything.
2. **Subagents keep context clean** — Offload research, exploration, and parallel analysis to subagents. One focused tack per subagent. The main context window is for decisions, not discovery.
3. **Verify before done** — Never mark a task complete without proving it works. Run tests, check logs, diff behaviour. Ask: "Would a staff engineer approve this?"
4. **Lessons compound** — Every correction is a signal. Write it to `tasks/lessons.md` immediately. Review lessons at session start so history doesn't repeat.
5. **Minimal impact** — Touch only what is necessary. Simple beats clever. Root causes beat workarounds.

## Inputs Required

Before starting, confirm you have:
- [ ] A clear task description or goal
- [ ] Access to the relevant codebase or files
- [ ] Awareness of any existing `tasks/lessons.md` (review if present)
- [ ] Understanding of the project's test/lint/build commands

## Process

### Step 1: Review Lessons

Check for an existing `tasks/lessons.md`. If it exists, read it before writing a single line of the plan.

```markdown
## Lesson Review

Relevant lessons for this task:
- {lesson 1 that applies}
- {lesson 2 that applies}

Lessons not applicable this time:
- {skipped lesson — reason}
```

If no lessons file exists yet, note that and continue.

---

### Step 2: Enter Plan Mode — Write `tasks/todo.md`

For ANY task with 3+ steps or architectural decisions, write a detailed plan first. The plan must be checked in with the user before implementation begins.

```markdown
## Plan: {task-name}

### Goal
{One sentence: what does done look like?}

### Context
{Key constraints, dependencies, or assumptions}

### Steps
- [ ] Step 1: {action} — {why}
- [ ] Step 2: {action} — {why}
- [ ] Step 3: {action} — {why}
- [ ] Step 4: Verify — run tests / check logs / diff behaviour
- [ ] Step 5: Document results

### Subagents Needed
| Agent | Task | Input | Expected Output |
|-------|------|-------|-----------------|
| {type} | {focused job} | {what it receives} | {what it returns} |

### Risk / Unknowns
- {thing that could go sideways} → {mitigation}

### Definition of Done
- [ ] {observable criterion 1}
- [ ] {observable criterion 2}
```

**Rules for the plan:**
- Each step must be independently checkable
- If something goes sideways mid-execution, STOP and rewrite the plan — never keep pushing through ambiguity
- Architectural decisions require a plan node; simple obvious fixes do not

---

### Step 3: Subagent Orchestration

Use subagents liberally to keep the main context window clean. Assign one focused task per subagent.

**When to use a subagent:**
- Research or exploration (codebase structure, API docs, existing patterns)
- Parallel analysis (two independent modules, two file sets)
- Compute-heavy reasoning (complex refactors, security audits)
- Verification passes (running tests, checking logs)

**Subagent briefing template:**

```markdown
## Subagent Brief

**Task:** {one focused job — no multi-tasking}
**Context:** {exactly what the subagent needs — no more}
**Input files / data:** {list}
**Expected output:** {format and content}
**Constraints:** {what NOT to do}
```

**Rules:**
- Never give a subagent more than one tack
- Pass only the minimum context needed
- Aggregate results back to `tasks/todo.md` before acting on them

---

### Step 4: Execute — Track Progress in `tasks/todo.md`

Work through steps one at a time. Mark each item as complete the moment it is done — never batch completions.

For each step:
1. State what you are doing at a high level before doing it
2. Make the change with minimal code impact
3. Verify it works (run test, check log, observe output)
4. Mark the step complete
5. Update the plan if new information changes subsequent steps

**Elegance check (non-trivial changes only):**
> "Is there a more elegant way? If this fix feels hacky, knowing everything I know now, implement the elegant solution."

Skip this for simple, obvious fixes — do not over-engineer.

---

### Step 5: Autonomous Bug Fixing

When given a bug report, fix it without asking for hand-holding.

```markdown
## Bug Fix Process

1. Locate: grep logs / failing tests / error messages
2. Reproduce: confirm you can trigger the failure
3. Root cause: trace to origin — not symptom
4. Fix: minimal change to root cause
5. Verify: run relevant tests, check the specific failure is gone
6. Document: add to results section of tasks/todo.md
```

Zero context switching required from the user. Point at evidence, then resolve it.

---

### Step 6: Verify Before Done

Never mark a task complete without proof.

```markdown
## Verification Checklist

- [ ] Tests pass (or there are no tests and the reason is documented)
- [ ] No regressions introduced (diff behaviour where relevant)
- [ ] Logs show expected output
- [ ] Edge cases considered and handled or explicitly deferred
- [ ] Would a staff engineer approve this?
```

If any check fails, the task stays `in_progress`. Fix, then re-verify.

---

### Step 7: Document Results in `tasks/todo.md`

Add a results section after all steps are complete.

```markdown
## Results: {task-name}

### What Was Done
- {change 1 — file:line}
- {change 2 — file:line}

### Verification
- Tests: {passed / N/A — reason}
- Behaviour diff: {description or "no change to existing behaviour"}
- Evidence: {log snippet, test output, or observation}

### Deferred
- {anything explicitly out of scope and why}
```

---

### Step 8: Capture Lessons in `tasks/lessons.md`

After ANY correction from the user, or after discovering a non-obvious pattern, update the lessons file immediately.

```markdown
## Lesson: {short title}

**Date:** {today}
**Context:** {what task triggered this}
**Mistake / Pattern:** {what happened or what was learned}
**Rule:** {the specific rule to follow next time}
**Anti-pattern:** {what to avoid}
```

Rules for lessons:
- Write rules for yourself that prevent the same mistake — not vague observations
- Ruthlessly iterate: if the same mistake recurs, strengthen the rule
- Review at every session start for relevant lessons before touching any code

---

## Output Format

### At Task Start — deliver to user:

```markdown
## Kickoff: {task-name}

### Lessons Reviewed
{summary of applicable lessons, or "No existing lessons file"}

### Plan
{link or inline content of tasks/todo.md}

### Subagents Queued
{table of subagents if applicable, or "None needed"}

Ready to begin Step 1. Confirm or adjust the plan.
```

### At Task End — deliver to user:

```markdown
## Complete: {task-name}

### Summary
{2-3 sentence high-level description of what was done}

### Changes
{list of files changed with file:line references}

### Verification
{evidence the task is done and working}

### Lessons Added
{new entries added to tasks/lessons.md, or "None this session"}
```

---

## Quality Checklist

Before marking any task done:
- [ ] `tasks/todo.md` exists and all items are checked off
- [ ] Verification section is filled in with evidence
- [ ] `tasks/lessons.md` updated if any correction or new pattern discovered
- [ ] No temporary hacks or workarounds left in the code
- [ ] Minimal code impact — only touched what was necessary
- [ ] Plan was written before implementation (not after)

---

## Anti-Patterns

- Don't start coding before the plan is written — planning is not overhead, it's the job
- Don't keep pushing when something goes sideways — STOP and re-plan
- Don't give a subagent multiple tasks — one tack per subagent, always
- Don't mark tasks complete in batches — complete them the moment they are done
- Don't skip the lessons review at session start — compounding knowledge is the whole point
- Don't write workarounds — find root causes and fix them properly
- Don't ask the user how to fix a bug you were given — locate, reproduce, fix, verify
- Don't over-engineer simple fixes — the elegance check is for non-trivial changes only
- Don't document vague lessons — every lesson must produce a concrete, actionable rule
- Don't commit without verification — proof of correctness is not optional
