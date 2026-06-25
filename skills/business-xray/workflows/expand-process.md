# Business X-Ray

Source: business-x-ray/workflows/expand-process.md
MIME: text/markdown

# Expand Process Workflow

**Drill into specific phases using 3-level progressive swimlanes, annotate opportunities.**

---

## Purpose

This workflow handles drilling down from Level 1 through Level 3:
1. Continues from `progressive-interview.md` Phase 3
2. Expands a specific phase into its sub-systems (Level 2)
3. Optionally expands a specific system into execution steps (Level 3) - case-by-case
4. Runs annotation review pass (add colors)
5. Presents opportunities with options

---

## 3-Level Swimlane Architecture

| Level | Lanes | What It Shows | Tool Names? |
|-------|-------|---------------|-------------|
| **Level 1: Process Flow** | Actor types (Owner \| AI \| Team \| Output) | WHAT phases happen, WHO owns each | No |
| **Level 2: System Detail** | Sub-systems or parallel workflows | WHICH systems handle each phase | No |
| **Level 3: Execution Detail** | Steps within a system | HOW each system works internally | Yes |

**Key differences:**
- **Level 1 lanes** = Actor types (who does the work)
- **Level 2 lanes** = Systems (which systems handle it)
- **Level 3 lanes** = Steps (how each system executes, with tool names)

**Key principle:** Start with process flow, drill into phases where pain surfaces. Level 3 is case-by-case - not every system needs it.

---

## Prerequisites

Before running this workflow:
- [ ] Business Map complete (Phase 1)
- [ ] Bow-Tie Funnel complete (Phase 2)
- [ ] Level 1 swimlane exists (from `progressive-interview.md` Phase 3)
- [ ] User has selected a phase to expand

---

## Level 2: System Detail Expansion

### When to Use

User says "drill into [phase]" or pain was detected in a Level 1 phase.

### Lanes

**Lanes become the sub-systems** that execute the phase (not actor types):

Examples by business type:
- **Coach/Consultant:** Scheduler | CRM | Email Sequences
- **Course Creator:** Content Platform | Email System | Payment Processor
- **Agency:** Project Management | Client Portal | Deliverables System
- **E-commerce:** Inventory | Order Processing | Fulfillment

### Infer the Sub-Systems

Based on the phase and business type, infer what systems handle it:

| Phase Type | Common Sub-Systems |
|-----------|-------------------|
| **Lead Capture** | Landing Page \| Email System \| CRM |
| **Sales Process** | Scheduler \| CRM \| Proposal Tool |
| **Onboarding** | Intake Form \| Welcome Sequence \| Setup System |
| **Fulfillment** | Delivery Platform \| Communication \| Support |
| **Content Creation** | Research \| Creation Tool \| Publishing |

### Present Inference

> "Let's break down [Client Onboarding] to see the systems involved:
>
> **LANES (sub-systems):**
> - Intake System
> - Welcome Sequence
> - Scheduling System
>
> These can run in parallel. Which one causes the most issues?"

**For HTML section generation:** Add the swimlane section to the report HTML directly. See `templates/report-template.html` for the swimlane HTML pattern.

Key rules: One element per slot. Sequential flow uses arrows. Branch and converge patterns use vertical stacking. Every element gets its own row even across lanes. Wider is better than taller. Max 2 stacked per lane.

### What to Ask at Level 2

**ONE question at a time:**
- "What systems handle this phase?"
- "Do these run in parallel or in sequence?"
- "Which system causes the most delays?"
- "What are the inputs and outputs?"

**Level 2 does NOT include tool names** - that's Level 3.

### CHECKPOINT: Level 2 Complete

> "Now I can see the systems involved in [Client Onboarding]. The Welcome Sequence seems straightforward, but [Intake System] has multiple steps.
>
> Want to drill into that system to see the actual steps and tools?"

**After confirmation:** If complex system → proceed to Level 3. Otherwise → annotation pass.

---

## Level 3: Execution Detail Expansion (Case-by-Case)

### When to Use

**Only when needed** - not every system requires Level 3. Use when:
- A system in Level 2 is complex (multiple steps)
- User says "show me how that works"
- SOP documentation would be valuable
- Bottleneck is inside a specific system

### Lanes

**Lanes become the steps** within the system:

> "Let's see exactly how [Intake System] works:
>
> **STEPS:**
> - Send Form (Typeform) → Collect Info → Store in CRM (HubSpot) → Trigger Welcome Email
>
> This takes about 5 minutes when automated. Is any part manual?"

**For HTML section generation:** Add the swimlane section to the report HTML directly. See `templates/report-template.html` for the swimlane HTML pattern.

Key rules: One element per slot. Sequential flow uses arrows. Branch and converge patterns use vertical stacking. Every element gets its own row even across lanes. Wider is better than taller. Max 2 stacked per lane.

### What to Ask at Level 3

**ONE question at a time:**
- "What are the actual steps in this system?"
- "What tools do you use for each step?"
- "How long does each step take?"
- "Which step is manual vs automated?"

### Level 3 Includes

