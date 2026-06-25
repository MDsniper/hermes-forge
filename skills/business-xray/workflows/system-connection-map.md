# Business X-Ray

Source: business-x-ray/workflows/system-connection-map.md
MIME: text/markdown

# System Connection Map Workflow

**Synthesize tool connections across all mapped processes into a visual network diagram.**

---

## Purpose

This workflow runs AFTER process swimlanes are mapped (Level 2/3) and BEFORE the Action Roadmap. It synthesizes the Tool Inventory that was passively collected during the interview into a visual map showing how all tools connect across the business.

**Most data is already collected.** This step:
1. Presents the full Tool Inventory to the user
2. Asks targeted questions about UNKNOWN connections only
3. Generates a hub-and-spoke network diagram (HTML section in the report)
4. Feeds integration opportunities into the Roadmap

---

## Prerequisites

**Post-BX-Ray mode (preferred):**
- [ ] Business Map complete
- [ ] At least 2 processes expanded to Level 2/3
- [ ] Tool Inventory maintained during interview (see progressive-interview.md)

**Standalone mode (fallback):**
- No prior BX-Ray data — runs full tool discovery interview instead

---

## Entry Point

This workflow triggers at the Decision Point in `progressive-interview.md` or `expand-process.md` when the user finishes mapping processes:

> "Before we build your roadmap, let me show you something..."

Or when user explicitly says: "how do my tools connect", "system map", "tool connections", "show me how everything connects"

---

## Execution Instructions (Post-BX-Ray Mode)

### Step 1: Present Tool Inventory

Compile the Tool Inventory maintained during the interview. Group by business function:

> "While we mapped your processes, I noticed you use **[X] tools** across your business. Here's the full picture:
>
> **Content & Marketing:** YouTube, Canva, ConvertKit
> **Sales:** Calendly, Zoom, Notion (CRM), Stripe
> **Delivery:** Notion (client portal), Google Drive, Zoom
> **Admin:** Excel, Google Calendar
>
> Am I missing anything? Any tools you use daily that didn't come up?"

STOP. Wait for response.

**Categorization rules:**
- Place each tool in its PRIMARY category (where it's used most)
- Tools used across categories get noted but placed once
- Common categories: Content & Marketing, Sales, Delivery, Admin/Operations
- Adjust categories based on what actually emerged during the interview

### Step 2: Confirm Known Connections

Present connections already captured during Level 3 expansion and connection probes:

> "From our mapping, I already know these connections:
>
> **Automated (tools talk directly):**
> - Calendly → Zoom (auto-generates meeting link)
> - ConvertKit → Stripe (payment triggers email sequence)
>
> **Manual (you handle the handoff):**
> - YouTube → ConvertKit (you add subscribers manually)
> - Notion CRM → Gmail (you write emails based on CRM notes)
>
> Does this match? Any connections I'm missing?"

STOP. Wait for response.

### Step 3: Probe Unknown Connections

For tool pairs where connection status is UNKNOWN, ask ONE question at a time:

> "A few connections I want to confirm:
>
> When someone pays on **Stripe**, does anything automatically happen in **Notion** — like creating a client record? Or do you set that up manually?"

STOP. Wait for response.

**Probing rules:**
- Only ask about connections that SHOULD logically exist based on business flow
- Max 3-4 connection questions total (don't over-interview)
- Use `references/common-tool-integrations.md` to infer what CAN connect
- If a tool pair has no logical reason to connect, skip it

**Priority probing order:**
1. Cross-category connections (Content → Sales handoff tools)
2. Payment → Fulfillment connections (Stripe → onboarding tools)
3. CRM → Communication connections (Notion/HubSpot → Email/Calendar)
4. Any tool appearing in 3+ processes

### Step 4: Identify Disconnected Tools

Flag tools with zero connections:

> "I notice **Excel** and **Dropbox** don't connect to anything else in your system. Excel is used for bookkeeping, and Dropbox for file sharing — but data doesn't flow in or out of either one automatically.
>
> Is that accurate, or am I missing a connection?"

STOP. Wait for response.

### Step 5: Checkpoint — Connection Map Summary

Present the complete connection map as text before generating the diagram:

> "Here's your complete System Connection Map:
>
> **[X] tools** across [Y] categories
> **[A] automated connections** (green — tools talk directly)
> **[B] manual bridges** (orange — you handle the handoff)
> **[C] disconnected tools** (red — isolated, no connections)
>
> **Hub tools** (appear in 3+ areas): [list]
> **Biggest manual burden:** [describe the most impactful manual bridge]
>
> Ready to generate the diagram?"

STOP. Wait for confirmation.

### Step 6: Generate Diagram

Generate the System Connection Map page directly:

1. Read `references/system-connection-template.md` for complete XML patterns
2. Read the references for color standards
3. Generate hub-and-spoke network diagram XML with:
   - **Page name:** System Connection Map | **Page ID:** page-scm
   - **Category zones** for each business function
   - **Tool node styles:**
     - Hub tools (3+ connections): Green thick border (#82b366)
     - Standard tools (1-2): Gray border (#666666)
     - Disconnected tools (0): Red thick border (#FF6B6B)
     - Redundant tools: Orange dashed border (#FFA500)
   - **Connections:**
     - Automated: green solid #82b366, label: 'API'
     - Manual: orange dashed #FFA500, label: 'manual'
     - Broken: red dotted #FF6B6B, label: '???'
   - **Opportunities** as numbered badges
   - Legend, Stats box, Back to Overview link
4. Append the section to the report HTML at `~/hermes-xray-reports/reports/[business-name]-xray-[date].html`
5. Tell the user: "System Connection Map added to your diagram."

### Step 7: Present Opportunities

After diagram is generated, present integration opportunities:

> "Based on your connection map, here are the biggest opportunities:
>
> **Quick Wins (automate manual bridges):**
> 1. **YouTube → ConvertKit:** Zapier integration available — auto-tag new subscribers. [Low effort]
> 2. **Stripe → Notion:** Zapier trigger on payment → create client record automatically. [Low effort]
>
> **Consolidation:**
> 3. **Dropbox → Google Drive:** You already use Google Drive for delivery. Consolidate files there, eliminate Dropbox. [Low effort]
>
> **Missing Connections:**
> 4. **No CRM automation:** Client data lives in Notion but doesn't trigger onboarding automatically. A Zapier workflow could fix this. [Medium effort]
>
> Which of these would save you the most time?"

STOP. Wait for response.

### Step 8: Feed Into Roadmap

Selected opportunities get added to the Action Roadmap alongside process bottlenecks:

> "I'll add these integration opportunities to your Action Roadmap alongside the process improvements we identified earlier.
>
> Now that you can see how your tools connect *today*, I can also draw the **other half** — what your business looks like once **AI Employees** are running it. That's the Operating System Map: each part of your business as an AI Employee, the skills it runs, the tools it plugs into, and which of those an AI can operate directly.
>
> A) **Operating System Map** — See your business as connected AI Employees (the future-state picture)
> B) **24 Assets Assessment** — Score all business assets and calculate your Leverage Score
> C) **Generate Roadmap** — Go straight to your 90-Day Action Plan
> D) **Stop here** — Take what we have"

STOP. Wait for choice.

- **A)** → `workflows/operating-system-map.md`
- **B)** → `workflows/digital-assets-assessment.md`
- **C)** → `workflows/generate-roadmap.md`
- **D)** → Output report HTML + resume block

