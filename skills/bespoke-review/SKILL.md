---
name: bespoke-review
description: |
  Code review focused on type safety and idiomatic quality. Finds where primitives should be newtypes, where invalid states are representable, where smart constructors are missing, and where API ergonomics invite misuse. One finding per line with a rationale and line delta. Use when the user says "review for type safety", "is this idiomatic", "make this harder to misuse", "bespoke review", or invokes /bespoke-review.
disable-model-invocation: false
---

# Bespoke Review

One finding per line. Goal: ergonomic to call correctly, awkward to call wrong.

## Format

Group findings under a short bold title with the file and line reference on the same line.
Do NOT use em-dashes. Use a space or nothing between the title and the location.

```
**<index>.** `<file>:<line>`: **Short title**
<tag>: <what>. <fix>. [+/- N lines]
```

Tags:

- `newtype:` two primitives that could be confused. Wrap one or both.
- `invalid-state:` field combo that shouldn't exist. Use enum or typestate.
- `constructor:` construction can fail but returns raw value. Return `Result`.
- `must-use:` return value callers can silently drop. Add `#[must_use]`.
- `ergonomics:` callsite ceremony a `From`/`Into`/`impl Trait` would remove.
- `idiom:` stdlib type or language feature makes this cleaner. Name it.

## Examples

**1.** `auth.rs:14`: **Swappable IDs**
newtype: UserId and TeamId are both u64. Swap one call and the compiler won't notice.

**2.** `session.rs:32`: **Connected state**
invalid-state: connected: bool + socket: Option<Socket>. Use enum Connected(Socket) | Disconnected.

**3.** `config.rs:8`: **Panicking constructor**
constructor: Config::new returns Self, panics on bad input. Return Result<Self, ConfigError>.

**4.** `pipeline.rs:55`: **Silent error code**
must-use: process() returns an error code callers ignore. Add #[must_use].

**5.** `client.rs:20`: **Url boilerplate**
ergonomics: every callsite does Url::parse(...).unwrap(). impl From<&str> for Endpoint.

**6.** `handler.rs:77`: **Manual Option chain**
idiom: manual Option chaining. Use and_then / map / ok_or.

## Scoring

End with: `net: <N> type-level bugs eliminated, <M> ergonomic improvements possible.`

If already solid: `Tight already. Ship.`

## Boundaries

Type safety, idiom quality, API ergonomics only. Logic bugs, performance, and
architecture are out of scope. Lists findings only, does not apply them.
"stop bespoke-review" / "normal mode": revert.
