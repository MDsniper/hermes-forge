# Hermes Forge

A native Hermes Agent toolkit for building AI automation -- skills, workflows, cron jobs, and subagent pipelines. Ported and adapted from the AI Employee Builder methodology with permission.

## What This Is

Hermes Forge is a skill authoring and business automation framework built specifically for Hermes Agent. It contains:

- **forge-skill** -- The core skill authoring toolkit. Create, validate, test, and improve Hermes skills using evidence-driven design methodology.
- **business-xray** -- Map, diagnose, and optimize your business operations. Find the highest-leverage automation opportunities.

## Installation

```bash
# Copy the skills to your Hermes skills directory
cp -r skills/* ~/.hermes/skills/

# Or symlink for easy updates
ln -s /path/to/hermes-forge/skills/forge-skill ~/.hermes/skills/forge-skill
ln -s /path/to/hermes-forge/skills/business-xray ~/.hermes/skills/business-xray
```

## Quick Start

```
# Create a new skill
"create a skill for daily standup summaries"

# Build a multi-step automation system
"build a skill system for client onboarding"

# Validate an existing skill
"validate the email-drafter skill"

# Map your business operations
"run business x-ray on my workflow"
```

## The Five Laws of Skill Design

These are measured, not vibes. Each law has eval evidence behind it.

1. **Guide, don't prescribe** -- Ship gotchas and frameworks, not comprehensive docs. A 50-line gotcha distillation matched a 575-line skill stack at 30% fewer tokens.
2. **One home per rule** -- Workflows are spine; rules live in their canonical skill. Inlined copies rot.
3. **Enforce, don't instruct** -- Mechanical rules become scripts with VERDICT evidence. A prose "zero tolerance" rule was violated in 8 of 9 measured runs.
4. **Measure, don't assume** -- Eval before and after any significant skill change. "Feels better" is how dead weight accumulates.
5. **Real examples beat rule-prose** -- Verbatim gold-standard samples carry behavior better than descriptions.

## Architecture

```
skills/
├── forge-skill/              # The skill authoring toolkit
│   ├── SKILL.md              # Router + core instructions
│   ├── workflows/            # Create, validate, test, harden
│   ├── references/           # Design specs, mechanism selection
│   └── templates/            # Skill templates for common patterns
│
└── business-xray/            # Business process mapping
    ├── SKILL.md              # Router + interview framework
    ├── workflows/            # Progressive analysis workflows
    └── references/           # Archetypes, templates, frameworks
```

## Platform Notes

Hermes Forge is built for Hermes Agent and uses:
- `skill_manage` for creating/editing skills
- `delegate_task` for isolated subagent execution (replaces Claude Code's `context: fork`)
- `cronjob` for scheduled/recurring automation (replaces Claude Code's `/schedule`)
- Standard file reads for loading workflow and reference content

## License

MIT. The methodology is adapted from the AI Employee Builder by Rashid Khamis (the2hourclo), ported to Hermes Agent conventions.
