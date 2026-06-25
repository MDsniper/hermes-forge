# Business X-Ray

Source: business-x-ray/references/swimlane-templates.md
MIME: text/markdown

# Swimlane Templates

**Pre-built process templates for fast swimlane generation.**

Use these as starting points - adjust based on user's actual process during expansion.

---

## CONNECTION RULES (CRITICAL)

> **Every box needs an ID. Every arrow needs source and target matching those IDs.**

### The Pattern

1. **Give every box a unique ID** - `id="step-1"`, `id="step-2"`, etc.
2. **Connect with arrows** - `source="step-1" target="step-2"`
3. **Arrow parenting:**
   - **Same-lane arrows** → `parent="1"` (root)
   - **Cross-lane arrows** → `parent="pool-id"` (the pool, NOT root)
4. **Arrows are edges** - `edge="1"` attribute required

> **Why cross-lane arrows parent to pool:** Shapes inside lanes have coordinates relative to their lane. The pool is the common ancestor, so arrows parented to the pool correctly resolve coordinates for shapes in different lanes.

### ID Naming

| Element | Pattern | Example |
|---------|---------|---------|
| Pool | `{process}-pool` | `content-pool` |
| Lane | `{process}-lane-{actor}` | `content-lane-owner` |
| Step | `{process}-step-{n}` | `content-step-1` |
| Arrow | `{process}-arrow-{n}` | `content-arrow-1` |

### Positioning Formula

- **X spacing:** First box at x=100, then +150 for each (box=100px + gap=50px)
- **Y centering:** (lane_height - box_height) / 2 = typically y=25
- **Pool width:** 100 + (150 × num_steps) + 50

---

## LANE ASSIGNMENT GUIDE

**The #1 mistake: putting collaborative steps in the AI lane.** If the owner is involved and driving the work — even with AI assistance — it goes in the OWNER lane with an "(AI-Supported)" label.

### Decision Tree: Which Lane?

```
Is the owner involved in this step?
├── YES → Does the owner make the decisions / apply judgment?
│   ├── YES → OWNER lane + "(AI-Supported)" if AI assists
│   │   Examples: Edit Video, Write Newsletter, Choose Topic, Review Draft
│   └── NO → AI/SYSTEM lane (owner just triggers it)
│       Examples: Auto-send welcome email, Format for Substack
└── NO → AI/SYSTEM lane
    Examples: Title generation, Hook development, Draft writing, Polish passes
```

### Common Lane Assignments

| Step | Lane | Why |
|------|------|-----|
| Topic/Angle Selection | OWNER | Judgment, taste, strategy |
| Content Recording | OWNER | Creative, irreplaceable |
| Video Editing | OWNER (AI-Supported) | Taste-driven collaboration |
| Newsletter Writing | OWNER (AI-Supported) | Owner drives, AI drafts |
| Title/Hook Generation | AI/SYSTEM | AI generates options, owner selects |
| Structure + Draft | AI/SYSTEM | AI builds, owner reviews |
| Humanize + Format | AI/SYSTEM | Automated polish passes |
| Review + Add Stories | OWNER | Only owner has the stories |
| Final Approval | OWNER | Quality gate |
| Publish + Distribute | AI/SYSTEM | Automated delivery |
| Welcome Email | AI/SYSTEM | Triggered automatically |
| Social Repurpose | AI/SYSTEM | AI transforms content |

### Sub-Process Template (Owner + AI Collaboration)

Most creative processes follow this 4-lane pattern:

```
CONTENT PLANNING (Owner)  → Topic, angle, direction decisions
AI PIPELINE (AI/System)   → Generate, draft, structure
HUMAN REVIEW (Owner)      → Add stories, judgment, approve
DISTRIBUTION (AI/Output)  → Polish, publish, repurpose
```

---

## BOTTLENECK DIAGNOSIS FRAMEWORK

**When a step is flagged as a bottleneck (red) in the OWNER lane, diagnose the fix type:**

