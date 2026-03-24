# /roast — Single-File Destruction

Line-by-line demolition of a single file. Every smell, every gap, every risk — called out with zero mercy.

## Trigger

User says `/roast <file_path>` or asks to roast/review a specific file.

### Arguments

- `<file_path>` — required. The file to destroy.

## Instructions

### Step 1: Read the File

Read the entire file. Understand its role in the project (check CLAUDE.md, imports, callers).

### Step 2: Destroy It

Go through every function, every block, every line. Find:

- **Security**: injection, XSS, auth bypass, secrets, unsafe deserialization
- **Performance**: O(n^2) loops, N+1 patterns, blocking calls, unbounded queries, memory leaks
- **Error handling**: bare except, swallowed errors, missing validation, unclear error messages
- **Logic**: off-by-one, race conditions, null derefs, type mismatches, unreachable code
- **Style**: god functions (>50 lines), deep nesting (>3 levels), misleading names, dead code
- **Accessibility**: missing ARIA, unlabeled inputs, color-only indicators
- **Hardcoded values**: magic numbers, hardcoded URLs, embedded credentials

### Step 3: Format as Line-by-Line Roast

```
## ROAST: <filename>
**<N> findings across <M> lines.**

Line 42: `query = f"SELECT * FROM {table}"` — SQL injection. Use parameterized queries.
Line 87: `except Exception: pass` — Swallowing every error including KeyboardInterrupt. At minimum catch specific exceptions.
Line 134-189: `def process_everything()` — 55-line god function with 4 side effects. Split by responsibility.
```

### Step 4: Summary

End with a brutal one-liner assessment:
- "This file is a liability. 12 findings, 3 of which are security risks."
- "Functional but fragile. 6 findings, mostly error handling gaps."

## Rules

- Read the ENTIRE file. Don't skim.
- Every finding must reference the exact line number.
- No praise. No "the rest looks fine." Just findings.
- If the file is clean, say: "Nothing to report. (This is the highest compliment brutal-forge gives.)"
