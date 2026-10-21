# skills

Ethan Ratnofsky's agent skills, written in the open [Agent Skills](https://agentskills.io) format (`SKILL.md`). They work with Claude and with any other agent that supports the standard.

## Skills

| Skill | What it does |
| --- | --- |
| [`product-research`](skills/product-research/SKILL.md) | Researches and recommends the best product or service for a need, weighting independent lab tests, long-term expert reviews, and owner reports, with a reliability veto, verified current prices, and a citation on every key claim. |

## Install

**Claude Code**

```
/plugin marketplace add ethanratnofsky/skills
/plugin install ethan-skills@ethanratnofsky
```

**Claude apps (web, desktop, Cowork):** download the packaged `.skill` file from this repo's Releases and upload it in the Skills section of Claude's settings.

**Other agents (Codex, Cursor, Gemini CLI, and others):**

```
npx skills add ethanratnofsky/skills
```

Or copy `skills/<name>/` into your agent's skills directory; check your agent's docs for the location.

## Layout

```
.claude-plugin/
  plugin.json          # Claude Code plugin manifest (optional layer)
  marketplace.json     # Claude Code marketplace catalog (optional layer)
skills/
  <name>/
    SKILL.md           # Required: frontmatter + instructions
    references/        # Loaded only when SKILL.md points to them
    evals/evals.json   # Test prompts for checking the skill's output
```

Everything under `skills/` follows the open standard. The `.claude-plugin/` folder only adds one-command installs in Claude Code; other agents ignore it.

## Adding or changing a skill

1. Create `skills/<name>/SKILL.md`. The `name` in the frontmatter must match the folder name (lowercase letters, numbers, hyphens).
2. Put long or category-specific material in `references/` and link each file from `SKILL.md`, one level deep.
3. Add realistic test prompts to `evals/evals.json`.
4. Validate with `skills-ref validate skills/<name>` and `claude plugin validate .`
5. Bump `version` in `.claude-plugin/plugin.json` and in the skill's `metadata`. Claude Code uses the plugin version to detect updates.

## License

[MIT](LICENSE)
