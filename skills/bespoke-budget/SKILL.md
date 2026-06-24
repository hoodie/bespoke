---
name: bespoke-budget
description: Shows a summary of the current bespoke complexity budget for the project. Reads bespoke-budget.md and prints a formatted ledger with total line delta and any decisions ponytail flagged as close calls. Use when the user runs /bespoke-budget or asks "what has bespoke spent", "show the budget", "how much has bespoke added", or "what would ponytail cut".
---

# Bespoke Budget

Read `bespoke-budget.md` from the project root.

If the file does not exist, say: "No budget yet. Bespoke hasn't made any
non-trivial type decisions in this project, or the file hasn't been created.
Activate bespoke with `/bespoke` to start tracking."

If it exists, print a summary in this format:

---

## Bespoke Budget

| # | What | Rationale | Lines | Vetoed? |
|---|------|-----------|-------|---------|
| (rows from file) |

**Total spent: +N lines**

### Close calls
List any rows where Vetoed? is `ponytail`, one per line:
- `#N — <what>`: ponytail flagged this. Still in? Consider `/ponytail-review`.

If no close calls: "No close calls. Ponytail would probably let this through."

---

After the summary, offer: "Want a full ponytail review of these decisions?
Run `/ponytail-review`."
