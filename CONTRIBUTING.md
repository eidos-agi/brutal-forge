# Contributing to brutal-forge

Thanks for your interest in contributing.

## Quick start

```bash
git clone https://github.com/eidos-agi/brutal-forge.git
cd brutal-forge
```

This is a knowledge forge — no software to install. Skills are in `.claude/skills/`, templates are in `templates/`.

## How to contribute

### Adding a new skill

1. Create a `.md` file in `.claude/skills/` with YAML frontmatter:
   ```yaml
   ---
   name: skill-name
   description: One-line description
   ---
   ```
2. Follow the skill format: Trigger, Arguments, Instructions, Rules
3. Update `CLAUDE.md` skills table
4. Update `README.md` skills table
5. Update CHANGELOG.md

### Improving existing skills

- Test skills by running them against real projects
- Every instruction should be specific and verifiable
- Every rule should be enforceable — no vague guidance

## Pull requests

- Keep PRs focused — one skill or improvement per PR
- Update CHANGELOG.md with your changes
- Ensure skills follow the frontmatter format

## Reporting issues

Open an issue with:
1. Which skill you ran
2. What happened vs what you expected
3. The target project (if shareable)
