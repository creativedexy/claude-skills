# Codex skills

Agent Skills for the OpenAI **Codex** CLI. Same `SKILL.md` format as Claude skills
(YAML frontmatter + markdown body), but Codex discovers them from `$CODEX_HOME/skills`
(default `~/.codex/skills/`) and can invoke them **implicitly or explicitly**.

## Skills

- **`tufte`** — Edward Tufte's data-visualization principles, plus a proactive
  decision-support mode (offer a clean visual when weighing options or trade-offs).
  Tufte's ten principles are preserved verbatim from the Claude version; only the
  triggering and output guidance are adapted for Codex's terminal-first workflow.

  ```
  tufte/
  ├── SKILL.md                 # triggers, process, output, checklist (lean)
  ├── references/principles.md # Tufte's ten rules (verbatim) + kill list
  └── agents/openai.yaml       # Codex metadata; allow_implicit_invocation: true
  ```

## Install (wire into Codex)

Copy the whole skill directory (it's multi-file now):

```bash
mkdir -p ~/.codex/skills
cp -r codex/skills/tufte ~/.codex/skills/
```

Then in a Codex session it triggers automatically (implicit invocation is enabled),
or invoke it explicitly with `$tufte`. No `config.toml` change is required — skills
under `~/.codex/skills/` are auto-discovered.
