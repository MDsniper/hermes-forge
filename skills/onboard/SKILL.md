---
name: onboard
description: "First-run setup for Hermes Forge. Scaffolds the skill authoring workspace, creates a workspace guide, and walks you through building your first custom skill. USE WHEN user says 'onboard me', 'set me up', 'get me started', 'start my workspace', 'first time setup', 'bootstrap my workspace', 'build my first skill'."
---

# Onboard -- First-Run Setup

Three-phase guided setup. ~10 minutes.

## Phase 1: Scaffold Workspace

Create the authoring directories:

```
~/.hermes/skills/        (already exists - where skills live)
~/hermes-forge/          (project workspace for building)
```

Verify the Forge skills are installed:
- forge-skill
- business-xray
- roadmap
- retrospective

If any are missing, note it and offer to install.

## Phase 2: Map Your Business (Optional)

If the user wants to understand their business first:
-> Route to `business-xray` for a quick Business Map

If they want to jump straight to building:
-> Skip to Phase 3

## Phase 3: Build Your First Skill

Walk through creating a simple skill using `forge-skill`:

1. Ask what they do repeatedly that a skill could handle
2. Use the create-skill workflow to build it
3. Test it with a real prompt
4. Iterate until it works

**Good first-skill candidates:**
- Daily standup summary
- Email draft helper
- Meeting notes formatter
- Status report generator
- Quick research task

## Completion

After the first skill is built and tested:

"You're set up. Here's what you can do now:
- 'create a skill for X' -- build more skills
- 'business x-ray' -- map your operations
- 'roadmap' -- see what to build next
- 'retrospective' -- fix a skill that went wrong"
