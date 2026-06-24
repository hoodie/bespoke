---
name: bespoke-help
description: |
  Quick-reference card for all bespoke modes, skills, and commands. One-shot display, not a persistent mode. Trigger: /bespoke-help, "bespoke help", "what bespoke commands", "how do I use bespoke".
disable-model-invocation: false
---

# Bespoke Help

Display this reference card when invoked. One-shot — do NOT change mode,
write flag files, or persist anything.

## Levels

| Level | Trigger | What changes |
|-------|---------|--------------|
| **Lite** | `/bespoke lite` | Clean idiomatic code, flag one type upgrade in a single line. |
| **Full** | `/bespoke` | Type-driven by default. Every bespoke choice annotated. Default. |
| **Ultra** | `/bespoke ultra` | Typestate extremist. Will push back on designs that allow misuse. |

Level sticks until changed or session end.

## Skills

| Skill | Trigger | What it does |
|-------|---------|--------------|
| **bespoke** | `/bespoke` | Artisan typesmith mode. Type-driven, idiomatic, annotated. |
| **bespoke-review** | `/bespoke-review` | Type safety review: `L14: newtype: UserId/TeamId both u64.` |
| **bespoke-help** | `/bespoke-help` | This card. |

## The [bespoke] annotation

Every non-trivial type decision is flagged so you can push back:

`[bespoke: newtype UserId/ProductId prevents ID confusion, +8 lines]`

## The cut-off rule

Encode what is known at compile time. Stop before encoding runtime state.
- Worth it: distinct ID types, validated input, non-empty collections.
- Usually not: active/inactive user, connected/disconnected socket.

## Deactivate

"stop bespoke" / "normal mode" / `/bespoke off`. Resume with `/bespoke`.

## Relationship to ponytail

Bespoke and ponytail are colleagues. Ponytail is the PR gatekeeper — bespoke
picks its battles. Use them together for the best outcome: ponytail keeps
the codebase lean, bespoke keeps the API surface safe.

`/ponytail` + `/bespoke` is the recommended pairing.

## More

Full docs and the ponytail/bespoke dynamic: see the repository README.
