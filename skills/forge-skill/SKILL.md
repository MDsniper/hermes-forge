---
name: forge-skill
description: "Create, validate, test, upgrade, and improve Hermes skills -- and chain them into Skill Systems. Use when someone says 'create a skill', 'build a skill for X', 'add a skill', 'turn this into a skill', 'build a skill system', 'build an AI employee', 'automate this whole operation', 'validate skill', 'test skill', 'improve this skill', 'update skill X', 'upgrade my skills', 'audit my skill library', or ANY time they want to change an existing skill or extend Hermes capabilities. ALWAYS load this skill before editing any ~/.hermes/skills/** file -- a direct hand-edit skips the evidence-driven discipline this skill enforces."
---

# Forge Skill -- Author, Chain, and Improve

## Workflow Routing

### Create a new skill -> `workflows/create-skill.md`
**When:** "create a skill for X", "build a skill that does Y", "add a skill". For ONE job.
**Output:** New skill directory with SKILL.md via `skill_manage(action=create)`.

### Build a Skill System -> `workflows/build-skill-system.md`
**When:** "build a skill system", "automate this whole operation", "turn this process into a system". For SEVERAL jobs wired in sequence.
**Output:** Chain of step-skills + orchestrator.

### Validate an existing skill -> `workflows/validate-skill.md`
**When:** "validate skill", "check compliance", "is this skill structured right?"
**Output:** Scored report with remediation steps.

### Harden a skill -> `workflows/build-harness.md`
**When:** "make this production-grade", "add a harness", "the skill keeps ignoring its own rule"
**Output:** Gate scripts + reviewer pattern + eval harness.

### Test a skill -> `workflows/test-skill.md`
**When:** "test skill", "eval skill", "is this skill actually good?"
**Output:** Graded eval report with pass/fail against salted fixtures.

### Upgrade and restructure -> `workflows/upgrade-skill.md`
**When:** "upgrade my skills", "fix my routing", "restructure this", "my skills are a mess"
**Output:** Restructured skill with cleaner routing, extracted references, no dead weight.

### Update an existing skill -- Evidence-Driven Discipline
**When:** "update skill X", "add this to the skill", "improve this skill", "the skill should also..."

> **ALWAYS ENTER HERE FIRST when changing ANY existing skill. Never hand-edit a SKILL.md directly.**

**The discipline:**
1. **Origin** -- Note date + what happened + who caught it, next to the rule.
2. **Carve-out** -- Name the case where the rule must NOT apply.
3. **Mechanical or judgment?** -- Literal patterns go in a gate script, not prose.
4. **One home** -- If the rule belongs in another skill, point to it by name.
5. **Measure or mark unmeasured** -- Significant change? Note it's unmeasured or run a test.
6. **Surgical apply** -- Use `skill_manage(action=patch)` with old_string/new_string.

---

## Related Skills (when to delegate)

| User says | Delegate to | Why |
|-----------|-------------|-----|
| "Fix this skill that went wrong" | `retrospective` | Surgical patch based on observed friction |
| "Map my business" | `business-xray` | Business process visualization |
| "What should I build next" | `roadmap` | Triage and direction |
| "Set me up" / "first time" | `onboard` | Workspace scaffolding |

---

## When to Activate

**Activate when:**
- Any phrase in the Workflow Routing table
- User wants to extend Hermes capabilities with a new skill
- User wants to clean up, upgrade, or chain an existing skill library

**ALWAYS activate (never hand-edit instead):**
- ANY request to change an existing skill. Enter via "Update an existing skill" above.

**Do NOT activate when:**
- User wants to fix a skill that misfired -> `retrospective`
- User already has a finished draft and just wants to save it -> use `skill_manage(action=create)` directly

---

## Evidence-Driven Skill Design (the five laws)

**Read `references/evidence-driven-skill-design.md` before authoring any skill.** The one-screen version:

1. **Guide, don't prescribe.** Ship gotchas and frameworks, not comprehensive docs. Measured: a 50-line gotcha distillation matched a 575-line skill stack at 30% fewer tokens.
2. **One home per rule.** Workflows are SPINE; rules live in their canonical skill. Inlined copies rot.
3. **Enforce, don't instruct.** Mechanical rules go in a gate script printing `VERDICT: CLEAN`. Measured: 8/9 model runs violated a prose "zero tolerance" rule; script catches 100%.
4. **Measure, don't assume.** Salted fixture -> deterministic scorer -> no-skill control -> pass bar (>=85%).
5. **Real examples beat rule-prose.** Name 1-2 gold-standard artifacts. Verbatim samples in briefs.

### The Mechanism Pass

Every behavior is a requirement. Assign each a mechanism before writing it.

