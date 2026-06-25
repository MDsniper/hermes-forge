# Upgrade Skill -- Restructure and Modernize

Audit an existing skill's content, extract bloat, fix routing, and bring it up to current standards.

---

## When to Use

- "upgrade my skills", "fix my routing", "restructure this"
- "my skills are a mess", "make these skills chain together"
- SKILL.md growing past 500 lines
- Skill keeps failing the same way after multiple patches

---

## Step 1: Content Audit (Four-Class Labels)

Read the full SKILL.md + all workflow files. Label every section:

| Class | Definition | Action |
|-------|-----------|--------|
| **SPINE** | Step order, gates, delegation calls, paths | Keep inline |
| **DUPLICATE** | Restates a rule from another skill | Replace with named pointer |
| **STEP-DETAIL** | Only needed during one specific step | Move to a reference file |
| **STALE** | Contradicts a newer calibration or is outdated | Fix immediately -- live bug |

Print a summary:
```
SPINE:        XX% (XX lines)
DUPLICATE:    XX% (XX lines)
STEP-DETAIL:  XX% (XX lines)
STALE:        XX% (XX lines)
```

---

## Step 2: Fix Stale Content First

Stale content is a live bug -- it actively gives wrong instructions. Fix these before anything else.

For each STALE section:
1. Identify what it contradicts
2. Apply the correct version via `skill_manage(action=patch)`
3. Note the fix in the patch history

---

## Step 3: Extract Step-Detail to References

For each STEP-DETAIL block:
1. Create a reference file: `skill_manage(action=write_file, file_path="references/[name].md")`
2. Replace the inline block with a pointer:
   ```
   Before starting [step], read `references/[name].md` for [what it contains].
   ```
3. Verify the pointer is specific about WHEN and WHY to load

---

## Step 4: Replace Duplicates with Pointers

For each DUPLICATE:
1. Identify the canonical home skill
2. Replace inline content with:
   ```
   Definitions: see `[canonical-skill]`, section [Y].
   ```
3. Never restate -- just point

---

## Step 5: Check Architecture

Run the Architecture Decision Tree from forge-skill SKILL.md:

- Are there workflows that serve multiple parents? -> Extract to standalone skills
- Is the orchestrator doing work instead of routing? -> Extract that work
- Are any workflows orphaned (not referenced from SKILL.md)? -> Remove or add pointer

---

## Step 6: Fix Routing and Descriptions

Check the description:
- 5+ trigger phrases? If not, add them
- Clear exclusions pointing to siblings? If not, add them
- Two-Goal Rewrite Test: can it be described in one sentence with one verb? If not, split

---

## Step 7: Apply Changes

Build the restructured version as a NEW file alongside (never overwrite in-place):

```bash
cp ~/.hermes/skills/[name]/SKILL.md ~/.hermes/skills/[name]/SKILL.md.bak
```

Apply changes with `skill_manage(action=patch)` for surgical edits, or `skill_manage(action=edit)` for full rewrites.

---

## Step 8: Verify Invariants

After restructuring, check:
- [ ] Every workflow referenced in SKILL.md actually exists
- [ ] Every reference file listed is actually used
- [ ] No orphaned workflows
- [ ] SKILL.md body under 500 lines
- [ ] Gate scripts still referenced and functional

---

## Exit Checklist

- [ ] Four-class audit complete
- [ ] Stale content fixed
- [ ] Step-detail moved to references with pointers
- [ ] Duplicates replaced with named pointers
- [ ] Architecture review done
- [ ] Description has 5+ triggers and clear exclusions
- [ ] All changes verified
- [ ] Backup of original preserved
