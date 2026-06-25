# Build Harness -- Make Skills Production-Grade

Sort every quality rule into its enforcement mechanism and build each one.

---

## When to Use

- "make this production-grade"
- "add a harness"
- "the skill keeps ignoring its own rule"
- After `build-skill-system` (a chain isn't done until rules are enforced)
- After `create-skill` when the skill is proven and needs hardening

---

## Step 1: Inventory All Rules

Read the skill's SKILL.md and all workflows. List every rule, gotcha, and constraint.

For each rule, classify:

| Type | Definition | Action |
|------|-----------|--------|
| **Mechanical** | Detectable by regex/script | Build gate script |
| **Judgment** | Needs reading comprehension | Keep as prose gotcha, add origin + carve-out |
| **Systemic** | Emergent behavior across runs | Build eval harness |

---

## Step 2: Build Gate Scripts (Mechanical Rules)

For each mechanical rule, create a script in `scripts/`:

```bash
#!/bin/bash
# Gate: [rule name]
# Origin: [date + what happened]
FILE="$1"
VIOLATIONS=0

# [regex checks]
if grep -nP '[pattern]' "$FILE"; then
    echo "VIOLATION: [rule name] -- [description]"
    VIOLATIONS=$((VIOLATIONS + 1))
fi

if [ $VIOLATIONS -eq 0 ]; then
    echo "VERDICT: CLEAN"
else
    echo "VERDICT: $VIOLATIONS VIOLATION(S) -- fix and re-run"
fi
exit $VIOLATIONS
```

Add to the skill's exit checklist:
```markdown
- [ ] Run `bash scripts/validate.sh [output-file]` and paste VERDICT
```

---

## Step 3: Set Up STOP Gates (Irreversible Hand-offs)

For any step that produces something irreversible (publish, send, delete):

```markdown
### Step N: [Action]
[Instructions]

**STOP:** Paste the output above. Do not proceed until the user approves.
```

The orchestrator waits for approval before continuing.

---

## Step 4: Build the Eval Harness

For skills with systemic rules, create an eval:

1. **Salted fixture** -- a realistic input with known problems
2. **Scorer script** -- regex-based, counts violations
3. **Pass bar** -- e.g. >=85% seeds fixed, all traps kept, 0 mechanical violations

Save in the skill's `evals/` directory:

```
evals/
  fixture.md        # The test input
  scorer.sh         # The scoring script
  results.json      # Latest run results
```

Run the eval after every significant change to the skill.

---

## Step 5: Wire Up the Cron Check (Optional)

For skills that run on a schedule, add a validation step to the cron job:

```
cronjob(action=create, schedule="...", 
  prompt="Run [skill] then validate with scripts/validate.sh. Report VERDICT.")
```

---

## The Exit Checklist

- [ ] Every mechanical rule has a gate script
- [ ] Gate scripts print `VERDICT: CLEAN` on success
- [ ] The skill's exit checklist demands VERDICT pasted as evidence
- [ ] Irreversible hand-offs have STOP gates
- [ ] Eval harness exists (or at minimum no-skill control run)
- [ ] All scripts are executable
