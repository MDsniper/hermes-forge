# Business X-Ray

Source: business-x-ray/workflows/implementation-router.md
MIME: text/markdown

# Implementation Router Workflow

**Classify opportunities, generate a CLO Workspace build plan, and hand off to meta-create-skill or meta-create-mcp.**

---

## Purpose

This workflow runs AFTER the Roadmap is generated. It bridges diagnosis (what's wrong) and execution (building out the CLO Workspace):

1. Classifies each Roadmap item into a CLO Workspace component type
2. Generates a structured Build Plan with dependencies and order
3. Hands off the first item to `meta-create-skill` or `meta-create-mcp` with pre-filled context

**Design principle:** Bias toward building. The user should leave this step with their first CLO Workspace component ready to start, not just a plan.

**What is a CLO Workspace?** An AI-powered business operating system built on Notion. Every component — AI Employees (skills), Digital Assets (databases/templates), Integrations (connections), and Playbooks (SOPs) — lives in one unified workspace. The X-Ray diagnosed what's broken. The Implementation Router builds the fix.

---

## Prerequisites

Before running this workflow:
- [ ] Business Map complete
- [ ] At least one process expanded with opportunities
- [ ] Action Roadmap generated (DO FIRST / DO NEXT / DO LATER)
- [ ] System Connection Map complete (recommended but not required)

---

## Entry Point

This workflow triggers at the end of `generate-roadmap.md` or when the user says:

- "let's build this"
- "implementation plan"
- "what should I build first"
- "create a skill for this"
- "turn this into an AI employee"
- "how do I implement this"

---

## Phase 1: Opportunity Classification (Inference-First)

### Step 1: Pull DO FIRST Items from Roadmap

Gather the DO FIRST items from the Action Roadmap. For each one, classify into an implementation type.

**Classification logic:** Reference `references/implementation-types.md` for detailed patterns.

### Step 2: Present Classification

Present as inference — Claude guesses, user confirms:

> "Based on your X-Ray, here's what I'd build and how:
>
> **OPPORTUNITY CLASSIFICATION**
>
> | # | Opportunity | Type | Routes To |
> |---|-------------|------|-----------|
> | 1 | Content bottleneck (3hrs/week writing from scratch) | AI Employee | `meta-create-skill` → Content Drafting Skill |
> | 2 | YouTube → ConvertKit manual subscriber sync | Integration | `meta-create-mcp` or Zapier setup |
> | 3 | No CRM system for tracking clients | Digital Asset | Notion database + template |
> | 4 | Manual proposal writing (2hrs each) | AI Employee | `meta-create-skill` → Proposal Generator |
> | 5 | No follow-up system after sales calls | Process + Digital Asset | SOP + email sequence template |
>
> **AI Employees** = Skills that Claude runs for you (draft content, generate proposals, prep for calls)
> **Integrations** = Connecting tools that don't talk to each other yet
> **Digital Assets** = Templates, databases, SOPs you build once and reuse
> **Process Changes** = New workflows or SOPs (no code needed)
>
> Does this classification match? Anything you'd change?"

STOP. Wait for response.

### Step 3: Confirm or Adjust

If user adjusts:
> "Got it — moving [X] from [Type A] to [Type B]. Updated."

If user confirms:
> "Great. Let me build your implementation plan."

---

## Phase 2: Build Plan Generation

### Step 4: Identify Dependencies

Map dependencies between items. Common patterns:

| Dependency Pattern | Example |
|-------------------|---------|
| **Data source first** | CRM database must exist before CRM automation skill |
| **Template before AI** | Proposal template must exist before proposal generator skill |
| **Integration before automation** | Stripe→Notion connection before auto-onboarding skill |
| **SOP before delegation** | Process documented before VA can execute |

### Step 5: Generate Build Plan

Present the structured build plan:

> "Here's your Implementation Plan — what to build, in what order:
>
> **WEEK 1: Foundation (Digital Assets + Quick Integrations)**
>
> 1. **Client CRM Database** [Digital Asset]
>    - Build: Notion database with client fields
>    - Fields: Name, Status, Source, Value, Last Contact, Notes
>    - Why first: Other builds need this data source
>    - Effort: ~1 hour
>
> 2. **YouTube → ConvertKit Sync** [Integration]
>    - Build: Zapier trigger (new YouTube subscriber → ConvertKit tag)
>    - Connects: YouTube ↔ ConvertKit
>    - Why now: Quick win, immediate time savings
>    - Effort: ~30 minutes
>
> **WEEK 2: First AI Employee**
>
> 3. **Content Drafting Skill** [AI Employee → meta-create-skill]
>    - Input: Topic + angle + target audience
>    - Output: First draft + 3 headline options
>    - Dependencies: None (standalone)
>    - Effort: ~2 hours to build, saves 3hrs/week
>
> **WEEK 3-4: Second AI Employee + Process**
>
> 4. **Proposal Generator Skill** [AI Employee → meta-create-skill]
>    - Input: Client name + project scope + CRM notes
>    - Output: Draft proposal with pricing options
>    - Dependencies: Client CRM Database (#1)
>    - Effort: ~2 hours to build, saves 2hrs/proposal
>
> 5. **Post-Call Follow-Up SOP** [Process Change]
>    - Build: Checklist + email template
>    - Trigger: After every sales call
>    - Dependencies: None
>    - Effort: ~30 minutes
>
> **Total: 5 builds across 4 weeks**
> **Estimated time saved after implementation: ~6 hours/week**
>
> Want to adjust the order, or ready to start building #1?"

STOP. Wait for response.

### Step 6: Allow Reordering

If user wants to adjust order:

> "No problem. Which item do you want to move?"

Validate dependencies:
> "Quick note: [Item X] depends on [Item Y]. If you build X first, you won't have the [data/template] it needs. Want to:
> A) Build Y first (10 min), then X
> B) Build X without [dependency] and add it later"

