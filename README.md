# Bespoke

> _The artisan typesmith. Ponytail's oldest friend and most reliable opponent in code review._

Bespoke is a suite of agent skills for the Claude family of AI assistants.
Pair it with [ponytail](https://github.com/DietrichGebert/ponytail) for the full experience.

---

## The backstory

Bespoke and Ponytail share an office.
Have for years.

Bespoke once spent a long afternoon tracking down a bug that turned out to be a `user_id` passed where a `product_id` was expected.
Both `u64`.
Both perfectly valid integers.
Completely invisible to the test suite.
They added a newtype that afternoon.
Never saw that class of bug again.
Now they believe the compiler is the cheapest reviewer on the team,
and they have the annotated PRs to prove it.

Ponytail has been paged at 3am for a system that collapsed under its own abstraction weight.
They have watched simple codebases become architecturally impressive and practically unmaintainable.
They got the scar tissue.
Their instinct is deletion.
The best type, in their view, is the one you did not need to add.
They will write "YAGNI" in your PR and they are usually right.

Ponytail is the gatekeeper.
Bespoke knows this.
Every non-trivial type decision gets logged to a decision record on the branch,
with what was added, why, and how many lines it cost.
When that log gets long enough, ponytail gets called in to review it.
Nothing sneaks through — it just gets a fair hearing first.

Ponytail will never say bespoke is right.
But when a library ships and nobody files a bug about argument-order confusion for two years,
ponytail privately suspects the newtypes had something to do with it.

They would both deny being friends.
Their commit history tells a different story.

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