```
OWNER lane bottleneck detected
├── Is this step TASTE/JUDGMENT dependent?
│   ├── YES → Keep in OWNER lane, but add AI support
│   │   FIX: Create a Skill (AI Employee) that drafts/prepares
│   │   Result: Owner reviews instead of creates from scratch
│   │   Example: "Write proposal" → AI drafts, owner reviews
│   └── NO → Move to AI/SYSTEM lane entirely
│       ├── Is it repeatable with predictable input/output?
│       │   ├── YES → Create a Skill (AI Employee)
│       │   │   Routes to: meta-create-skill
│       │   └── NO → Is it connecting two systems?
│       │       ├── YES → Build an Integration
│       │       │   Routes to: meta-create-mcp or Zapier
│       │       └── NO → Build a Digital Asset
│       │           Routes to: template, SOP, landing page
│       └── Is the owner doing it because no one else can?
│           ├── YES, needs documentation → Build SOP (Digital Asset)
│           │   Then delegate
│           └── YES, needs special access → Build Integration
│               Automate the access/trigger
```

### Diagnosis Presentation Format

> **Bottleneck:** [Step Name] — currently in OWNER lane, taking [X hours/week]
>
> **Diagnosis:** This is [taste-dependent / repeatable / system-bridging]
>
> **Recommended Fix:** [Create Skill / Build Integration / Build Digital Asset / Process Change]
> - **What it does:** [Specific description]
> - **Owner's new role:** [Reviews instead of creates / Approves instead of executes / Not involved]
> - **Time saved:** [Estimate]
> - **Build effort:** [Estimate]
>
> **Routes to:** `meta-create-skill` / `meta-create-mcp` / inline build

---

## COMPLETE WORKING EXAMPLE

**This shows the exact XML pattern. Copy the structure, change the content.**

```xml
<!-- POOL -->
<mxCell id="example-pool" value="Process Name" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=30;fillColor=#f5f5f5;strokeColor=#666666;fontStyle=1;fontSize=14;" vertex="1" parent="1">
    <mxGeometry x="40" y="40" width="600" height="200" as="geometry"/>
</mxCell>

<!-- LANE: Owner -->
<mxCell id="example-lane-owner" value="Owner" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#dae8fc;strokeColor=#6c8ebf;fontStyle=1;" vertex="1" parent="example-pool">
    <mxGeometry x="30" width="570" height="100" as="geometry"/>
</mxCell>

<!-- LANE: AI -->
<mxCell id="example-lane-ai" value="AI" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#ffe6cc;strokeColor=#d79b00;fontStyle=1;" vertex="1" parent="example-pool">
    <mxGeometry x="30" y="100" width="570" height="100" as="geometry"/>
</mxCell>

<!-- STEP 1: In Owner lane -->
<mxCell id="example-step-1" value="First Step" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#666666;fontSize=10;" vertex="1" parent="example-lane-owner">
    <mxGeometry x="100" y="25" width="100" height="50" as="geometry"/>
</mxCell>

<!-- STEP 2: In AI lane (handoff) -->
<mxCell id="example-step-2" value="Second Step" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#666666;fontSize=10;" vertex="1" parent="example-lane-ai">
    <mxGeometry x="250" y="25" width="100" height="50" as="geometry"/>
</mxCell>

<!-- STEP 3: Back in Owner lane -->
<mxCell id="example-step-3" value="Third Step" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#666666;fontSize=10;" vertex="1" parent="example-lane-owner">
    <mxGeometry x="400" y="25" width="100" height="50" as="geometry"/>
</mxCell>

<!-- ARROW 1: Step 1 → Step 2 (CROSS-LANE: Owner → AI) -->
<mxCell id="example-arrow-1" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;strokeColor=#666666;strokeWidth=2;" edge="1" parent="example-pool" source="example-step-1" target="example-step-2">
    <mxGeometry relative="1" as="geometry"/>
</mxCell>

<!-- ARROW 2: Step 2 → Step 3 (CROSS-LANE: AI → Owner) -->
<mxCell id="example-arrow-2" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;strokeColor=#666666;strokeWidth=2;" edge="1" parent="example-pool" source="example-step-2" target="example-step-3">
    <mxGeometry relative="1" as="geometry"/>
</mxCell>
```

