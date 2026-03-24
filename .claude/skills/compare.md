---
name: compare
description: Feature gap analysis against a competitor — find every missing capability
---

# /compare — Feature Gap Analysis

Compare a project against a known-good competitor or standard. Find every feature gap, every UX regression, every missing table-stakes capability.

## Trigger

User says `/compare <target> <competitor>` or asks to compare their app against something.

### Arguments

- `<target>` — required. The project to criticize (repo path or "this").
- `<competitor>` — required. The gold standard to compare against (e.g., "Gmail", "Linear", "Stripe Dashboard").

## Instructions

### Step 1: Understand the Target

Read the target's CLAUDE.md, templates, routes, and UI. Build a feature inventory.

### Step 2: Build the Competitor Feature List

From your knowledge of the competitor, list every feature a user would expect. Organize by category:
- Core functionality
- Navigation and information architecture
- Search and filtering
- Notifications and feedback
- Settings and customization
- Keyboard shortcuts
- Mobile experience
- Accessibility

### Step 3: Gap Analysis

For each competitor feature, check if the target has it:
- **MISSING** — not implemented at all
- **PARTIAL** — exists but incomplete or broken
- **PRESENT** — fully implemented (don't list these — no praise rule)

### Step 4: Format Output

```
## FEATURE GAP: <target> vs <competitor>

**<N> gaps found. <missing> missing, <partial> partial.**

### MISSING (not implemented)
- Email threading / conversation view
- Attachment support (view, download, send)
- Draft auto-save

### PARTIAL (exists but broken/incomplete)
- Search: works but no filters, no pagination, max 20 results
- Keyboard shortcuts: exist but conflict with browser defaults
```

### Step 5: Prioritize

Rank gaps by "how many users would notice on day 1." The features people reach for in the first 5 minutes are the ones that matter most.

## Rules

- Be fair about scope — a personal project isn't expected to match Gmail's 20-year feature set.
- But be honest — if basic features are missing, say so.
- Focus on table-stakes features, not nice-to-haves.
