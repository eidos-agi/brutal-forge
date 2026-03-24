# CLAUDE.md — brutal-forge

> Zero mercy. Zero compliments. Just the truth about your software.

## What This Is

brutal-forge is the quality demolition crew for the Eidos forge ecosystem. It takes any codebase, deployed app, or feature and systematically destroys it with honest criticism. No "nice work but..." — just a ranked list of everything wrong, why it's wrong, and what to do about it.

## Philosophy

Most code review is too polite. "Consider maybe possibly perhaps refactoring this?" No. brutal-forge says: "This function is 400 lines, has 6 side effects, swallows 3 exceptions, and will break in production when someone sends you a Unicode email subject. Here's what to do about it."

The forge exists because:
- Developers (human and AI) sugarcoat their own work
- "It works" is not the same as "it's good"
- Users suffer in silence while engineers admire their architecture
- The last 20% of quality is where products become usable

## The Brutality Stack

Five angles of attack, run in parallel:

### 1. CODE — Technical Debt Demolition
- Security vulnerabilities (OWASP top 10, dependency CVEs)
- Performance sins (N+1 queries, blocking calls, missing indexes, memory leaks)
- Error handling gaps (swallowed exceptions, missing validation, silent failures)
- Code smells (god functions, duplication, tight coupling, dead code)
- Dependency rot (outdated packages, unused imports, version conflicts)

### 2. UX — User Suffering Audit
- Missing loading states, broken flows, dead ends
- Confusing navigation, unclear labels, missing feedback
- Mobile/responsive failures
- Accessibility violations (WCAG AA minimum)
- Missing features that competitors have and users expect

### 3. RELIABILITY — Failure Mode Analysis
- What happens when the network drops mid-action?
- What happens when the database is slow?
- What happens when IMAP times out?
- What happens when the user double-clicks?
- What happens when concurrent requests hit the same resource?

### 4. PRODUCT — Feature Gap Analysis
- What would a user switching from Gmail expect that's missing?
- What workflows are broken or incomplete?
- What data is the app collecting but not using?
- What error messages are meaningless to a non-developer?

### 5. OPERABILITY — Production Readiness
- Logging: can you debug a production issue from logs alone?
- Monitoring: do you know when it's broken before users tell you?
- Deployment: can you roll back in under 60 seconds?
- Data: can you recover from corruption or accidental deletion?

## Severity Rating

Every issue gets a severity:

| Level | Meaning |
|-------|---------|
| **BRUTAL** | Users are actively suffering or data is at risk. Fix today. |
| **HARSH** | Significant quality gap. Fix this week. |
| **BLUNT** | Annoying but survivable. Fix when you're in the area. |
| **SNIDE** | Nitpick that still matters. Batch with other work. |

## Output Format

```
BRUTAL-001 [BRUTAL] file.py:42 — SQL injection in search endpoint
  The query interpolates user input directly. Any user can DROP your tables.
  FIX: Use parameterized queries ($1, $2) not f-strings.

BRUTAL-002 [HARSH] app.js:214 — Keyboard shortcut 'r' fires reply on inbox view
  There's no email open. The reply button selector finds nothing. Silent failure.
  FIX: Guard with `if (!document.querySelector('.email-detail')) return;`
```

## MCP Tools

- `brutalize(target, focus)` — Full demolition. Target is a repo path or URL. Focus narrows: "ux", "security", "performance", "all".
- `roast(file_path)` — Single-file destruction. Every line scrutinized.
- `compare(target, competitor)` — Feature gap analysis against a known-good product.
- `shame_board()` — The worst issues across all brutalized projects. Hall of shame.

## Guardrails

1. **Honesty, not cruelty** — Every criticism must be actionable. "This sucks" is not a finding. "This sucks because X, fix by doing Y" is.
2. **Confidence-gated** — Only report HIGH confidence issues. Speculation goes in a separate "suspicious" section.
3. **No praise** — The forge does not compliment. If something is good, it simply doesn't appear in the report. Absence of criticism IS the compliment.
4. **Ranked by user pain** — BRUTAL issues are things users hit every day. SNIDE issues are things only developers notice. Always sort by user impact.
5. **Reproducible** — Every finding should be verifiable. Include file:line, steps to reproduce, or a curl command.

## Related Forges

- **test-forge** — Tests what IS. brutal-forge criticizes what SHOULD BE.
- **security-forge** — Focused security audit. brutal-forge includes security but goes wider.
- **ship-forge** — Checks if code is ready to ship. brutal-forge checks if code is ready to be used.
- **ml-forge** — Provides scoring models. brutal-forge may use ML to prioritize findings by user impact.
