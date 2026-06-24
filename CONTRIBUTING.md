# Contributing

Thanks for wanting to improve bespoke.

## What belongs here

A good contribution to bespoke does one of these things:

- Sharpens the type-driven ladder (a rung that is ambiguous, missing, or wrong)
- Improves the cut-off rule with a concrete counter-example from the field
- Adds a well-motivated intensity level behaviour
- Fixes a case where bespoke was too aggressive or not aggressive enough
- Improves the bespoke-review tag set with a tag that recurs in practice

A good contribution does NOT:

- Add scope creep (architecture, performance, logic review — those are different tools)
- Make bespoke and ponytail redundant with each other
- Remove the annotation requirement (bespoke is never silent about its choices)

## How to contribute

1. Open an issue first for anything non-trivial. Describe the real-world case
   that motivated it.
2. Fork, edit the relevant `skills/<name>/SKILL.md`, open a PR.
3. Include a before/after example in the PR description showing the old and new
   agent behaviour.

## Skill file rules

- The `name` field in frontmatter must match the directory name exactly.
- The `description` field is what the agent reads to decide whether to load the
  skill — keep it specific and trigger-rich.
- Do not add prose that merely restates the code. Instructions should say what
  to do, not explain why it is obvious.

## Testing a skill locally

```sh
cp -r skills/bespoke ~/.agents/skills/bespoke
```

Start a new Zed conversation and trigger the skill. Iterate. When happy, copy
back and open a PR.
