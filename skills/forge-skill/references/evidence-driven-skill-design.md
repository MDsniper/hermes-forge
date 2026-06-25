# Evidence-Driven Skill Design -- The Full Spec

The five laws, measured not vibes. Each has eval evidence behind it.

## The Evidence

One controlled eval, 22 runs, deterministic scoring. A draft salted with 22 known violations + 5 voice traps:

| Configuration | Violations Fixed | Voice Preserved | Pass Rate |
|---|---|---|---|
| Full 575-line skill stack | 20-21/22 | 5/5 | **0%** (banned chars survived) |
| 50-line gotcha distillation | 21/22 | 5/5 | 33% |
| No skill ("make it sound human") | 10-11/22 | 4/5 | 0% |
| **Gotcha SKILL.md + script gate** | 21-22/22 | 5/5 | **92%** (12/13) |

Four facts to internalize:
- The calibrated content WAS load-bearing (no-skill scored half). This is NOT "delete your skills."
- 525 of 575 lines bought zero accuracy. Reference files "felt" essential and measured useless.
- "Zero tolerance" in a prompt is not zero. 8/9 runs violated it.
- Original benchmark (WorkOS): a 10,000-line docs-generated skill scored 77% on tasks the bare model did at 97%.

---

## Law 1 -- Guide, Don't Prescribe

The model already knows how to write, code, and reason. A skill's job is to supply what the model CANNOT know: your landmines, calibrations from real failures, conventions, taste.

**What earns a line:**
- Gotchas born from real failures, with origin noted (date + what happened + who caught it)
- Carve-outs and keep-rules (what looks like a violation but is wanted)
- Frameworks with named parts
- Real examples, verbatim
- Conventions that are arbitrary but must be consistent

**What does NOT earn a line:**
- Anything the base model already does well
- Comprehensive catalogs "for completeness"
- Restatements of another skill's rules (Law 2)
- A rule stated three escalating ways. Once, with the why.

**The test:** "Would the model get this wrong WITHOUT the line?" If you don't know -- that's Law 4.

---

## Law 2 -- One Home Per Rule

Audited example: a 1,383-line workflow was 25% SPINE / 33% DUPLICATE / 37% STEP-DETAIL / 5% STALE. One inlined prompt coached banned behavior months after the rules were deleted from the canonical skill.

**The four content classes:**

| Class | Definition | Treatment |
|---|---|---|
| **SPINE** | Step order, gates, delegation calls, paths | Stays inline |
| **DUPLICATE** | Restates another skill's rule | Replace with named pointer |
| **STEP-DETAIL** | Needed only during one step | Move to reference file |
| **STALE** | Contradicts newer calibration | Fix immediately -- live bug |

**Exceptions that MUST stay inline:**
- Sub-agent prompt templates (they can't follow pointers they never receive)
- Acceptance criteria at gates
- Worked examples (Law 5)

---

## Law 3 -- Enforce, Don't Instruct

Split every rule into two piles:

**Mechanical rules** (detectable by regex/script): banned phrases, forbidden characters, required format, length bounds, required sections. These go in a **gate script**, not (only) in prose.

**Judgment rules** (need reading comprehension): tone, structure, over-correction risk. These stay as gotchas with origin + carve-out.

**The gate script spec:**
- Takes the output file path
- Prints line-numbered violations with rule name + snippet
- Ends with `VERDICT: CLEAN` or `VERDICT: N VIOLATION(S)`
- The exit checklist REQUIRES the clean verdict pasted as evidence
- "Trust replaced with evidence" -- don't accept "I ran the check," accept the check's output

**The principle:** make doing the work easier than lying about it.

---

## Law 4 -- Measure, Don't Assume

You cannot know whether a skill helps without running it. "Feels better" sample-of-one is how dead weight accumulates.

**The minimal eval harness:**

1. **Salted fixture** -- realistic input seeded with N known violations (REMOVE seeds) + M traps to preserve (KEEP traps)
2. **Deterministic scorer** -- one regex per seed/trap. No LLM judge for anything regex can decide.
3. **Variants** -- A: current skill. B: proposed change. C: no skill (the control).
4. **Runs** -- 3 per variant for direction; 10+ to claim a pass rate.
5. **PASS criterion + bar** -- e.g. >=86% seeds fixed AND all traps kept AND 0 mechanical violations. Bar: >=85%.
6. **Regression rule** -- the harness outlives the experiment. Re-run on every future edit.

**When a full harness is overkill:** still do variant C once. If the bare model matches the skill, the skill is decoration.

---

## Law 5 -- Real Examples Beat Rule-Prose

- **Calibration loads:** name 1-2 REAL gold-standard artifacts and say "match THIS."
- **Verbatim samples in sub-agent briefs:** paste actual paragraphs -- file pointers don't survive a fork.
- **Worked examples are exempt from dedup** (Law 2): a before/after pair teaches what three paragraphs can't.
- Examples age better than rules: a rule fights the next calibration; an example gets replaced.

---

## The Authoring Checklist

Run on every new or rebuilt skill:

- [ ] Every rule answers "would the model get this wrong without it?"
- [ ] Gotchas carry origin (date + what happened); carve-outs included
- [ ] No rule restated from another skill -- pointers by name
- [ ] Mechanical rules in a gate script with `VERDICT:` line
- [ ] STOP gates at irreversible hand-offs
- [ ] 1-2 named real examples loaded for calibration
- [ ] Eval fixture + scorer exists (or at minimum no-skill control run once)
- [ ] References demoted to on-request unless measured to earn default loading

---

**Cross-references:** mechanism selection -> `references/mechanism-selection.md` · skill anatomy -> SKILL.md
