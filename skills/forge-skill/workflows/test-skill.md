# Test Skill -- Eval Loop

Run a skill against salted fixtures to measure whether it actually works.

---

## When to Use

- "test skill", "eval skill", "run benchmarks"
- "is this skill actually good?"
- Before and after any significant skill change
- When a skill "feels useful" but hasn't been measured

---

## Step 1: Create the Salted Fixture

A fixture is a realistic input with two kinds of problems embedded:

**REMOVE seeds** -- problems the skill MUST fix:
- Banned phrases, wrong formats, missing sections
- Known violations that the skill's rules should catch
- Number them: R1, R2, R3...

**KEEP traps** -- things the skill must NOT touch:
- Correct content that looks like a violation but isn't
- Voice/style elements that must survive
- Number them: K1, K2, K3...

Save the fixture:
```
write_file(path="[skill-dir]/evals/fixture.md", content="...")
```

---

## Step 2: Write the Deterministic Scorer

A script that checks the output against the fixture:

```bash
#!/bin/bash
# Scorer for [skill-name]
OUTPUT="$1"
PASS=0
FAIL=0

# REMOVE checks (pattern must be ABSENT after skill runs)
check_remove() {
    local id="$1" pattern="$2"
    if grep -qP "$pattern" "$OUTPUT"; then
        echo "FAIL $id: pattern still present"
        FAIL=$((FAIL + 1))
    else
        echo "PASS $id: pattern removed"
        PASS=$((PASS + 1))
    fi
}

# KEEP checks (pattern must be PRESENT after skill runs)
check_keep() {
    local id="$1" pattern="$2"
    if grep -qP "$pattern" "$OUTPUT"; then
        echo "PASS $id: pattern preserved"
        PASS=$((PASS + 1))
    else
        echo "FAIL $id: pattern lost"
        FAIL=$((FAIL + 1))
    fi
}

# Add your checks here
# check_remove "R1" "banned phrase"
# check_keep "K1" "voice marker"

TOTAL=$((PASS + FAIL))
echo ""
echo "Score: $PASS/$TOTAL"
if [ $FAIL -eq 0 ]; then
    echo "VERDICT: PASS"
else
    echo "VERDICT: FAIL ($FAIL failures)"
fi
```

Save in `evals/scorer.sh`.

---

## Step 3: Run the Variants

**Variant A -- with the skill:**
```
Run the skill against the fixture input.
Save output to evals/output-A.md
```

**Variant B -- with proposed changes (if testing a modification):**
```
Run the modified skill against the same fixture.
Save output to evals/output-B.md
```

**Variant C -- no skill (the control):**
```
Run the same prompt WITHOUT loading the skill.
Save output to evals/output-C.md
```

The control (C) tells you if the skill earns its existence. If C matches A, the skill is decoration.

---

## Step 4: Score and Compare

Run the scorer on each variant:

```bash
bash evals/scorer.sh evals/output-A.md
bash evals/scorer.sh evals/output-B.md
bash evals/scorer.sh evals/output-C.md
```

---

## Step 5: Set the Pass Bar

Define what "passing" means:

| Criterion | Threshold |
|-----------|-----------|
| REMOVE seeds fixed | >= 85% |
| KEEP traps preserved | 100% |
| Mechanical violations | 0 |
| Length retention | 70-110% of input |

Record the pass bar in `evals/pass-bar.md`.

---

## Step 6: Report Results

```markdown
# Eval Report: [skill-name]

## Variants
| Variant | Seeds Fixed | Traps Kept | Violations | Score |
|---------|-------------|------------|------------|-------|
| A (current) | X/Y | X/Y | N | XX% |
| B (proposed) | X/Y | X/Y | N | XX% |
| C (no skill) | X/Y | X/Y | N | XX% |

## Verdict
[PASS/FAIL] at [threshold]% bar

## Recommendations
- [What to fix]
- [What to keep]
```

---

## Regression Rule

The harness outlives the experiment. After any edit to the skill:
1. Re-run the eval
2. Must stay above the pass bar
3. If it drops, investigate before shipping

Save results: `write_file(path="[skill-dir]/evals/results.json", content="...")`
