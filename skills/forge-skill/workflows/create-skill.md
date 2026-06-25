# Create Skill -- The Full Workflow

Build a new Hermes skill from scratch. Follow these steps in order.

---

## Step 1: Gather the Brief

Before writing anything, understand what the skill needs to do.

**Ask the user:**
1. What does this skill do? (one sentence)
2. When should it trigger? (5-10 realistic phrases)
3. What does good output look like? (get a real example if possible)
4. What should it NOT do? (exclusions -> other skills)
5. Does it touch any external systems? (APIs, MCPs, files)

**If the user has a real artifact** (an email they wrote, a PR they reviewed, a report they generated):
- Save it as a gold-standard example in the skill's `assets/` directory
- This becomes Law 5 calibration material

---

## Step 2: Choose the Architecture

Use the Decision Tree from the main SKILL.md:

- **One job, user invokes by name?** -> Standalone skill
- **One job, parent routes to it?** -> Workflow inside parent
- **Multiple jobs in sequence?** -> Skill system (orchestrator + step-skills)
- **Needs fresh context?** -> Use `delegate_task` pattern

**Default to standalone.** Extracting later is cheap. Merging is expensive.

---

## Step 3: Write the SKILL.md

Use a template from `templates/`:
- `simple-skill-template.md` for 1-3 workflows
- `complex-skill-template.md` for multi-workflow skills
- `orchestrator-skill-template.md` for coordinators
- `cron-skill-template.md` for scheduled skills

**The SKILL.md must have:**

```yaml
---
name: skill-name           # kebab-case, matches directory name
description: "What it does. USE WHEN user says 'trigger 1', 'trigger 2', ..."
---
```

**Keep the body under 500 lines.** Split into workflows/ and references/ if it grows.

---

## Step 4: The Mechanism Pass

Read `references/mechanism-selection.md`. Walk every rule in your brief through the decision table:

| Rule from brief | Mechanism |
|---|---|
| "Never use em dashes" | Gate script |
| "Match this voice" | Verbatim example |
| "If unsure, check with user" | Prose gotcha |

Move anything mechanical into a gate script. Keep only judgment rules in prose.

---

## Step 5: Write Gate Scripts (if needed)

For mechanical rules, write a validation script:

```bash
#!/bin/bash
# Gate: check for banned patterns
FILE="$1"
VIOLATIONS=0

if grep -n '—' "$FILE"; then
    echo "VIOLATION: em dash found"
    VIOLATIONS=$((VIOLATIONS + 1))
fi

if [ $VIOLATIONS -eq 0 ]; then
    echo "VERDICT: CLEAN"
else
    echo "VERDICT: $VIOLATIONS VIOLATION(S) -- fix and re-run until CLEAN"
fi
```

Save in `scripts/validate.sh`. The skill's exit checklist must require the VERDICT.

---

## Step 6: Create the Skill

Use `skill_manage` to create the skill:

```
skill_manage(action=create, name="skill-name", content="...full SKILL.md...")
```

The skill directory is created at `~/.hermes/skills/skill-name/`.

For sub-files (workflows, references), use `skill_manage(action=write_file)`:

```
skill_manage(action=write_file, name="skill-name", file_path="workflows/my-workflow.md", file_content="...")
```

---

## Step 7: Write Real Examples

If you gathered gold-standard artifacts in Step 1, save them:

```
skill_manage(action=write_file, name="skill-name", file_path="assets/example-email.md", file_content="...the real email...")
```

The skill should reference these by name: "Match the tone of `assets/example-email.md`."

---

## Step 8: Test with a Real Prompt

Run the skill against a realistic input. Does it:
- Trigger correctly? (check the description)
- Produce output that matches the gold standard?
- Respect the exclusions?
- Handle edge cases?

If the output is wrong, go to `retrospective` to patch.

---

## Step 9: Quick Smoke Test (variant C)

Run the same prompt WITHOUT the skill loaded. If the bare model produces equally good output, the skill is decoration. Either:
- The skill needs more domain-specific gotchas (Law 1)
- The skill is solving a problem the model already handles

---

## Step 10: Version and Document

Add to the bottom of the SKILL.md:

```markdown
---
**Version:** 1.0.0
**Created:** YYYY-MM-DD
**Tests:** [describe what was tested]
```

---

## The Exit Checklist

Before declaring the skill done:

- [ ] Description has 5+ trigger phrases and exclusions
- [ ] Every rule answers "would the model get this wrong without it?"
- [ ] Mechanical rules have gate scripts with VERDICT lines
- [ ] 1-2 real examples saved in assets/
- [ ] Tested with a real prompt
- [ ] Bare-model control run at least once
- [ ] SKILL.md under 500 lines (or split into workflows/)
