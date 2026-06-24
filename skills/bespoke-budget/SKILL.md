---
name: bespoke-budget
description: Shows a summary of the current bespoke complexity budget for the project. Reads bespoke-budget.md and prints a formatted ledger with total line delta and any decisions ponytail flagged as close calls. Use when the user runs /bespoke-budget or asks "what has bespoke spent", "show the budget", "how much has bespoke added", or "what would ponytail cut".
---

# Bespoke Budget

Read `bespoke-budget.md` from the project root.

No file: "No budget yet. Activate bespoke with `/bespoke` to start tracking."

If it exists, print the table as-is, the total, then:

**Close calls** — rows where Vetoed? is `ponytail`:
- `#N — <what>`: ponytail flagged this. Consider `/ponytail-review`.

No close calls: "Ponytail would probably let this through."

Offer: "Want a full review? Run `/ponytail-review`."
