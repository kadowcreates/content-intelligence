# Content Intelligence

Skill that turns talks, training, webinars, lectures, podcasts, and voice notes into structured insight summaries.

Built for learning. Themes, frameworks, mental models, and applications. Not an action tracker. Decisions and owners belong in Meeting Intelligence.

- **Version:** 1.0.0
- **License:** MIT
- **Repo:** https://github.com/kadowcreates/content-intelligence
- **Skill file:** `SKILL.md`
- **Compatible with:** Grok custom skills, Claude Code, OpenCode

## What it does

1. Reads a transcript of informational content.
2. Extracts themes, frameworks, and key ideas with high fidelity.
3. Synthesizes mental models and perspective shifts only where the source supports them.
4. Captures quotes, open questions, and named resources.
5. Writes a fixed Markdown summary, plus a Word doc unless you ask for Markdown only.

It does not invent frameworks. If the speaker did not say it, it does not appear.

## Modes

| Mode | When to use |
|---|---|
| **Concise** | Short talk, or you only want the high-level pass. |
| **Standard** | Default. Most conference talks and training sessions. |
| **Deep** | Long-form training or dense technical material. More synthesis. |

Say `content-intelligence in deep mode` or `concise summary using content-intelligence`.

Ask for `JSON mode` or `structured data` when you want a machine-readable block after the Markdown.

## Install

### Grok

```text
~/.grok/skills/content-intelligence/SKILL.md
```

### Claude Code / OpenCode

```text
.claude/skills/content-intelligence/SKILL.md
```

Keep the folder name `content-intelligence` so it matches the frontmatter `name`.

### Update from this repo

```bash
git clone https://github.com/kadowcreates/content-intelligence.git
cp content-intelligence/SKILL.md ~/.grok/skills/content-intelligence/SKILL.md
```

## Usage

```text
Summarize this with content-intelligence:

[paste transcript]
```

## File map

```text
content-intelligence/
  README.md
  LICENSE
  SKILL.md
```

## Version history

| Version | Date | Changes |
|---|---|---|
| **v1.0.0** | **2026-10-02** | Initial publish. Insight-oriented summary contract, depth modes, JSON export, Word doc generation. |

## License

MIT. See `LICENSE`.
