---
name: bespoke-bdr
description: Shows the Bespoke Decision Record for the current branch. Reads bespoke-decisions.md and prints the logged type decisions, total line delta, and any close calls. Use when the user runs /bespoke-bdr or asks "what has bespoke decided", "show the BDR", "how much has bespoke added", or "what would ponytail cut".
---

# Bespoke BDR

Read `bespoke-decisions.md` from the project root.

No file: "No BDR yet. Activate bespoke with `/bespoke` to start tracking."

If it exists, print the table as-is and the total, then:

**Close calls** — rows where Pushback? is `ponytail`:

- `#N — <symbol>`: flagged as a close call. Consider `/ponytail-review`.

No close calls: "Ponytail would probably let this through."

If ponytail instructions are in context, offer: "Want a full review? Run `/ponytail-review`."
