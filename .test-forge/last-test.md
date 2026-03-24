# repo at /Users/dshanklinbv/repos-eidos-agi/brutal-forge

**Target:** /Users/dshanklinbv/repos-eidos-agi/brutal-forge
**Type:** repo
**Tested as:** Software Engineer
**Last tested:** 2026-03-24 15:22 UTC
**Status:** MISCONFIGURED (20/23 checks passed)
**Rounds:** 2
**Test suite:** `/Users/dshanklinbv/repos-eidos-agi/brutal-forge/.test-forge/suites/Users-dshanklinbv-repos-eidos-agi-brutal-forge.yaml`

## What "working" means
imports work, tests pass, repo is clean

## What's working
- **skills directory exists with skill files** — passed (8.1ms) — Forge Standard requires .claude/skills/ with actual skill files
- **templates directory exists with template files** — passed (6.0ms) — Forge Standard requires templates/ directory
- **visionlog initialized** — passed (5.9ms) — Forge Standard requires visionlog to be initialized
- **visionlog has vision.md** — passed (4.4ms) — Visionlog should have a vision statement defined
- **no pyproject.toml (forge not software)** — passed (2.8ms) — Forge Standard: no software artifacts — forges are knowledge, not packages
- **no setup.py or package.json (forge not software)** — passed (3.1ms) — Forge Standard: no CLI, no package — forges are pure knowledge
- **LICENSE file exists and has content** — passed (4.5ms) — Forge Standard requires LICENSE file
- **gitignore exists** — passed (4.1ms) — Forge Standard requires .gitignore
- **git working tree is clean** — passed (8.9ms) — Forge Standard requires git clean — no uncommitted changes
- **pushed to GitHub remote** — passed (6.9ms) — Forge Standard requires repo pushed to GitHub
- **local branch matches remote (no unpushed commits)** — passed (9.0ms) — Forge must be fully pushed — no local-only commits
- **skills match README advertised skills** — passed (4.8ms) — README advertises brutalize, roast, compare, shame-board — verify skill files exist for them
- **no Dockerfile (forge not deployable)** — passed (2.7ms) — Forges are knowledge repos, not deployable services
- **registered in forge-forge registry** — passed (36.0ms) — Forge Standard requires registration in the forge-forge registry
- **skill files are markdown not other formats** — passed (6.8ms) — Verify skill files are .md format as expected by Claude Code skill loading.
- **CLAUDE.md references skills directory correctly** — passed (5.0ms) — CLAUDE.md should describe the skills this forge provides so Claude Code knows how to use them.
- **visionlog has guardrails defined** — passed (8.0ms) — Forge standard expects visionlog to be initialized with guardrails, not just vision.md.
- **no Python or Node runtime files leaked in** — passed (5.4ms) — Forges are knowledge packages, not software. No runtime code should exist at root level.
- **gitignore has sensible entries for a forge** — passed (4.2ms) — Gitignore should at minimum exclude OS artifacts. Verify it has reasonable forge-appropriate entries.
- **LICENSE is a recognized open source license** — passed (4.0ms) — LICENSE should contain a real license text, not just a placeholder.

## What's broken
- **skill files have valid frontmatter**
  - Output does not contain '---'
  - Why this matters: Skill files need YAML frontmatter to be picked up by Claude Code
- **skill files frontmatter re-check (read actual content)**
  - Output does not contain '---'
  - Why this matters: Previous frontmatter check failed. Need to see actual file contents to determine if files lack frontmatter or if the test pattern was wrong.
- **templates are non-empty markdown files**
  - Output does not contain 'total'
  - Why this matters: Templates should have substantial content, not be empty placeholder files.

## Probable root causes
- Skill files were written starting with `# /name` markdown headers instead of YAML frontmatter blocks
- templates/ directory was created as an empty placeholder during forge scaffolding but never populated with actual template files

## What to do about it
- Add YAML frontmatter to each skill file in /Users/dshanklinbv/repos-eidos-agi/brutal-forge/.claude/skills/*.md — prepend `---\nname: skillname\ndescription: one-line description\n---\n` before the existing content
- Add at least one template file to /Users/dshanklinbv/repos-eidos-agi/brutal-forge/templates/ (e.g., a demolition report template or shame-board output template), or remove the empty directory if templates are not applicable to this forge
- Commit and push the fixes, then re-run the forge standard checks

## Watch out for
- 302 on authenticated endpoints is correct behavior, not a failure
- 405 means wrong HTTP method, not a broken endpoint
- 422 on POST without body means validation is working correctly

## When it's fixed
All 23 checks should pass. Specifically:
- skill files have valid frontmatter should pass
- skill files frontmatter re-check (read actual content) should pass
- templates are non-empty markdown files should pass

## For the next robot

**Test suite:** `/Users/dshanklinbv/repos-eidos-agi/brutal-forge/.test-forge/suites/Users-dshanklinbv-repos-eidos-agi-brutal-forge.yaml` — run `test_this("/Users/dshanklinbv/repos-eidos-agi/brutal-forge")` to execute it.
The suite is the artifact. It persists. Add to it, don't start over.

**To retest:** `test_this("/Users/dshanklinbv/repos-eidos-agi/brutal-forge")` or `test_this("/Users/dshanklinbv/repos-eidos-agi/brutal-forge", playbook="security")`