| Element | Example |
|---------|---------|
| **Tool names** | Claude, Notion, Zapier, ConvertKit, Typeform |
| **Step sequence** | "Step 1 → Step 2 → Step 3" |
| **Time estimates** | "~2 min" on step boxes |
| **Manual vs automated** | Manual steps get orange border |
| **Inputs/Outputs** | "Form data in → CRM record out" |

### Connection Probe (During Level 3)

**When a tool name appears that was ALSO seen in a previous process swimlane**, ask ONE targeted connection question:

> "[Tool] came up earlier in your [Previous Process] for [previous use]. Now it's appearing in [Current Process] too. **Are these the same [Tool] workspace, or separate? Does data flow between them?**"

**Rules:**
- Only probe when a tool appears in **2+ processes** (first repeat triggers the question)
- **Max 1 probe per tool** — if the tool appears in a 3rd process, just note it silently
- Record the answer in the Tool Inventory: automated / manual / none
- Reference `references/common-tool-integrations.md` to make informed guesses about what CAN connect

**Examples:**
- "Notion came up earlier for content planning. Now it's in client onboarding. Same workspace, or separate?"
- "You use Zoom for both sales calls and coaching sessions. Do calendar events auto-create, or do you set those up separately?"
- "Stripe handles payments, and ConvertKit handles email. When someone pays, does ConvertKit know automatically?"

**Continue with Level 3 mapping after the probe — don't derail the process flow.**

### CHECKPOINT: Level 3 Complete

> "Now I can see exactly how [Intake System] executes. [Collect Info] is manual and takes 10 minutes - that could be automated.
>
> Ready to annotate and look at options?"

**After confirmation:** → Proceed to Annotation Review Pass

---

## Step 3: Annotation Review Pass

### Now Add Colors

Go through each step and apply annotations based on interview signals:

| Annotation | Border Style | Color | Apply When |
|------------|--------------|-------|------------|
| **Bottleneck** | Solid thick | Red (#FF6B6B) | User said "takes forever", "frustrating", "delays" |
| **Automate** | Dashed | Orange (#FFA500) | Repetitive, rule-based, AI could do this |
| **High Value** | Solid thick | Green (#90EE90) | Strategic, requires human judgment, should STAY with owner |
| **Normal** | Thin/none | Gray (#f5f5f5) | Standard step, nothing to flag |

### Review Each Step

> "Let me review each step:
>
> **[Step 1: Ideation]** - You mentioned this is where you get stuck sometimes. Marking as BOTTLENECK (red).
>
> **[Step 2: Research]** - This is repetitive lookup work. Marking as AUTOMATE (orange) - AI could draft this.
>
> **[Step 3: Create Draft]** - This is your creative work, high value. Marking as HIGH VALUE (green) - you should keep doing this.
>
> Does this assessment match your experience?"

---

## Step 5: Present Opportunities

### Opportunities List Format

After swimlane is annotated, present:

> "## Opportunities Identified
>
> **🔴 BOTTLENECK: [Step Name]**
> Currently takes [X hours/week]
>
> Options:
> - Create SOP/checklist to streamline
> - Delegate to VA (with template)
> - Simplify the process (remove unnecessary steps)
> - Batch process (do it all at once weekly)
>
> → Which fits your business?
>
> ---
>
> **🟠 AUTOMATE: [Step Name]**
> Currently manual, but rule-based
>
> Options:
> - AI tool to draft/assist (Claude, ChatGPT)
> - Zapier/automation workflow
> - Template + VA execution
> - Custom script/tool
>
> → Which fits your business?
>
> ---
>
> **🟢 HIGH VALUE: [Step Name]**
> Keep doing this yourself - it's strategic
>
> Options:
> - Protect time for this (calendar block)
> - Get faster at it (templates, shortcuts)
> - Make sure nothing else takes this time
>
> → How can you protect this time?"

### Opportunity Categories

Reference `references/opportunity-categories.md` for detailed options per category.

---

## Step 6: Decision Point

### Fix or Continue?

> "You now have:
> ✅ Business Map (complete)
> ✅ Bow-Tie Funnel (complete)
> ✅ [Process Name] Swimlane (annotated)
> ✅ [X] Opportunities identified
>
> **What would you like to do next?**
>
> A) **Fix first** - Take these opportunities and implement them before mapping more. I'll give you a mini-roadmap for just this process.
>
> B) **Keep mapping** - Let's expand another process. Which one: [list remaining pain points]?
>
> C) **System Connection Map** - See how all your tools connect across your business before building the roadmap.
>
> D) **Generate full roadmap** - Create a 90-day plan across all identified opportunities."

### Based on Response

- **Fix first:** Generate mini-roadmap for this process only → output actionable next steps → end session with resume block
- **Keep mapping:** Return to this workflow for next process
- **System Connection Map:** → `workflows/system-connection-map.md` (synthesizes Tool Inventory into network diagram, feeds integration opportunities into Roadmap)
- **Full roadmap:** Proceed to `generate-roadmap.md`

**Recommended flow:** Map at least 2 areas → System Connection Map → Roadmap. The connection map reveals integration opportunities that compound with process bottlenecks.

---