**Key observations:**
- Steps parent to their lane (`parent="example-lane-owner"`)
- **Cross-lane arrows parent to pool** (`parent="example-pool"`)
- Same-lane arrows can use `parent="1"` (root)
- X positions: 100 → 250 → 400 (increments of 150)

---

## How to Use Templates Below

1. **Match template** to user's process type
2. **Present as inference** (ASCII diagram)
3. **Customize lanes and steps** based on user's actual workflow
4. **Generate XML** using the connection pattern above
5. **Apply annotations** after mapping (bottleneck=red, automate=orange)

> **The templates below show CONTENT IDEAS. Apply the CONNECTION RULES above when generating XML.**

---

## Template 1: Content Creation

**Common for:** Coaches, Course Creators, Creators

### Default Lanes

| Lane | Owner | Typical Activities |
|------|-------|-------------------|
| **Strategy** | Owner | Topic ideation, content calendar, trend research |
| **Creation** | Owner/AI | Writing, recording, editing, design |
| **Publishing** | Owner/VA/Tool | Scheduling, posting, cross-platform distribution |
| **Engagement** | Owner/VA | Comments, DMs, community interaction |

### Default Flow

```
START → Topic Research → Content Brief → Draft/Record → Edit → Review → Schedule → Publish → Engage → END
```

### Common Swimlane Structure

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│ CONTENT CREATION                                                                 │
├──────────┬──────────────────────────────────────────────────────────────────────┤
│ Owner    │ [Research] → [Brief] → [Draft] → [Review] ─────────→ [Engage]       │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ AI/Tool  │              ↗ [AI Draft]    ↗ [AI Edit]                             │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ VA       │                                        → [Schedule] → [Publish]      │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Output   │                                                        [Post Live]   │
└──────────┴──────────────────────────────────────────────────────────────────────┘
```

### Typical Bottlenecks (Red)
- Topic research taking too long
- Editing bottleneck
- Owner doing all scheduling

### Typical AI Opportunities (Orange)
- AI draft generation
- AI editing/polish
- Automated scheduling
- Repurposing to other formats

### XML Template

```xml
<mxCell id="cc-pool" value="Content Creation" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=30;fillColor=#f5f5f5;strokeColor=#666666;fontStyle=1;fontSize=14;" vertex="1" parent="1">
    <mxGeometry x="40" y="40" width="900" height="400" as="geometry"/>
</mxCell>

<!-- Owner Lane -->
<mxCell id="cc-lane-owner" value="Owner" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#dae8fc;strokeColor=#6c8ebf;fontStyle=1;" vertex="1" parent="cc-pool">
    <mxGeometry x="30" width="870" height="100" as="geometry"/>
</mxCell>

<!-- AI/Tool Lane -->
<mxCell id="cc-lane-ai" value="AI / Tool" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#ffe6cc;strokeColor=#d79b00;fontStyle=1;" vertex="1" parent="cc-pool">
    <mxGeometry x="30" y="100" width="870" height="100" as="geometry"/>
</mxCell>

<!-- VA Lane -->
<mxCell id="cc-lane-va" value="VA" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#e1d5e7;strokeColor=#9673a6;fontStyle=1;" vertex="1" parent="cc-pool">
    <mxGeometry x="30" y="200" width="870" height="100" as="geometry"/>
</mxCell>

<!-- Output Lane -->
<mxCell id="cc-lane-output" value="Output" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#d5e8d4;strokeColor=#82b366;fontStyle=1;" vertex="1" parent="cc-pool">
    <mxGeometry x="30" y="300" width="870" height="100" as="geometry"/>
