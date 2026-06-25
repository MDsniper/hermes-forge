# Business X-Ray

Source: business-x-ray/references/implementation-types.md
MIME: text/markdown

# Implementation Types Reference

**Classification patterns for routing X-Ray opportunities to the right build type.**

---

## How to Use

When classifying a Roadmap opportunity, match it against these patterns. Each type has signal words, typical examples, and where it routes for building.

---

## Type 1: AI Employee (→ meta-create-skill)

**What it is:** A Claude skill that handles a repeatable task. Takes structured input, produces consistent output. The user "hires" Claude for this job.

**Signal words:**
- "I do this the same way every time"
- "It's mostly writing/drafting/research"
- "I spend X hours on this weekly"
- "Template-based but needs customization"
- "Could be better with AI"

**Matches when:**
- Task is repeatable with predictable input/output
- Output is text-based (drafts, emails, proposals, reports, summaries)
- Human review is the quality gate (AI drafts, human approves)
- Task currently takes 1+ hours/week

**Common AI Employees:**

| AI Employee | Input | Output | Typical Savings |
|-------------|-------|--------|-----------------|
| Content Drafter | Topic + angle | First draft + headlines | 2-4 hrs/week |
| Proposal Generator | Client info + scope | Draft proposal + pricing | 1-2 hrs/proposal |
| Call Prep Assistant | Calendar event + CRM notes | Research brief + questions | 30 min/call |
| Email Responder | Inbound email + context | Draft reply | 1-2 hrs/week |
| Content Repurposer | Long-form content | Social posts + newsletter | 2-3 hrs/piece |
| Meeting Summarizer | Transcript | Action items + summary | 30 min/meeting |
| Client Onboarding | Client info | Welcome sequence + setup docs | 1 hr/client |
| Research Assistant | Topic + questions | Research brief + sources | 1-3 hrs/project |

**Routes to:** `meta-create-skill` with handoff YAML

**Build effort:** 1-3 hours (skill creation + testing)

---

## Type 2: Integration (→ meta-create-mcp or Zapier guide)

**What it is:** Connecting two tools that don't currently talk to each other. Eliminates manual copy-paste between systems.

**Signal words:**
- "I copy-paste between X and Y"
- "I have to manually update both systems"
- "When something happens in X, I go update Y"
- "Data doesn't flow between these"

**Matches when:**
- Two tools need to share data
- There's a manual bridge between systems (identified in Connection Map)
- A trigger in one tool should cause an action in another
- Data is being re-entered in multiple places

**Common Integrations:**

| Integration | Trigger | Action | Method |
|-------------|---------|--------|--------|
| YouTube → ConvertKit | New subscriber/comment | Tag in email list | Zapier |
| Stripe → Notion | Payment received | Create client record | Zapier |
| Calendly → CRM | Meeting booked | Update contact record | Zapier/Native |
| Form → Notion | Form submitted | Create database entry | Zapier/Native |
| CRM → Email | Status change | Trigger email sequence | Zapier |
| Stripe → Slack | Payment received | Notification | Zapier/Native |
| Calendar → CRM | Meeting completed | Log activity | Zapier |

**Routes to:**
- `meta-create-mcp` — if building a custom MCP server for deep integration
- Zapier setup guide — for standard trigger→action connections
- Native integration guide — if tools support direct connection

**Build effort:** 15-60 minutes (Zapier), 2-4 hours (custom MCP)

**Decision: MCP vs Zapier:**

| Factor | Use MCP | Use Zapier |
|--------|---------|------------|
| Claude needs to interact with the tool | Yes | No |
| Simple trigger → action | No | Yes |
| Multi-step workflow | Depends | Yes |
| Real-time data access | Yes | No |
| User comfort with code | Required | Not required |
| Ongoing maintenance | Manual | Managed |

---

## Type 3: Digital Asset (→ inline build or Notion setup)

**What it is:** Something built once and reused repeatedly — databases, templates, SOPs, checklists, landing pages. The "infrastructure" that skills and integrations plug into.

**Signal words:**
- "I don't have a system for this"
- "I should have a template but I start from scratch"
- "I explain this to every client"
- "There's no central place for this"
- "I keep this in my head"

**Matches when:**
- A data source is missing (no CRM, no content calendar)
- A template would eliminate repeated work
- An SOP would enable delegation
- A landing page or form is needed for a funnel stage

**Common Digital Assets:**

