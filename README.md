# Claude Code Output Styles

Custom [output styles](https://docs.claude.com/en/docs/claude-code/output-styles) for [Claude Code](https://claude.com/claude-code). Output styles change how Claude formats and structures its responses, without changing what tools it can use.

## Styles

### BLUF (`output-styles/bluf.md`)

Bottom Line Up Front. Every response leads with the answer, decision, or required action in 1-2 sentences — before any explanation, research narration, or process detail. Supporting points (if any) follow, most important first, one topic per bullet. Active voice throughout; every response ends with the next action or decision needed.

Good fit if you want Claude to read like a status update, not an essay.

## Install

Output styles are markdown files with a frontmatter header, loaded from `~/.claude/output-styles/` (user-level, all projects) or `.claude/output-styles/` (project-level).

**User-level (recommended):**

```bash
mkdir -p ~/.claude/output-styles
curl -o ~/.claude/output-styles/bluf.md \
  https://raw.githubusercontent.com/<your-username>/claude-code-output-styles/main/output-styles/bluf.md
```

**Or clone the whole repo:**

```bash
git clone https://github.com/<your-username>/claude-code-output-styles.git
cp claude-code-output-styles/output-styles/*.md ~/.claude/output-styles/
```

**Project-level:** copy the same file into `.claude/output-styles/` inside a specific project instead, if you only want it there.

## Use

Inside Claude Code:

```
/config outputStyle=bluf
```

Or select it interactively via `/config` → **Output style**.

The change takes effect on your next session or after `/clear` — output style is baked into the system prompt at session start, not applied mid-turn.

Switch back anytime with `/config outputStyle=default` (or pick another style the same way).

> Note: the older standalone `/output-style` command was deprecated in Claude Code v2.1.73 and removed in v2.1.91. Use `/config` instead.

## Writing your own

An output style is a markdown file with YAML frontmatter:

```markdown
---
name: MyStyle
description: One-line summary shown in the /output-style picker
keep-coding-instructions: true
---

Instructions for how Claude should format and structure its responses go here.
```

- `name` — display name in the picker.
- `description` — shown next to the name in the picker.
- `keep-coding-instructions` — set `true` to keep Claude's default coding-related system prompt behavior alongside your formatting rules; `false` replaces it entirely.

Drop the file in `~/.claude/output-styles/` and it shows up in `/output-style`.

## License

MIT — see [LICENSE](LICENSE).
