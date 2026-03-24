---
name: shame-board
description: Worst findings across all brutalized projects — the hall of shame
---

# /shame-board — Hall of Shame

Surface the worst findings across all brutalized projects. The issues that keep coming back, the patterns that never get fixed, the sins that every project commits.

## Trigger

User says `/shame-board` or asks to see the worst findings.

## Instructions

### Step 1: Find All Reports

Look for `.brutal-forge/last-report.md` files across all repos in `~/repos-eidos-agi/` and `~/repos-aic/`. Also check `~/.local/share/brutal-forge/reports/`.

### Step 2: Extract BRUTAL Findings

From each report, pull all BRUTAL-severity findings. Group by pattern:
- **Security sins** — CSRF, injection, session issues
- **UX crimes** — missing feedback, broken flows, accessibility
- **Performance offenders** — N+1, unbounded queries, blocking calls
- **Data risks** — no backups, no soft deletes, silent corruption

### Step 3: Rank by Frequency

The finding that appears in the most projects goes first. Repeat offenders are the real problems — they indicate systemic patterns, not one-off mistakes.

### Step 4: Format

```
## SHAME BOARD — Eidos AGI Ecosystem

### Most Common Sins
1. CSRF missing on POST endpoints (4/7 projects)
2. No loading state feedback (3/7 projects)
3. Session secrets with hardcoded fallbacks (3/7 projects)

### Worst Individual Findings
1. [eidos-mail] SQL injection pattern in Ike filter
2. [eidos-mail] Outbound email missing RFC-required headers
```

## Rules

- This is a learning tool, not a blame tool. The point is pattern recognition.
- If no reports exist yet, tell the user to `/brutalize` some projects first.
