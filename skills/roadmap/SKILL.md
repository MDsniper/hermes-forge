---
name: roadmap
description: "Triage front door and build ladder for Hermes Forge. TWO entry modes: (1) Ladder mode -- walks you from first skill to reliable automated systems. (2) Triage mode -- you describe a problem, it figures out what to build and routes to the right builder. USE WHEN user says 'what's next', 'what should I build', 'where am I', 'roadmap', 'I want to automate X', 'I keep doing X by hand', 'help me figure out what to build', 'what should I build next', 'look at what I have and tell me what to build'."
---

# Roadmap -- Triage and Build Ladder

Two entry modes. Pick based on where the user is.

## Mode 1: Triage (user has a problem)

When the user describes a pain point or goal:

1. **Classify the problem:**
   - Recurring manual task -> build a **skill**
   - Multi-step process -> build a **skill system**
   - Needs enforcement -> add a **gate/harness**
   - Needs external data -> add an **MCP/server connection**
   - Runs on a schedule -> create a **cron job**
   - Triggered by event -> create a **hook** (if Hermes supports it)
   - Quick shortcut -> create a **command**

2. **Explain why** that's the right shape
3. **Route to the builder:**
   - Single skill -> `forge-skill` create-skill workflow
   - Skill system -> `forge-skill` build-skill-system workflow
   - Business mapping -> `business-xray`

## Mode 2: Ladder (user wants direction)

Walk through these stages in order:

| Stage | What to Build | Skill |
|-------|--------------|-------|
| 1 | First custom skill | `forge-skill` |
| 2 | Skill with proper triggers | `forge-skill` (optimize-description) |
| 3 | Skill with validation | `forge-skill` (validate-skill) |
| 4 | Skill with gate scripts | `forge-skill` (build-harness) |
| 5 | Skill system (multi-step) | `forge-skill` (build-skill-system) |
| 6 | Scheduled automation | `cronjob` tool |
| 7 | Business-wide mapping | `business-xray` |

**Assess where the user is** by scanning their skills directory:
- No skills? -> Stage 1
- Has skills but no validation? -> Stage 3
- Has validated skills? -> Stage 5
- Has systems? -> Stage 6

Show the current stage and the single next move.

## When to Activate

**Activate when:**
- User asks "what should I build next"
- User describes a pain point and wants direction
- User wants to see their progress
- User says "roadmap" or "what's next"

**Do NOT activate when:**
- User already knows what to build -> go straight to `forge-skill` or `business-xray`
- User wants to fix a broken skill -> route to `retrospective`
