---
name: retrospective
description: "Capture learnings from skill usage and propose SKILL.md improvements. USE WHEN user says 'retrospective', 'this skill messed up', 'fix this skill', 'improve this skill', 'the skill got it wrong', 'update the skill', 'capture what went wrong', 'skill-level post-mortem', or when a skill produces wrong output and the user wants to patch its instructions."
---

# Retrospective -- Fix Skills After They Misbehave

Skills get better when you patch them after real failures, not from pure forethought.

## Two Entry Modes

### Mode 1: Immediate Fix

**When:** "fix this skill", "heal this skill", "the skill got X wrong"

1. Read the skill's SKILL.md
2. Identify what went wrong vs what the skill instructed
3. Propose a surgical patch using the Evidence-Driven discipline
4. Apply with approval using `skill_manage(action=patch)`

### Mode 2: Session Scan

**When:** "retrospective", "review the session", "any skill issues today"

1. Review the session for skill-related friction points
2. Classify each: fixable with a patch vs. needs a new workflow vs. user error
3. Propose patches ranked by impact
4. Apply approved patches

## The Patch Discipline

Before patching ANY skill, follow this order:

1. **Origin** -- Note the date, what happened, who caught it. A rule with no origin is a preference.
2. **Carve-out** -- Name the case where this rule must NOT apply. Over-correction is usually costlier.
3. **Mechanical or judgment?** -- If detectable by regex/script, it belongs in a gate script, not prose.
4. **One home** -- If the rule's canonical home is another skill, point to it. Don't restate.
5. **Measure** -- If the change is significant, note that it's unmeasured, or run a quick test.

## Patching with skill_manage

```
# Surgical edit to a specific section
skill_manage(action=patch, name="skill-name", old_string="...", new_string="...")

# Major rewrite (use sparingly)
skill_manage(action=edit, name="skill-name", content="...")
```

Always use `patch` for surgical fixes. Only use `edit` for full rewrites.

## Version Tracking

After patching, add a version note at the bottom of the SKILL.md:

```markdown
---
**Patch History:**
- [YYYY-MM-DD] Description of change and why
```

## Related Skills

- **New skill needed** -> route to `forge-skill`
- **Skill needs restructuring** -> route to `forge-skill` (upgrade-skill workflow)
- **Automation failed** -> check if the cron job needs updating
