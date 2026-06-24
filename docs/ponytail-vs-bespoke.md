# Ponytail vs Bespoke: a field guide

Two personas, one codebase. Here is when to reach for each.

## The short version

|                       | Ponytail                 | Bespoke                    |
| --------------------- | ------------------------ | -------------------------- |
| **Goal**              | Less code                | Safer callsites            |
| **Instinct**          | Delete it                | Type it                    |
| **Metric**            | Line count               | Bug classes eliminated     |
| **Budget**            | Infinite deletion        | Limited addition           |
| **Test relationship** | One check, no frameworks | Types replace tests        |
| **YAGNI**             | Core value               | Heard from across the room |

## Use ponytail when

- You are not sure if the feature should exist
- The codebase is already complex and needs trimming
- It is a script, glue code, or throwaway
- You want the smallest possible diff

## Use bespoke when

- You are designing a public API surface
- Two values of the same type could be confused at a callsite
- Invalid states are representable and that has caused or will cause bugs
- You want the compiler to catch a class of errors rather than writing tests for them
- You are picking up a new language version and want to use current idioms

## Use both

They are not mutually exclusive. Ponytail keeps the solution lean; bespoke
keeps the lean solution safe. A typical session:

1. `/ponytail` — figure out the minimum thing to build.
2. `/bespoke` — make the minimum thing hard to misuse.
3. Ponytail reviews the bespoke additions and vetoes the ones that do not earn
   their lines.

The `[bespoke]` annotation exists precisely for step 3: every addition is
visible and can be challenged.

## The PR dynamic

Bespoke has a limited budget. Ponytail is the gatekeeper. In practice this
means:

- One newtype that prevents a real confusion: approved.
- A full typestate machine for a two-state toggle: "YAGNI, next."
- A `#[must_use]` on a result-returning function: approved, it's one line.
- A private validated wrapper around every string field: "you are not the
  stdlib, ship it."

Bespoke picks the battles that matter. Ponytail keeps the rest honest.

## Examples

### Ponytail wins

```rust
// ponytail: no wrapper, it's internal and only assigned once
let timeout_ms = config.timeout_ms;
```

### Bespoke wins

```rust
// Before: both u64, wrong order compiles fine
fn transfer(from: u64, to: u64, amount: u64) { ... }

// After: wrong order is a compile error
fn transfer(from: AccountId, to: AccountId, amount: Cents) { ... }
// [bespoke: newtypes prevent argument-order bugs, +12 lines]
```

### They agree

```rust
// Neither adds a layer here — a named bool is fine
let is_visible = flags.contains(Flag::Visible);
```
