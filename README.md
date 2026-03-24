# brutal-forge

> Zero mercy. Zero compliments. Just the truth about your software.

## What is this?

brutal-forge is a knowledge forge that packages agent skills for brutally honest software quality review. It attacks from 5 angles — code, UX, reliability, product, and operability — and ranks every finding by user pain.

Part of the [Eidos AGI](https://github.com/eidos-agi) forge ecosystem.

## Skills

| Skill | What It Does |
|-------|-------------|
| `/brutalize` | Full 5-angle demolition of a codebase or deployed app |
| `/roast` | Line-by-line destruction of a single file |
| `/compare` | Feature gap analysis against a competitor |
| `/shame-board` | Worst findings across all brutalized projects |

## Severity Levels

| Level | Meaning |
|-------|---------|
| **BRUTAL** | Users are actively suffering or data is at risk. Fix today. |
| **HARSH** | Significant quality gap. Fix this week. |
| **BLUNT** | Annoying but survivable. Fix when in the area. |
| **SNIDE** | Nitpick that still matters. Batch with other work. |

## Usage

Clone the repo and symlink the skills into your project:

```bash
git clone https://github.com/eidos-agi/brutal-forge.git ~/repos-eidos-agi/brutal-forge
```

Skills are in `.claude/skills/` — Claude Code picks them up automatically when the repo is referenced.

## Related Forges

- **test-forge** — Tests what IS. brutal-forge criticizes what SHOULD BE.
- **security-forge** — Focused security audit. brutal-forge includes security but goes wider.
- **ship-forge** — Checks if code is ready to ship. brutal-forge checks if code is ready to *use*.

## License

MIT
