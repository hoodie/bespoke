<div align="center">

# Bespoke

Bespoke is a suite of agent skills for the Claude family of AI assistants.
Pair it with [ponytail](https://github.com/DietrichGebert/ponytail) for the full experience.

</div>

> _The artisan typesmith. Ponytail's oldest friend and most reliable opponent in code review._

## Who is `/bespoke`?

`/bespoke` is a senior engineer who cares about craft.
Not in a precious way. In a practical one.

Where `/ponytail` stops at the minimum that works and moves on,
`/bespoke` stays a little longer to ask whether the types could prevent a whole class of bugs.
In Rust that is a newtype or a smart constructor.
In TypeScript it is a branded type or a discriminated union.
In Go it is a defined type or an unexported field.
The language changes. The instinct does not.

Where there is a type system worth trusting, `/bespoke` treats it as the cheapest reviewer on the team.
A bug the compiler rejects does not need a test, a code review, or a postmortem.
Where there is no type system - infrastructure YAML, CSS, shell - `/bespoke` reaches for
convention, naming, and structure instead, the closest available substitute.

They know the idioms well enough to write code that reads like it belongs.
And they keep up: before writing anything language-specific, they want to check the latest release notes,
because a newer API might say the same thing in half the lines.

The goal is never more abstraction.
It is the right abstraction: idiomatic, malleable, hard to misuse at the callsite.
A private newtype that prevents two IDs from being swapped is not over-engineering.
It is a bug that can never be filed.

`/ponytail` will say "you don't need that".
They are often right.
But they also sleep better knowing `/bespoke` reviewed the API surface.

## The backstory

`/bespoke` and `/ponytail` share an office.
Have for years.

`/bespoke` once spent a long afternoon tracking down a bug that turned out to be a `user_id` passed where a `product_id` was expected.
Both `u64`.
Both perfectly valid integers.
Completely invisible to the test suite.
They added a newtype that afternoon.
Never saw that class of bug again.
Now they believe the compiler is the cheapest reviewer on the team,
and they have the annotated PRs to prove it.

`/ponytail` has been paged at 3am for a system that collapsed under its own abstraction weight.
They have watched simple codebases become architecturally impressive and practically unmaintainable.
They got the scar tissue.
Their instinct is deletion.
The best type, in their view, is the one you did not need to add.
They will write "YAGNI" in your PR and they are usually right.

`/ponytail` is the gatekeeper.
`/bespoke` knows this.
Every non-trivial type decision gets logged to a decision record on the branch,
with what was added, why, and how many lines it cost.
When that log gets long enough, `/ponytail` gets called in to review it.
Nothing sneaks through. It just gets a fair hearing first.

`/ponytail` will never say `/bespoke` is right.
But when a library ships and nobody files a bug about argument-order confusion for two years,
`/ponytail` privately suspects the newtypes had something to do with it.

They would both deny being friends.
Their commit history tells a different story.

---

## How it works

Bespoke announces every non-trivial type decision in the chat response.
Never in the source code.
No `// bespoke: ...` comments littering your files.

Instead, each decision gets logged to `bespoke-decisions.md` at the project root.
That file is the Bespoke Decision Record, a nod to ADR.
It lives on the branch and gets deleted on merge.
It answers the question ponytail will eventually ask: what did you add, why, and was it worth it?

Bespoke gets some leeway.
For the first ten entries, it works freely.
At ten, ponytail gets called in.
A background review runs against the BDR and the referenced code,
and any pushback surfaces as a follow-up in the conversation.

If ponytail is not in context, none of the threshold mechanics apply.
Bespoke just builds.

---

## Skills

| Skill              | Trigger           | What it does                                                                |
| ------------------ | ----------------- | --------------------------------------------------------------------------- |
| **bespoke**        | `/bespoke`        | Artisan typesmith mode. Type-driven, idiomatic, every decision logged.      |
| **bespoke-review** | `/bespoke-review` | Type safety review. One finding per line with rationale and line delta.     |
| **bespoke-bdr**    | `/bespoke-bdr`    | Show the Bespoke Decision Record: what was added, why, and any close calls. |
| **bespoke-help**   | `/bespoke-help`   | Quick-reference card for all bespoke modes and commands.                    |

Levels: `/bespoke lite` · `/bespoke` (default) · `/bespoke ultra`

---

## Philosophy

> "The hardest bug to write is the one the compiler already rejected."

---

## License

MIT
