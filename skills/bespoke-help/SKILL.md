---
name: bespoke-help
description: |
  Quick-reference card for all bespoke modes, skills, and commands. One-shot display, not a persistent mode. Trigger: /bespoke-help, "bespoke help", "what bespoke commands", "how do I use bespoke".
disable-model-invocation: false
---

# Bespoke Help

One-shot reference card. Do not change mode or persist anything.

## Levels

| Level     | Trigger          | Behaviour                                                 |
| --------- | ---------------- | --------------------------------------------------------- |
| **lite**  | `/bespoke lite`  | Idiomatic code, flag one type upgrade in one line.        |
| **full**  | `/bespoke`       | Type-driven. Every decision announced. Default.           |
| **ultra** | `/bespoke ultra` | Typestate extremist. Pushes back on misuse-prone designs. |

Level persists until changed or session
end. Deactivate: "stop bespoke" / `/bespoke off`.

## Skills

| Skill              | Trigger           | What it does                                      |
| ------------------ | ----------------- | ------------------------------------------------- |
| **bespoke**        | `/bespoke`        | Artisan typesmith mode.                           |
| **bespoke-review** | `/bespoke-review` | Type safety review: one finding per line.         |
| **bespoke-bdr**    | `/bespoke-bdr`    | Show the Bespoke Decision Record for this branch. |
| **bespoke-help**   | `/bespoke-help`   | This card.                                        |

## Decisions

Every non-trivial type decision is announced in the chat response, never written into source code:

`[bespoke: newtype UserId/ProductId prevents ID confusion, +8 lines]`

Each decision is also logged to `bespoke-decisions.md` (the BDR) at the project root.
The BDR is a PR artifact. Delete it on merge.

## The cut-off rule

Encode compile-time invariants. Stop before encoding runtime state.

- Worth it: distinct IDs, validated input, non-empty collections.
- Not worth it: active/inactive user, connected/disconnected socket.

## Ponytail pairing

The BDR is the handshake. Bespoke logs every decision with cost and rationale;
ponytail's instructions respond to those naturally if both are in context.
At 10 BDR entries, bespoke warns you and spawns a background ponytail review.

`/ponytail` + `/bespoke` is the recommended pairing.
