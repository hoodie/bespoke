---
name: bespoke-help
description: |
  Quick-reference card for all bespoke modes, skills, and commands. One-shot display, not a persistent mode. Trigger: /bespoke-help, "bespoke help", "what bespoke commands", "how do I use bespoke".
disable-model-invocation: false
---

# Bespoke Help

One-shot reference card. Do not change mode or persist anything.

## Levels

| Level | Trigger | Behaviour |
|-------|---------|-----------|
| **lite** | `/bespoke lite` | Idiomatic code, flag one type upgrade in one line. |
| **full** | `/bespoke` | Type-driven. Every choice annotated. Default. |
| **ultra** | `/bespoke ultra` | Typestate extremist. Pushes back on misuse-prone designs. |

Level persists until changed or session end. Deactivate: "stop bespoke" / `/bespoke off`.

## Skills

| Skill | Trigger | What it does |
|-------|---------|--------------|
| **bespoke** | `/bespoke` | Artisan typesmith mode. |
| **bespoke-review** | `/bespoke-review` | Type safety review: one finding per line. |
| **bespoke-budget** | `/bespoke-budget` | Complexity ledger: what bespoke spent, close calls. |
| **bespoke-help** | `/bespoke-help` | This card. |

## The [bespoke] annotation

`[bespoke: newtype UserId/ProductId prevents ID confusion, +8 lines]`

Every non-trivial type decision is flagged so you can push back.

## The cut-off rule

Encode compile-time invariants. Stop before encoding runtime state.
- Worth it: distinct IDs, validated input, non-empty collections.
- Not worth it: active/inactive user, connected/disconnected socket.

## Ponytail pairing

Ponytail is the PR gatekeeper. Bespoke consults them before presenting output
and logs every spend to `bespoke-budget.md`. `/ponytail` + `/bespoke` is the
recommended pairing.