### Step 7: Save Build Plan

Store the build plan as a YAML block for session continuity:

```yaml
# Implementation Plan
implementation_plan:
  client: [Business Name]
  date: [Date]
  total_builds: [count]
  estimated_weekly_savings: [hours]

  digital_assets:
    - name: [Asset Name]
      type: notion_db | template | sop | checklist
      data_source: [where data comes from]
      fields: [key fields if database]
      priority: week_1
      status: pending

  ai_employees:
    - name: [Skill Name]
      type: skill
      input: [what it takes]
      output: [what it produces]
      dependencies: [what must exist first]
      priority: week_2 | week_3
      status: pending

  integrations:
    - name: [Integration Name]
      type: mcp | zapier | native
      connects: [Tool A] → [Tool B]
      method: [zapier_trigger | native_api | mcp_server]
      priority: week_1
      status: pending

  process_changes:
    - name: [Process Name]
      type: sop | checklist | workflow
      trigger: [when it runs]
      dependencies: [what must exist first]
      priority: week_3
      status: pending

  build_order:
    week_1: [list of names]
    week_2: [list of names]
    week_3_4: [list of names]
    month_2: [list of names if any]
```

---

## Phase 3: Handoff

### Step 8: Select First Build

Identify the first item in the build order:

> "Let's start with **[First Item Name]**."

### Step 9: Generate Handoff Context

For the selected build, generate a structured handoff that `meta-create-skill` or `meta-create-mcp` can consume.

**For AI Employees (→ meta-create-skill):**

