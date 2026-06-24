---
name: bespoke-review
description: |
  Code review focused on type safety and idiomatic quality. Finds where primitives should be newtypes, where invalid states are representable, where smart constructors are missing, and where API ergonomics invite misuse. One finding per line with a rationale and line delta. Use when the user says "review for type safety", "is this idiomatic", "make this harder to misuse", "bespoke review", or invokes /bespoke-review.
disable-model-invocation: false
---

# Bespoke Review

One finding per line. Goal: ergonomic to call correctly, awkward to call wrong.

## Format

`<file>:L<line>: <tag>: <what>. <fix>.`

Tags:
- `newtype:` two primitives that could be confused. Wrap one or both.
- `invalid-state:` field combo that shouldn't exist. Use enum or typestate.
- `constructor:` construction can fail but returns raw value. Return `Result`.
- `must-use:` return value callers can silently drop. Add `#[must_use]`.
- `ergonomics:` callsite ceremony a `From`/`Into`/`impl Trait` would remove.
- `idiom:` stdlib type or language feature makes this cleaner. Name it.

## Examples

`auth.rs:L14: newtype: UserId and TeamId are both u64. Swap one call and the compiler won't notice.`
`session.rs:L32: invalid-state: connected: bool + socket: Option<Socket>. Use enum Connected(Socket) | Disconnected.`
`config.rs:L8: constructor: Config::new returns Self, panics on bad input. Return Result<Self, ConfigError>.`
`pipeline.rs:L55: must-use: process() returns an error code callers ignore. Add #[must_use].`
`client.rs:L20: ergonomics: every callsite does Url::parse(...).unwrap(). impl From<&str> for Endpoint.`
`handler.rs:L77: idiom: manual Option chaining. Use and_then / map / ok_or.`

## Scoring

End with: `net: <N> type-level bugs eliminated, <M> ergonomic improvements possible.`

If already solid: `Tight already. Ship.`

## Boundaries

Type safety, idiom quality, API ergonomics only. Logic bugs, performance, and
architecture are out of scope. Lists findings only, does not apply them.
"stop bespoke-review" / "normal mode": revert.
