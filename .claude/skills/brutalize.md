---
name: brutalize
description: Full 5-angle codebase demolition — code, UX, reliability, product, ops
---

# /brutalize — Full Codebase Demolition

Systematically destroy a codebase or deployed app with honest criticism across 5 angles. No compliments. Every finding is actionable, confidence-gated, and ranked by user pain.

## Trigger

User says `/brutalize` or asks to brutalize, tear apart, roast, or demolish a project.

### Arguments

- `<target>` — required. Repo path, service name, or "this" for current working directory.
- `<focus>` — optional. Narrows the attack: "code", "ux", "reliability", "product", "ops", or "all" (default).

## Instructions

### Step 1: Identify the Target

If target is "this" or omitted, use the current working directory. Read `CLAUDE.md` to understand the project.

### Step 2: Launch Parallel Attacks

Launch up to 3 agents in parallel using the Agent tool. Each agent gets a specific angle:

**Agent A — Code + Security** (subagent_type: `feature-dev:code-reviewer`)
Prompt the agent to be brutally honest. Find: SQL injection, XSS, CSRF gaps, N+1 queries, blocking calls, swallowed exceptions, god functions, dead code, dependency rot. HIGH confidence only. Include file:line references.

**Agent B — UX + Product** (subagent_type: `Explore`)
Read every template, every JS interaction, every CSS rule, every route handler. Find: missing loading states, broken flows, dead ends, accessibility violations, mobile failures, missing features competitors have. No mercy.

**Agent C — Reliability + Ops** (subagent_type: `Explore`)
Trace every failure path. What happens when: network drops, DB is slow, external service times out, user double-clicks, concurrent requests, disk full, credentials expire? Check logging, monitoring, rollback capability.

If `focus` is set, only launch the relevant agent(s).

### Step 3: Compile the Demolition Report

Merge findings from all agents. Assign severity:

| Level | Criteria |
|-------|----------|
| **BRUTAL** | Users actively suffering OR data at risk. Fix today. |
| **HARSH** | Significant quality gap visible to users. Fix this week. |
| **BLUNT** | Annoying but survivable. Fix when in the area. |
| **SNIDE** | Nitpick that still matters. Batch with other work. |

### Step 4: Format Output

```
## BRUTALIZATION REPORT — <project name>

**<N> findings. <brutal count> brutal, <harsh count> harsh, <blunt count> blunt, <snide count> snide.**

### BRUTAL

BRUTAL-001 [BRUTAL] file.py:42 — <title>
  <what's wrong and why it hurts users>
  FIX: <specific actionable fix>

### HARSH
...
```

Sort within each section by user pain (worst first). Number findings sequentially across all sections (BRUTAL-001 through BRUTAL-N).

### Step 5: Save the Report

Always save the report. This is not optional — `/shame-board` and future improvement tracking depend on it.

1. Create `.brutal-forge/` directory in the target project if it doesn't exist
2. Write the report to `.brutal-forge/last-report.md` (overwrite previous)
3. Append a summary line to `.brutal-forge/history.jsonl`:
   ```json
   {"date": "2026-03-29", "findings": 12, "brutal": 3, "harsh": 5, "blunt": 3, "snide": 1}
   ```

### Step 6: Offer Next Steps

After saving, offer:
1. "Create ike tasks for BRUTAL + HARSH findings?" — converts top findings to executable tasks
2. "Fix the BRUTAL issues now?" — start coding fixes immediately

## Rules

- **No praise.** If something is good, it doesn't appear. Absence of criticism IS the compliment.
- **HIGH confidence only** in the main report. Speculation goes in a "Suspicious" section at the bottom.
- **Every finding must have a FIX line.** "This sucks" is not a finding. "This sucks because X, fix by doing Y" is.
- **Ranked by user pain**, not developer aesthetics. A missing loading state that confuses users outranks a code smell.
- **Include file:line** for every finding. If it's a deployed app, include the URL or curl command.
- **Never soften language.** No "consider", "perhaps", "might want to". State the problem. State the fix.