```yaml
handoff:
  build_type: skill
  name: [Skill Name]
  purpose: [1-sentence from X-Ray findings]

  input:
    required:
      - [Input 1]: [description]
      - [Input 2]: [description]
    optional:
      - [Input 3]: [description]

  output:
    - [Output 1]: [format/description]
    - [Output 2]: [format/description]

  tools_involved: [from Tool Inventory]
  connections_needed: [from Connection Map]

  context: |
    [Summary of relevant X-Ray findings:
     - Which process this fixes (from swimlane)
     - What the current pain point is (from annotations)
     - What tools are already in use (from Tool Inventory)
     - How this connects to other systems (from Connection Map)]

  success_criteria: |
    [What "done" looks like:
     - User can provide [input] and get [output]
     - Output quality matches [standard]
     - Saves approximately [X] hours/week]
```

**For Integrations (→ meta-create-mcp):**

```yaml
handoff:
  build_type: mcp
  name: [Integration Name]
  purpose: [1-sentence from X-Ray findings]

  source_tool: [Tool A]
  target_tool: [Tool B]
  data_flow: [what moves between them]
  trigger: [what initiates the flow]

  current_state: manual | broken | missing
  desired_state: automated

  tools_involved: [from Tool Inventory]
  api_details: |
    [Known API capabilities from common-tool-integrations.md]

  context: |
    [Summary of relevant X-Ray findings:
     - Which processes this bridge appears in
     - Current manual workaround
     - Impact of automating (hours saved, errors prevented)]
```

**For Digital Assets (→ manual build or meta-create-skill):**

```yaml
handoff:
  build_type: digital_asset
  name: [Asset Name]
  purpose: [1-sentence from X-Ray findings]
  asset_type: notion_db | template | sop | checklist | landing_page | email_sequence

  structure: |
    [What the asset contains:
     - Fields (if database)
     - Sections (if template/SOP)
     - Steps (if checklist)]

  data_source: [where existing data lives]
  used_by: [which processes reference this asset]

  context: |
    [Summary of relevant X-Ray findings]
```

### Step 10: Present Handoff and Launch

> "Here's the build context for **[First Item]**:
>
> **Type:** [AI Employee / Integration / Digital Asset]
> **Purpose:** [1-sentence]
> **Input:** [what it needs]
> **Output:** [what it produces]
> **Dependencies:** [what must exist] ✅ / ⏳
>
> Ready to build? Say:
> - **'create a skill for [X]'** → I'll start building the AI Employee
> - **'create an MCP for [X]'** → I'll set up the integration
> - **'build [X]'** → I'll create the digital asset
>
> Or:
> - **'skip to #2'** → Move to the next item
> - **'save plan'** → Save the build plan and come back later"

STOP. Wait for response.

### Step 11: Route to Builder

Based on user's choice:

| User Says | Route To | Context Passed |
|-----------|----------|----------------|
| "create a skill for X" | `meta-create-skill` skill | Handoff YAML (skill type) |
| "create an MCP for X" | `meta-create-mcp` skill (if exists) or manual setup guide | Handoff YAML (mcp type) |
| "build X" (digital asset) | Inline creation or Notion setup | Handoff YAML (digital_asset type) |
| "skip to #2" | Loop back to Step 8 with next item | — |
| "save plan" | Output resume block and end | — |

**When routing to meta-create-skill:**

> "Starting the build for **[Skill Name]**...
>
> I'm passing along:
> - What this skill does (from your X-Ray)
> - What inputs it needs
> - What output it should produce
> - Which tools it connects to
>
> Let's build it."

Then invoke the `meta-create-skill` skill with the handoff context.

**When routing to manual build (digital assets):**

Help the user build it inline:
- Notion database → Create structure, suggest fields, provide setup steps
- Template → Draft the template content
- SOP → Write the step-by-step process
- Checklist → Create the checklist items

---

## Decision Points (Between Builds)

After completing each build:

> "**[Item Name]** is done! ✅
>
> Your build plan progress:
> ✅ [Completed Item 1]
> ✅ [Completed Item 2]
> ⏳ [Next Item] ← up next
> ○ [Future Item]
> ○ [Future Item]
>
> **What's next?**
> A) **Build next item** — [Next Item Name] ([Type])
> B) **Test what we built** — Run [Completed Item] to see it work
> C) **Adjust the plan** — Priorities changed
> D) **Save and stop** — Come back later with your progress state"

