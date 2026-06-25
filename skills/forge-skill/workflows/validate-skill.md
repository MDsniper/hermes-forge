# Validate Skill -- Compliance Check

Score a skill across five dimensions. Output a structured report.

---

## The Five Dimensions

| Dimension | What to Check | Weight |
|-----------|--------------|--------|
| **Structure** | SKILL.md format, frontmatter, <500 lines, directory layout | 20% |
| **Routing** | Description triggers, exclusions, delegation patterns | 20% |
| **Activation** | Triggers fire correctly, doesn't over/under-trigger | 20% |
| **Documentation** | Examples, references, clear instructions | 20% |
| **Quality** | Five laws compliance, mechanism pass, gate scripts | 20% |

---

## Validation Process

### 1. Structure Check

- [ ] Frontmatter has `name` and `description`
- [ ] Description is in double quotes
- [ ] SKILL.md body under 500 lines
- [ ] Directory follows anatomy (SKILL.md + optional workflows/ references/ scripts/ assets/)
- [ ] No stale references to files that don't exist

### 2. Routing Check

- [ ] Description has 5+ trigger phrases
- [ ] Description has "USE WHEN" clause
- [ ] Description has "Do NOT use when" exclusions pointing to siblings
- [ ] Workflow routing table matches the trigger phrases
- [ ] No orphan workflows (every workflow is referenced from SKILL.md)

### 3. Activation Check

- [ ] Test: does the skill trigger on its listed phrases?
- [ ] Test: does it NOT trigger on excluded phrases?
- [ ] Test: does it handle ambiguous inputs gracefully?

### 4. Documentation Check

- [ ] Each workflow has clear "When to use" and "Output" descriptions
- [ ] Examples exist for common patterns
- [ ] Reference files are listed with "read" pointers and load-when guidance
- [ ] No restated rules from other skills (Law 2)

### 5. Quality Check (Five Laws)

- [ ] Law 1: No comprehensive docs that the model already knows
- [ ] Law 2: No duplicated rules from other skills
- [ ] Law 3: Mechanical rules have gate scripts, not just prose
- [ ] Law 4: At least a no-skill control was run once
- [ ] Law 5: Real examples exist for calibration

---

## Scoring

Rate each dimension 0-100:

| Score | Meaning |
|-------|---------|
| 90-100 | Excellent -- ship it |
| 70-89 | Good -- minor fixes |
| 50-69 | Needs work -- address the lowest dimension |
| 0-49 | Rebuild -- fundamental issues |

**Overall score** = weighted average of all five dimensions.

---

## Output Format

```
# Validation Report: [skill-name]

## Scores
- Structure:    XX/100
- Routing:      XX/100
- Activation:   XX/100
- Documentation: XX/100
- Quality:      XX/100
- **Overall:    XX/100**

## Issues Found
1. [Dimension] [Description of issue] -> [Fix]
2. ...

## Recommendations
- [Priority 1 fix]
- [Priority 2 fix]
```