## Output: Process Swimlane

### For Claude Code

Save as new section in the report HTML:

- Use the swimlane HTML pattern from `templates/report-template.html`
- Each lane becomes a `.lane-row` div
- Each step becomes a `.step` div with optional annotation class (bottleneck/automate/high-value/digital-asset)
- Sequential steps separated by `<span class="arrow">→</span>`
- Apply annotation colors

### For Web/ChatGPT

Output XML:

```xml
<diagram name="[Process Name] Flow" id="process-[name]">
    <!-- Swimlane content -->
</diagram>
```

> "Add this page to your Business X-Ray file:
> 1. The expanded swimlane section is now in your report HTML at https://xray.bawai.org/reports/[name]-xray-[date].html

---

## Page Hierarchy (Single-Page Per Area)

Each process area lives on **ONE page** - all levels stacked vertically. No tab jumping.

```
Page 1: Business Overview
├── Business Map (top)
└── Bow-Tie Funnel (bottom)

Page 2: Lead Generation
├── Level 1: Process Flow (Owner | AI | Team | Output)
│   └── [Create Content] → [Capture] → [Nurture] → [Call] → [Close]
│
├── ─── DISCOVERY CALL PREP (Level 2: System Detail) ───
│   └── Calendar System | CRM System | Prep Workflow
│
└── ─── PREP WORKFLOW (Level 3: Execution Detail) ─── [if needed]
    └── Pull Info (HubSpot) → Generate Questions (Claude) → Review Notes (Notion)

Page 3: Sales Process
├── Level 1: Process Flow
│   └── [Qualify] → [Present] → [Propose] → [Close]
│
└── ─── PROPOSAL CREATION (Level 2: System Detail) ───
    └── Research System | Template System | Pricing Tool

Page 4: Fulfillment
├── Level 1: Process Flow
│   └── [Onboard] → [Deliver] → [Support] → [Complete]
│
└── ─── CLIENT ONBOARDING (Level 2: System Detail) ───
    └── Intake System | Welcome Sequence | Scheduling System

Page 5: Action Roadmap
```

**Benefits:**
- No tab jumping for related processes
- Scroll down for more detail (Level 1 → Level 2 → Level 3)
- Each "area" is self-contained
- Progressive disclosure: start with process flow, drill as needed
- Level 3 only added when a system is complex enough to warrant it

---

## When to Drill Down to Level 2

Drill down when:
- User says "that takes forever" about a phase
- Phase is complex (multiple systems involved)
- Phase is a bottleneck candidate

> "[Client Onboarding] sounds like it involves multiple systems. Want to see what's happening inside?"

---

## When to Drill Down to Level 3 (Case-by-Case)

**Not every system needs Level 3.** Only drill down when:
- A specific system in Level 2 is complex (multiple internal steps)
- User says "show me how that works" about a system
- Bottleneck is hiding inside a specific system
- SOP documentation would be valuable for delegation/training

> "[Prep Workflow] has several steps inside it. Want to see exactly how it works - the specific tools and steps?"

**Skip Level 3 when:**
- System is simple (1-2 steps)
- System is already well-understood
- No pain detected in that system

---

## Page Layout (3 Levels Stacked)

Each area page contains:
1. **Level 1: Process Flow** (top) - Actor lanes showing WHAT phases happen
2. **Divider** - Section label for the expanded phase
3. **Level 2: System Detail** (middle) - System lanes showing WHICH systems handle it
4. **Divider** - Section label for the expanded system (if Level 3 needed)
5. **Level 3: Execution Detail** (bottom, optional) - Step lanes showing HOW the system works

### Vertical Spacing

| Section | Y Position |
|---------|------------|
| Level 1 swimlane | y=40 |
| Level 2 divider | y=300 |
| Level 2 swimlane | y=340 |
| Level 3 divider | y=600 |
| Level 3 swimlane | y=640 |

**For HTML section generation:** Add the swimlane section to the report HTML directly. See `templates/report-template.html` for the swimlane HTML pattern.

---

## Mini-Roadmap Format

If user chooses "Fix first":

> "## [Process Name] - Quick Wins Roadmap
>
> ### This Week
> - [ ] 🔴 [Bottleneck fix] - [specific action]
> - [ ] Set up [quick automation]
>
> ### Next Week
> - [ ] 🟠 [Automation] - [specific tool/setup]
> - [ ] Create [template/SOP]
>
> ### Week 3-4
> - [ ] 🟢 [Protect high-value time] - [calendar action]
> - [ ] Review and refine
>
> Once you've implemented these, come back and we'll map the next process."

---

## Resume Block

At end of session:

```yaml
# Business X-Ray Progress
stage: process_expansion
business_type: [type]
business_map_complete: true
bowtie_complete: true
pain_points: [original list]
selected_process: [current process]
expanded_processes: [[process name]]
pending: [remaining processes]
opportunities_flagged: [count]
last_updated: [date]
```

---

## Next Workflow

- **If more processes to expand:** Loop back to this workflow
- **If ready for roadmap:** → `generate-roadmap.md`
- **If fixing first:** End session with mini-roadmap + resume block