---

## Output: Build Plan (HTML Section — Optional)

If the user wants a visual build plan, generate as a new HTML section in the report:

```
┌─────────────────────────────────────────────────────────────┐
│                  IMPLEMENTATION PLAN                          │
│                                                               │
│  WEEK 1: FOUNDATION                                          │
│  ─────────────────                                           │
│  ☐ 📦 Client CRM Database          [Digital Asset]           │
│     Notion database · ~1hr                                   │
│                                                               │
│  ☐ 🔗 YouTube → ConvertKit Sync     [Integration]            │
│     Zapier trigger · ~30min                                  │
│                                                               │
│  WEEK 2: FIRST AI EMPLOYEE                                   │
│  ─────────────────────────                                   │
│  ☐ 🤖 Content Drafting Skill        [AI Employee]            │
│     meta-create-skill · ~2hrs · saves 3hrs/week                   │
│     └── depends on: none                                     │
│                                                               │
│  WEEK 3-4: SCALE                                             │
│  ───────────────                                             │
│  ☐ 🤖 Proposal Generator            [AI Employee]            │
│     meta-create-skill · ~2hrs · saves 2hrs/proposal               │
│     └── depends on: Client CRM Database ☐                    │
│                                                               │
│  ☐ 📋 Post-Call Follow-Up SOP       [Process]                │
│     Checklist + template · ~30min                            │
│                                                               │
├─────────────────────────────────────────────────────────────┤
│  🤖 = AI Employee   📦 = Digital Asset                       │
│  🔗 = Integration   📋 = Process Change                      │
│  Total: 5 builds · Est. savings: 6hrs/week                   │
└─────────────────────────────────────────────────────────────┘
```

**Color Coding:**

| Type | Border | Fill |
|------|--------|------|
| AI Employee | Blue `#6C8EBF` | `#DAE8FC` |
| Digital Asset | Purple `#9370DB` | `#f5f0ff` |
| Integration | Green `#82b366` | `#d5e8d4` |
| Process Change | Orange `#FFA500` | `#fff8e6` |

---

## Resume Block

At end of session:

```yaml
# Business X-Ray Progress - Implementation
stage: implementation_router
business_type: [type]
business_map_complete: true
bowtie_complete: true
roadmap_complete: true
system_connection_map_complete: [true/false]

implementation_plan:
  total_builds: [count]
  completed: [count]
  in_progress: [current item name]
  next_up: [next item name]
  builds:
    - name: [Name]
      type: [skill | mcp | digital_asset | process]
      status: [complete | in_progress | pending]
      week: [1 | 2 | 3-4]

handoff_context: |
  [Current handoff YAML for the in-progress or next build]

last_updated: [date]
```

---

## Build Plan Diagram (Optional)

If user wants the build plan HTML section, generate it directly:

1. Read the references for layout patterns
2. Generate the build plan HTML with classified opportunities
3. Append as new section to the report HTML at `~/hermes-xray-reports/reports/[business-name]-xray-[date].html`
4. Tell the user: "Build plan added to your report."
   - **Color coding:**
     - AI Employee: Blue border #6C8EBF, fill #DAE8FC
     - Digital Asset: Purple border #9370DB, fill #f5f0ff
     - Integration: Green border #82b366, fill #d5e8d4
     - Process Change: Orange border #FFA500, fill #fff8e6
   - Include: Progress tracking (checkboxes), dependency arrows, time estimates, weekly savings
   4. Tell the user: "Implementation Plan section added to your report."

---

## Next Workflow

After Implementation Router:
- **Build AI Employee:** → invoke `meta-create-skill` with handoff context
- **Build Integration:** → invoke `meta-create-mcp` or provide Zapier setup guide
- **Build Digital Asset:** → inline creation (Notion DB, template, SOP)
- **Save and return later:** → resume block with build plan state