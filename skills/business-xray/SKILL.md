---
name: business-xray
description: "Map, diagnose, and optimize business operations through progressive visual analysis. Creates Business Maps, Bow-Tie Funnels, Process Swimlanes with 3-level drill-down, a System Connection Map, and a future-state Operating System Map that redraws the business as connected AI Employees. USE WHEN user says 'business x-ray', 'map my business', 'identify bottlenecks', 'process improvement', 'visualize my business', 'find automation opportunities', 'what should I automate', 'map my operations'."
---

# Business X-Ray

Map, diagnose, and optimize business operations through progressive visual analysis.

## Core Principles

1. **Inference-first** -- Guess more, user confirms more (less typing)
2. **ONE question at a time** -- Never bundle multiple questions
3. **Goals = Performance Goals** -- Actions that drive the funnel
4. **Goals emerge** -- Infer from pain points, don't ask directly
5. **Map first, annotate after** -- Get process right, then flag opportunities
6. **Fix before moving on** -- Actionable output at each checkpoint

## Diagram Generation

Generate all diagram XML inline. Do NOT use subagents for diagrams.

At each checkpoint:
1. Read the relevant reference file for XML patterns
2. Generate the .drawio XML
3. Write to file
4. Confirm to user

| Diagram Type | Reference |
|-------------|-----------|
| Business Map | references/drawio-standards.md |
| Bow-Tie Funnel | references/bowtie-funnel.md |
| Process Swimlane | references/swimlane-templates.md |
| System Connection Map | references/system-connection-template.md |
| Operating System Map | references/operating-system-map-template.md |
| 24 Assets Scorecard | references/scorecard-template.md |

---

## Workflow Routing

### Start New X-Ray -> `workflows/progressive-interview.md`

**When:** User says "business x-ray", "map my business", "let's do an x-ray"
**Output:** Business Map + Bow-Tie Funnel (.drawio)

### Expand Process -> `workflows/expand-process.md`

**When:** User says "drill down", "expand this", "show me more detail"
**Output:** Process swimlane with annotations (.drawio page)

### Generate Roadmap -> `workflows/generate-roadmap.md`

**When:** User says "what should I fix", "prioritize", "roadmap"
**Output:** 90-Day Roadmap (.drawio page)

### Map System Connections -> `workflows/system-connection-map.md`

**When:** After process expansion; user says "how do my tools connect", "system map"
**Output:** System Connection Map (.drawio page)

### Map Operating System -> `workflows/operating-system-map.md`

**When:** After System Connection Map; user says "show my AI employees", "future state"
**Output:** Operating System Map (.drawio page)

### 24 Assets Assessment -> `workflows/digital-assets-assessment.md`

**When:** User says "score my assets", "24 assets", "leverage score"
**Output:** 24 Assets Scorecard + Leverage Score

### Implementation Router -> `workflows/implementation-router.md`

**When:** After Roadmap; user says "let's build this", "create a skill for this"
**Output:** Classified opportunity list + handoff to `forge-skill`

### Generate Report -> `workflows/generate-report.md`

**When:** After any x-ray workflow; user says "generate report", "make a report", "export", "push to notion"
**Output:** Polished HTML report + optional Notion page

### Scan Existing Diagram -> `workflows/scan-diagram.md`

**When:** User has an existing .drawio file; "scan my diagram", "read my business map"
**Output:** Reconstructed business state + next steps

---

## Annotation Colors

| Annotation | Border | Color | Meaning |
|------------|--------|-------|---------|
| **Bottleneck** | Solid thick | Red #FF6B6B | Slowing things down |
| **Automate** | Dashed | Orange #FFA500 | AI/tool could do this |
| **High Value** | Solid thick | Green #90EE90 | Human should keep doing |
| **Digital Asset** | Solid | Purple #9370DB | Needs to be built |

---

## Business Archetypes

| Type | Trigger Words | Typical Flow |
|------|---------------|--------------|
| **Coach** | coaching, consulting, clients | YouTube -> Email -> Call -> High-ticket |
| **Course Creator** | course, membership, students | Content -> Lead Magnet -> Webinar -> Course |
| **Agency** | agency, clients, retainer | Referrals -> Proposal -> Retainer |
| **SaaS** | software, app, subscribers, MRR | Content -> Trial -> Subscription |
| **Service Provider** | services, done-for-you | Referrals -> Call -> Proposal -> Retainer |
| **Creator** | content, audience, followers | Platform -> Subscribe -> Products |

Detailed patterns: `read references/business-archetypes.md`

---

## Output Format

Two artifacts per engagement:

**Working file:** Single `.drawio` file with multiple pages (the editable source you keep):

| Page | Content |
|------|---------|
| Business Overview | 7-column Business Map + Bow-Tie Funnel |
| [Area] Page | Main swimlane + sub-processes |
| System Connection Map | Hub-and-spoke network diagram |
| Operating System Map | Future-state AI Employees |
| 24 Assets Scorecard | 24 asset grid + Leverage Score |
| Action Roadmap | DO FIRST / DO NEXT / DO LATER |

**Client deliverable:** Polished HTML report deployed to https://xray.bawai.org/reports/[name]-xray-[date].html (via `workflows/generate-report.md`). Client opens the link in their browser -- no draw.io required.

---

## When to Activate

**Activate when:**
- User wants to visualize their business structure
- User wants to identify operational bottlenecks
- User wants to find automation/delegation opportunities

**Do NOT activate when:**
- User wants to create a specific skill -> route to `forge-skill`
- User wants to fix a skill that misfired -> route to `retrospective`

---

## References

Load on-demand:
- `references/drawio-standards.md` -- XML patterns, colors, styles
- `references/bowtie-funnel.md` -- Bow-tie funnel XML patterns
- `references/business-archetypes.md` -- Pre-built inference patterns
- `references/swimlane-templates.md` -- Common process templates
- `references/opportunity-categories.md` -- Fix options per category
- `references/system-connection-template.md` -- Network diagram patterns
- `references/operating-system-map-template.md` -- AI Employee map patterns
- `references/common-tool-integrations.md` -- Tool connection inference data
- `references/implementation-types.md` -- Classification for implementation routing
- `references/24-assets-framework.md` -- Asset scoring criteria
- `references/scorecard-template.md` -- Scorecard draw.io template
- `references/mcp-directory.md` -- Tool to MCP/automation tier lookup

## Templates

- `templates/report-template.html` -- HTML report template (fill placeholders)
- `templates/sample-report.html` -- Complete sample report (coach business)