</mxCell>
```

---

## Template 2: Sales Process

**Common for:** Coaches, Agencies, Service Providers

### Default Lanes

| Lane | Owner | Typical Activities |
|------|-------|-------------------|
| **Lead Handling** | Owner/VA | Lead capture, qualification, booking |
| **Sales Calls** | Owner | Discovery, pitch, objection handling |
| **Follow-up** | Owner/VA/Tool | Proposals, reminders, closing |
| **Admin** | VA/Tool | Contracts, payments, CRM updates |

### Default Flow

```
Lead In → Qualify → Book Call → Discovery Call → <Decision> → Proposal → Follow-up → Close → Onboard
```

### Common Swimlane Structure

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│ SALES PROCESS                                                                    │
├──────────┬──────────────────────────────────────────────────────────────────────┤
│ Lead     │ [Capture] → [Qualify] ──────────────────────────────────────────→    │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Owner    │            ↗ [Book Call] → [Discovery] → <Fit?> → [Close]           │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ VA/Tool  │                                    ↗ [Proposal] → [Follow-up]        │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Output   │                                                    → [Contract]      │
└──────────┴──────────────────────────────────────────────────────────────────────┘
```

### Typical Bottlenecks (Red)
- Discovery calls eating all time
- Proposal creation manual and slow
- Follow-up slipping through cracks

### Typical AI Opportunities (Orange)
- Lead qualification scoring
- Proposal generation
- Automated follow-up sequences
- Calendar booking automation

### XML Template

```xml
<mxCell id="sp-pool" value="Sales Process" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=30;fillColor=#f5f5f5;strokeColor=#666666;fontStyle=1;fontSize=14;" vertex="1" parent="1">
    <mxGeometry x="40" y="40" width="900" height="400" as="geometry"/>
</mxCell>

<!-- Lead Lane -->
<mxCell id="sp-lane-lead" value="Lead" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#d5e8d4;strokeColor=#82b366;fontStyle=1;" vertex="1" parent="sp-pool">
    <mxGeometry x="30" width="870" height="100" as="geometry"/>
</mxCell>

<!-- Owner Lane -->
<mxCell id="sp-lane-owner" value="Owner" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#dae8fc;strokeColor=#6c8ebf;fontStyle=1;" vertex="1" parent="sp-pool">
    <mxGeometry x="30" y="100" width="870" height="100" as="geometry"/>
</mxCell>

<!-- VA/Tool Lane -->
<mxCell id="sp-lane-va" value="VA / Tool" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#e1d5e7;strokeColor=#9673a6;fontStyle=1;" vertex="1" parent="sp-pool">
    <mxGeometry x="30" y="200" width="870" height="100" as="geometry"/>
</mxCell>

<!-- Output Lane -->
<mxCell id="sp-lane-output" value="Output" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#f8cecc;strokeColor=#b85450;fontStyle=1;" vertex="1" parent="sp-pool">
    <mxGeometry x="30" y="300" width="870" height="100" as="geometry"/>
</mxCell>
```

---

## Template 3: Client Onboarding

**Common for:** All service-based businesses

### Default Lanes

| Lane | Owner | Typical Activities |
|------|-------|-------------------|
| **Client** | Client | Forms, access setup, orientation |
| **Owner** | Owner | Kickoff call, goals setting, relationship building |
| **System** | Tool/VA | Welcome emails, access provisioning, setup |
| **Delivery** | Owner/Team | First deliverable, quick win |

### Default Flow

```
Payment → Welcome → Intake Form → Access Setup → Kickoff Call → First Session/Deliverable → Check-in
```