| Asset | Format | Purpose | Effort |
|-------|--------|---------|--------|
| Client CRM | Notion database | Track clients + pipeline | 1-2 hrs |
| Content Calendar | Notion database | Plan + track content | 1 hr |
| Proposal Template | Notion/Google Doc | Standardize proposals | 1-2 hrs |
| Onboarding Checklist | Notion/Checklist | Ensure nothing missed | 30 min |
| SOP Document | Notion page | Document process for delegation | 1-2 hrs |
| Email Sequence | ConvertKit/Email tool | Automated nurture | 2-3 hrs |
| Landing Page | Carrd/Webflow | Capture leads | 1-3 hrs |
| Welcome Kit | PDF/Notion | Client welcome package | 1-2 hrs |
| Intake Form | Tally/Typeform | Collect client info | 30-60 min |

**Routes to:** Inline creation (Claude helps build it in the conversation) or Notion setup

**Build effort:** 30 minutes - 3 hours

**Priority rule:** Digital assets often need to be built FIRST because AI Employees and Integrations depend on them as data sources.

---

## Type 4: Process Change (→ SOP document or workflow redesign)

**What it is:** A new or revised way of doing something. No code, no tools — just a better process. Often the simplest and cheapest fix.

**Signal words:**
- "We don't have a process for this"
- "Everyone does it differently"
- "Steps get skipped"
- "The order is wrong"
- "We should be doing X but we don't"

**Matches when:**
- The problem is workflow order, not tooling
- A checklist would solve 80% of the issue
- The fix is "do step A before step B" or "add step C"
- Delegation is the goal (need documentation first)

**Common Process Changes:**

| Process | Type | Impact |
|---------|------|--------|
| Post-call follow-up | Checklist + email template | Prevents leads going cold |
| Content publishing workflow | Step-by-step SOP | Enables delegation |
| Client handoff | Checklist + template | Smooth transitions |
| Weekly review | Agenda template | Consistent cadence |
| Quality check | Checklist | Fewer errors |

**Routes to:** Inline creation (Claude writes the SOP/checklist/workflow)

**Build effort:** 15-60 minutes

---

## Classification Decision Tree

Use this when an opportunity could fit multiple types:

```
Is the core problem "I need a tool/system I don't have"?
├── YES → Is it a data store or template?
│         ├── YES → DIGITAL ASSET
│         └── NO → Is it connecting two existing tools?
│                   ├── YES → INTEGRATION
│                   └── NO → AI EMPLOYEE (if text/analysis task)
│
└── NO → Is the core problem "the process itself is wrong"?
          ├── YES → PROCESS CHANGE
          └── NO → Is it "this takes too long / too manual"?
                    ├── YES → Is it text-based output?
                    │         ├── YES → AI EMPLOYEE
                    │         └── NO → Is it data movement?
                    │                   ├── YES → INTEGRATION
                    │                   └── NO → PROCESS CHANGE (simplify)
                    └── NO → Re-evaluate (may not need a build)
```

---

## Dependency Patterns

When ordering builds, respect these dependency chains:

```
TYPICAL BUILD ORDER:

1. Digital Assets (data sources, templates)
   ↓ feeds into
2. Integrations (connect the data sources)
   ↓ enables
3. AI Employees (use the data + integrations)
   ↓ documented by
4. Process Changes (SOPs for using the new systems)
```

**Common dependency chains:**

| Build | Depends On |
|-------|-----------|
| CRM automation skill | CRM database (digital asset) |
| Proposal generator skill | Proposal template (digital asset) + CRM data |
| Auto-onboarding integration | Onboarding checklist (digital asset) + payment trigger |
| Content repurposer skill | Content calendar (digital asset) |
| Follow-up email integration | Email sequence (digital asset) + CRM trigger |

**Rule:** If a build's dependency doesn't exist yet, schedule the dependency in the same week or the week before.

---

## Scoring Adjustments for Implementation Types

When scoring priorities in the Build Plan, adjust based on type:

| Type | Effort Bias | Impact Bias | Notes |
|------|-------------|-------------|-------|
| Digital Asset | +1 effort (usually easy) | Neutral | Often a prerequisite — build early |
| Integration | +1 effort (Zapier is fast) | +1 if eliminates manual bridge | Quick wins |
| AI Employee | Neutral | +1 if saves 2+ hrs/week | Highest long-term ROI |
| Process Change | +1 effort (just documentation) | Neutral | Cheapest fix, do alongside others |

---

## Framing Guide

Use CLO-OS language when presenting:

| Technical Term | CLO-OS Language |
|---------------|-----------------|
| Claude skill | **AI Employee** |
| MCP server | **Integration** or **Connection** |
| Notion database | **Digital Asset** or **System** |
| SOP | **Playbook** or **Process** |
| Zapier workflow | **Automation** or **Bridge** |
| API connection | **Integration** |
| Template | **Blueprint** or **Template** |

> "You're not just fixing bottlenecks — you're hiring AI Employees, building Digital Assets, and connecting your systems. This is how a Chief Leverage Officer operates."