---

## Execution Instructions (Standalone Mode)

When running without a prior BX-Ray session, the workflow must discover tools from scratch.

### Standalone Step 1: Opening

> "Let's map how your tools and systems connect across your business. I'll go through each area one at a time.
>
> Starting with **content and marketing** — what tools do you use to create, publish, and distribute content?"

STOP. Wait for response.

### Standalone Step 2: Category-by-Category Discovery

Go through each category ONE AT A TIME:

1. **Content & Marketing** → "What tools for content creation and distribution?"
2. **Sales** → "What tools for leads, calls, proposals, payments?"
3. **Delivery** → "What tools for client onboarding, sessions, deliverables?"
4. **Admin** → "What tools for scheduling, bookkeeping, communication?"

After each: STOP. Wait for response. Confirm and probe for missing tools.

### Standalone Step 3: Connection Mapping

Same as Post-BX-Ray Steps 2-4. Go through connections one pair at a time.

### Standalone Step 4: Continue from Step 5

Proceed with Checkpoint, Diagram Generation, Opportunities — same as Post-BX-Ray mode.

**Standalone output:** Single report HTML with just the System Connection Map section (no Business Overview, no swimlanes).

---

## Resume Block Additions

When outputting the resume YAML, include connection map data:

```yaml
# System Connection Map
system_connection_map_complete: [true/false]
tools_identified: [count]
tool_inventory:
  content_marketing: [tool list]
  sales: [tool list]
  delivery: [tool list]
  admin: [tool list]
connections:
  automated: [count]
  manual: [count]
  disconnected_tools: [list]
connection_opportunities: [count]
```

---

## Opportunity Scoring (feeds into Roadmap)

Connection map opportunities use the same priority scoring as process opportunities:

```
Priority Score = Impact (1-3) + Effort (1-3) + Dependency (1-3)

Impact:
  3 = Saves 3+ hours/week or eliminates error-prone manual step
  2 = Saves 1-2 hours/week or simplifies workflow
  1 = Nice-to-have, marginal improvement

Effort:
  3 = Turn-key (enable a setting, install a Zapier template)
  2 = Some setup (configure Zapier, migrate files)
  1 = Significant work (custom scripts, major migration)

Dependency:
  3 = Blocks other improvements (must fix first)
  2 = Enables future improvements
  1 = Independent, standalone fix
```

**High scores (7-9):** Add to DO FIRST in Roadmap
**Medium scores (5-6):** Add to DO NEXT
**Low scores (3-4):** Add to DO LATER

---

## Next Workflow

After System Connection Map is complete:
- **24 Assets Assessment:** → `workflows/digital-assets-assessment.md` (recommended — score all business assets before building roadmap)
- **Generate Roadmap:** → `generate-roadmap.md` (includes both process AND connection opportunities)
- **Implementation Router:** → `workflows/implementation-router.md` (if Roadmap already exists, skip straight to building)
- **Stop here:** Output report HTML + resume block