| The behavior | The mechanism |
|---|---|
| Ban/require a literal (phrase, character, format) | Gate script with `VERDICT: CLEAN` |
| Must hold on EVERY session | Hermes cron hook |
| Judgment call needing context | Prose gotcha + origin + carve-out |
| Taste (voice, design feel) | Real examples, verbatim |
| Two+ goals colliding | `delegate_task` with fresh context |
| Irreversible hand-off | Orchestrator STOP gate |
| Deterministic computation | Script the skill runs via `terminal` |
| Recurring/scheduled | `cronjob` tool |
| External system | MCP server or API script |
| Any "it works" claim | Eval harness + pass bar |

Full decision table: `read references/mechanism-selection.md`

---

## Architecture Decision Tree

**Should it be a standalone skill or a workflow nested inside an existing skill?**

| Criterion | Standalone | Nested Workflow |
|-----------|------------|-----------------|
| Reusable across parents? | Yes | No (one parent) |
| User invokes by name? | Yes | No |
| Universal vs specific? | Universal | Content-type specific |
| Needs fresh context? | Often yes (use `delegate_task`) | Usually no |
| Parent works without it? | Yes | No |

**When signals are mixed -- default to standalone.**

---

## Skill Anatomy

```
skill-name/
  SKILL.md          (required -- router + core instructions, <500 lines ideal)
  workflows/        (optional -- separate files for each distinct flow)
  references/       (optional -- docs loaded on demand)
  scripts/          (optional -- executable code)
  assets/           (optional -- templates, examples)
```

**Progressive disclosure:**
1. **Metadata** (YAML name + description) -- always in context, ~100 words
2. **SKILL.md body** -- loaded when skill triggers, ideally <500 lines
3. **Bundled resources** -- loaded on demand via `read_file` or `skill_view`

---

## Writing Patterns for SKILL.md

**Prefer imperative voice.** "Create the directory" -- not "You should create the directory."

**Explain WHY.** When you tell a future agent why a rule exists, it can judge edge cases.

**ALWAYS/NEVER in all caps is a yellow flag.** Reframe with reasoning.

**Show examples, not abstractions.**
Bad: "Choose an appropriate naming convention."
Good: "Use kebab-case. `write-hook` not `writeHook`."

---

## Descriptions -- Make Them Pushy

Hermes tends to undertrigger skills. Descriptions should be specific AND assertive.

Include:
- **What the skill does** (one clean sentence)
- **5-10 trigger phrases** in a "USE WHEN" clause
- **Exclusions** -- "Do NOT use when..." pointing to the right sibling

---

## Cross-Skill Routing

### Pattern 1: "Delegate to X"
```markdown
### Step 3: Voice Cleanup
Delegate to `writing-humanize` skill for voice cleanup.
Use `delegate_task` so it gets a fresh context.
```

### Pattern 2: Defensive Routing
```markdown
**Do NOT activate when:**
- User wants X -> route to `other-skill`
```

### Pattern 3: The Orchestrator
Some skills coordinate others. They detect intent, route, delegate, compose.

### Anti-pattern: reaching into another skill's internals
Skills are black boxes. If you need functionality, delegate -- don't inline.

---

## Pipeline Pattern (chained subagents)

Use `delegate_task` for composition. Each layer gets fresh context:

```
write (orchestrator)
  -> routes by content type
  -> delegates to writing-logic   [delegate_task] -- argument structure
  -> delegates to write-hook      [delegate_task] -- opening
  -> delegates to writing-humanize [delegate_task] -- voice cleanup
  -> delegates to writing-format  [delegate_task] -- formatting
```

Each layer can be improved independently.

---

## Graduating to Cron

When a skill is proven and runs repeatedly, automate it:

```
# Schedule a skill to run on a cadence
cronjob(action=create, schedule="0 9 * * *", prompt="Run the daily standup skill...", deliver="telegram")
```

Gate on: satisfied + tested + runs reliably. Don't schedule unproven skills.

---

## Reference Pointers

Load these when the context calls for them:

- `references/evidence-driven-skill-design.md` -- **Load BEFORE authoring or rebuilding any skill.**
- `references/mechanism-selection.md` -- **Load when adding a rule to any skill.**
- `templates/simple-skill-template.md` -- For 1-3 workflow skills
- `templates/complex-skill-template.md` -- For multi-workflow skills
- `templates/orchestrator-skill-template.md` -- For skills that coordinate others
- `templates/cron-skill-template.md` -- For skills that run on a schedule

---

**The bar:** a skill isn't done when it's written -- it's done when it's been tested and survives real input. A system isn't done until the whole chain runs end to end. Don't stop at "authored."
