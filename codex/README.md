# Codex skills

Agent Skills for the OpenAI **Codex** CLI. Same `SKILL.md` format as Claude skills
(YAML frontmatter + markdown body), but Codex discovers them from `$CODEX_HOME/skills`
(default `~/.codex/skills/`) and can invoke them **implicitly or explicitly**.

## Skills

- **`tufte`** — Edward Tufte's data-visualization principles, plus a proactive
  decision-support mode (offer a clean visual when weighing options or trade-offs).
  Tufte's ten principles are preserved verbatim from the Claude version; only the
  triggering and output guidance are adapted for Codex's terminal-first workflow.

## Install (wire into Codex)

```bash
mkdir -p ~/.codex/skills/tufte
cp codex/skills/tufte/SKILL.md ~/.codex/skills/tufte/SKILL.md
```

Then in a Codex session it triggers automatically, or invoke explicitly via the slash menu.
No `config.toml` change is required — skills under `~/.codex/skills/` are auto-discovered.
