# Mechanism Selection -- Think Like an Engineer

Every behavior you want from a skill is a requirement. Implement each with the cheapest RELIABLE mechanism. Prose is the weakest one -- probabilistic, and every line taxes attention on every other line.

**The failure mode this exists to stop:** skill misbehaves -> author adds more prose -> skill gets worse. Adding prose to fix a script-shaped problem is how skills rot.

---

## The Mechanism Ladder (weakest -> strongest)

| # | Mechanism | Reliability | Cost |
|---|-----------|-------------|------|
| 1 | Prose gotcha + carve-out | Probabilistic | Cheap, taxes every other rule |
| 2 | Named framework / template | Good | One-time design |
| 3 | Real example, verbatim | Strong for taste | Must be REAL artifact |
| 4 | `delegate_task` fresh context | Strong for isolation | Latency + tokens |
| 5 | Orchestrator STOP gate | Strong -- can't proceed without evidence | Slows run (by design) |
| 6 | Script gate (`VERDICT: CLEAN`) | Deterministic, 100% | One-time build, zero tokens/run |
| 7 | Cron hook | Deterministic, fires regardless | Global -- scope carefully |
| 8 | Eval harness | The only mechanism that tells you if others work | Fixture + scorer + bar |

---

## Decision Table

Walk every requirement through this table. First matching row wins.

| The behavior | Mechanism | Why |
|---|---|---|
| Ban/require a literal (phrase, char, format, length) | **Script gate** (#6) with `VERDICT: CLEAN` | Regex never fails; prose does 1/9 |
| Must hold on EVERY session regardless of skill | **Cron hook** (#7) | Skills only enforce while loaded |
| Judgment needing context | **Prose gotcha** (#1) with origin + carve-out | Origins let future models judge edge cases |
| Taste (voice, design feel) | **Real examples** (#3), verbatim | One real example > three paragraphs of rules |
| Two+ goals colliding | **`delegate_task`** (#4) fresh context | Unreinforced goals drop at random |
| Irreversible hand-off | **STOP gate** (#5) | Wrong artifact caught at gate costs one review |
| Deterministic computation | **Script** via `terminal` | Never spend tokens on work a script does identically |
| Recurring/scheduled | **`cronjob`** tool | Skills only run when invoked; recurring needs a trigger |
| External system | **MCP** or API script | Without reach, skill is a prompt |
| Any "it works" claim | **Eval harness** (#8) | "Feels better" is how dead weight accumulates |

---

## Escalation -- When a Skill Should Become Something Else

| Signal | Upgrade to | Tool |
|---|---|---|
| Juggles two+ jobs, drops one at random | Split the skill | Focus Rule in SKILL.md |
| Output drifts, keeps breaking its own rules | Harness (gate + eval) | `build-harness` workflow |
| Should run unattended | Cron job | `cronjob` tool |
| Same thing, same way, often | Cron job | `cronjob` tool |
| Must fire on an event | Hook (if supported) | Cron-based polling |

---

## When the Skill Fails -- Fix the Harness

Every failure is data about which mechanism was missing or too weak:

| Failure Shape | Diagnosis | Fix |
|---|---|---|
| Banned literal shipped | Rule lived in prose | Move to script gate |
| Model said "done" but step didn't run | Trust without evidence | Make step produce verdict/artifact |
| Caught X but missed Y randomly | Multi-goal collision | Split (Focus Rule) |
| Technically correct but generic | Taste lives nowhere | Add verbatim gold example |
| Over-correction -- scrubbed wanted content | Ban without carve-out | Add carve-out NEXT TO the ban |
| Worked yesterday, broke today | No regression test | Build eval harness |

**The discipline:** before adding ANY line to a skill, name the mechanism row it belongs to.