### Common Swimlane Structure

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│ CLIENT ONBOARDING                                                                │
├──────────┬──────────────────────────────────────────────────────────────────────┤
│ Client   │ [Payment] → [Intake Form] ──────────────→ [First Session] → [Win!]  │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ System   │          ↗ [Welcome Email] → [Access Setup] → [Reminders]           │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Owner    │                           ↗ [Kickoff Call] → [Goals Set]            │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Output   │                                              → [Client Ready]        │
└──────────┴──────────────────────────────────────────────────────────────────────┘
```

### Typical Bottlenecks (Red)
- Manual intake form review
- Access setup inconsistent
- Kickoff calls not scheduled quickly

### Typical AI Opportunities (Orange)
- Automated welcome sequence
- Self-service access provisioning
- Intake form processing
- Scheduling automation

### Digital Assets Needed (Purple)
- Welcome email template
- Intake form
- Onboarding checklist
- Getting started guide

### XML Template

```xml
<mxCell id="co-pool" value="Client Onboarding" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=30;fillColor=#f5f5f5;strokeColor=#666666;fontStyle=1;fontSize=14;" vertex="1" parent="1">
    <mxGeometry x="40" y="40" width="900" height="400" as="geometry"/>
</mxCell>

<!-- Client Lane -->
<mxCell id="co-lane-client" value="Client" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#d5e8d4;strokeColor=#82b366;fontStyle=1;" vertex="1" parent="co-pool">
    <mxGeometry x="30" width="870" height="100" as="geometry"/>
</mxCell>

<!-- System Lane -->
<mxCell id="co-lane-system" value="System" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#ffe6cc;strokeColor=#d79b00;fontStyle=1;" vertex="1" parent="co-pool">
    <mxGeometry x="30" y="100" width="870" height="100" as="geometry"/>
</mxCell>

<!-- Owner Lane -->
<mxCell id="co-lane-owner" value="Owner" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#dae8fc;strokeColor=#6c8ebf;fontStyle=1;" vertex="1" parent="co-pool">
    <mxGeometry x="30" y="200" width="870" height="100" as="geometry"/>
</mxCell>

<!-- Output Lane -->
<mxCell id="co-lane-output" value="Output" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#f8cecc;strokeColor=#b85450;fontStyle=1;" vertex="1" parent="co-pool">
    <mxGeometry x="30" y="300" width="870" height="100" as="geometry"/>
</mxCell>
```

---

## Template 4: Fulfillment / Delivery

**Common for:** Coaches, Course Creators, Agencies

### Default Lanes

| Lane | Owner | Typical Activities |
|------|-------|-------------------|
| **Client** | Client | Engagement, feedback, completion |
| **Owner** | Owner | Core delivery, coaching, strategy |
| **Team/VA** | Team | Support, scheduling, admin |
| **System** | Tool | Automation, content delivery, tracking |

### Default Flow

```
Kickoff → Delivery Cycle [Prep → Execute → Review → Iterate] → Completion → Results Capture → Offboard
```

### Common Swimlane Structure

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│ FULFILLMENT / DELIVERY                                                           │
├──────────┬──────────────────────────────────────────────────────────────────────┤
│ Client   │ [Engage] ────────────────→ [Complete Tasks] → [Give Feedback]        │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Owner    │ [Prep] → [Deliver] → [Review] ──────────────→ [Capture Results]     │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Team/VA  │        ↗ [Support] → [Schedule] → [Admin]                            │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ System   │ [Content Delivery] → [Progress Track] ─────→ [Completion Cert]       │
└──────────┴──────────────────────────────────────────────────────────────────────┘
```

### Typical Bottlenecks (Red)
- Client not engaging
- Prep work time-consuming
- Results not being captured

### Typical AI Opportunities (Orange)
- Automated content delivery
- Progress tracking
- Check-in reminders
- Results documentation

### XML Template

```xml
<mxCell id="fd-pool" value="Fulfillment / Delivery" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=30;fillColor=#f5f5f5;strokeColor=#666666;fontStyle=1;fontSize=14;" vertex="1" parent="1">
    <mxGeometry x="40" y="40" width="900" height="400" as="geometry"/>
</mxCell>

<!-- Client Lane -->
<mxCell id="fd-lane-client" value="Client" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#d5e8d4;strokeColor=#82b366;fontStyle=1;" vertex="1" parent="fd-pool">
    <mxGeometry x="30" width="870" height="100" as="geometry"/>
</mxCell>

<!-- Owner Lane -->
<mxCell id="fd-lane-owner" value="Owner" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#dae8fc;strokeColor=#6c8ebf;fontStyle=1;" vertex="1" parent="fd-pool">
    <mxGeometry x="30" y="100" width="870" height="100" as="geometry"/>
</mxCell>

<!-- Team/VA Lane -->
<mxCell id="fd-lane-team" value="Team / VA" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#e1d5e7;strokeColor=#9673a6;fontStyle=1;" vertex="1" parent="fd-pool">
    <mxGeometry x="30" y="200" width="870" height="100" as="geometry"/>
</mxCell>

<!-- System Lane -->
<mxCell id="fd-lane-system" value="System" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=80;fillColor=#ffe6cc;strokeColor=#d79b00;fontStyle=1;" vertex="1" parent="fd-pool">
    <mxGeometry x="30" y="300" width="870" height="100" as="geometry"/>
</mxCell>
```

---

## Template 5: Admin / Operations

**Common for:** All businesses (often hidden but causing pain)

### Default Lanes

| Lane | Owner | Typical Activities |
|------|-------|-------------------|
| **Finance** | Owner/VA | Invoicing, bookkeeping, payments |
| **Client Mgmt** | Owner/VA | CRM, communication, scheduling |
| **Tools/Systems** | Owner/Tool | Software management, integrations |
| **Planning** | Owner | Calendar, priorities, strategy |

### Default Flow

```
Daily Check-in → Task Triage → Execute Tasks → Update Systems → End-of-day Review
```

### Common Swimlane Structure

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│ ADMIN / OPERATIONS                                                               │
├──────────┬──────────────────────────────────────────────────────────────────────┤
│ Finance  │ [Invoices] → [Payments] → [Bookkeeping] → [Reports]                  │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Client   │ [CRM Update] → [Communications] → [Scheduling]                       │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Systems  │ [Tool Admin] → [Integrations] → [Backups]                            │
├──────────┼──────────────────────────────────────────────────────────────────────┤
│ Owner    │ [Priority Setting] ───────────────────→ [Week Review]                │
└──────────┴──────────────────────────────────────────────────────────────────────┘
```

### Typical Bottlenecks (Red)
- Owner doing all admin
- Manual invoicing
- Too many tools, no integration

### Typical AI Opportunities (Orange)
- Automated invoicing
- CRM auto-updates
- Scheduling automation
- Tool integration (Zapier, Make)

---

## Quick Reference: Lane Colors

| Lane Type | Fill | Stroke | Use For |
|-----------|------|--------|---------|
| Owner | `#dae8fc` | `#6c8ebf` | Business owner actions |
| AI/Tool | `#ffe6cc` | `#d79b00` | Automated or AI-assisted |
| VA/Team | `#e1d5e7` | `#9673a6` | Delegated to humans |
| Client | `#d5e8d4` | `#82b366` | Client/customer actions |
| System | `#ffe6cc` | `#d79b00` | Tool/platform actions |
| Output | `#f8cecc` | `#b85450` | Results/deliverables |

---

## Step Shape Reference

| Shape | Style | Use For |
|-------|-------|---------|
| Rounded Rectangle | `rounded=1` | Normal process steps |
| Diamond | `rhombus` | Decision points |
| Ellipse | `ellipse` | Start/End points |
| Rectangle | `rounded=0` | Data/Documents |

---

## Using Templates in expand-process.md

When user describes their process:

1. **Match to template** - Which template is closest?
2. **Present as inference:**
   > "Based on what you described, your [Process Name] probably looks something like this:
   > [Show ASCII diagram from template]
   > Is this roughly right, or should we adjust?"
3. **Adjust based on feedback** - Add/remove steps, change lane assignments
4. **Generate XML** - Use template structure with customized content
5. **Apply annotations** - Mark bottlenecks (red) and opportunities (orange) after mapping

