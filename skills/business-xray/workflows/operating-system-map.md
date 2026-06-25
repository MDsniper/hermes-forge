# Business X-Ray

Source: business-x-ray/workflows/operating-system-map.md
MIME: text/markdown

# Operating System Map Workflow

**Redraw the whole business as connected Skill Systems — the future-state payoff page.**

The owner walks away with one picture of how the work gets done *without them*: each stage of the business as a **Skill System** (an AI Employee you build), the **Skills** it runs, the **Tools/MCPs** it plugs into, the **Digital Assets** it runs on, the **Digital Assets it hands to the next stage**, and an **ordered list of the Skill Systems to build first** — sequenced by what the owner told you matters most.

> **Skill System = AI Employee** — same thing, two names. On a build blueprint like this, use **Skill System** (it reads as a thing you build, not a hire). "AI Employee" stays as the vision metaphor in the title.

> **This works for ANY business.** Flex the *content*; keep the *structure*. Never tell the user the map was "designed for an agency" or any archetype — just build theirs.

---

## This is a SYNTHESIS of the X-Ray — know where each layer comes from

The OS Map is the **capstone**. Almost everything it shows was already collected during the X-Ray. Your job is mostly to *re-shape existing data*, then ask three small probes + run MCP discovery.

| Map element | Input it needs | X-Ray source | If missing → ask |
|---|---|---|---|
| **Skill Systems** (stages) | the value chain | Business Map / archetype | "What are your 3-5 core stages?" |
| **Skills** (jobs per stage) | the recurring jobs | process swimlanes (the activities) | "What repeats every week in [stage]?" |
| **Tools / MCPs** | tool stack *per stage* | Tool Inventory / System Connection Map | explicit per-stage tool question (Step 3) |
| **MCP tier** ✅/🔶/⚪ | does an MCP exist | — *(new)* | MCP discovery (Step 4) |
| **Digital Assets** (in-card + status) | documented knowledge + maturity | **24 Assets Assessment** (Green/Yellow/Red) | "What docs/templates does [stage] use? which exist?" |
| **Digital Asset passed** (handoff) | the deliverable each stage hands on | Bow-Tie funnel / process outputs | "What does [stage] hand to [next]?" |
| **Loop-back** | retention/referral exists | Bow-Tie (Results → referral) | infer; confirm if unclear |
| **Build-first ORDER** | user's #1 priority + bottleneck + impact/effort/dependency + readiness | roadmap scoring + pain signals + the goal | the **priority-anchor** question (Step 5) |

**Three new probes only:** per-stage tools (Step 3), the handoff deliverable (Step 2), the priority anchor (Step 5). Everything else is inference-first from data you already have.

---

## Prerequisites (and what each unlocks)

**Best result — a fairly complete X-Ray:**
- Business Map → the **Skill Systems** (stages)
- 2+ process swimlanes → the **Skills**
- Tool Inventory / System Connection Map → the **Tools**
- 24 Assets Assessment → the in-card **Digital Assets** (+ Green/Yellow/Red maturity)
- Bow-Tie → the **handoffs** and the **loop-back**
- Roadmap (or pain signals) → the **build-first ordering**

**Minimum:** Business Map + one mapped process. Thinner inputs = a sparser map; gather the gaps with the fallback probes above, and tell the user the map gets richer as the X-Ray deepens. **If the 24 Assets Assessment hasn't run, do it first** (`workflows/digital-assets-assessment.md`) — it's what fills the Digital Assets layer with real maturity status.

---

## Entry Point

After the System Connection Map / 24 Assets, or when the user says:
*"operating system map", "show my AI employees", "map my skill systems", "what would my business look like with AI", "future state map", "AI org chart".*

Offer it as the capstone:
> "Now I can draw the destination — your whole business as connected **Skill Systems**: each stage as an AI worker you build, the skills it runs, the tools it plugs into, the digital assets it runs on, and what it hands to the next stage. It ends with the exact order to build them in. Want me to put it together?"

---

## Execution Instructions

### Step 1: Confirm the Skill Systems (stages)

From the Business Map, propose one **Skill System per value-chain stage.** Default to the 4 systems — Marketing, Sales, Delivery, Operations — renamed to what the business actually calls them. Give each a plain persona name (a role, or the real person who owns it).

> "I'll draw your business as a line of **Skill Systems** — the AI workers you'd build, one per stage:
> - **① Marketing → 'Maya'** — content & lead gen
> - **② Sales → 'Sam'** — qualifying & closing
> - **③ Delivery → 'Dev'** — onboarding & fulfillment
> - **④ Operations → 'Ona'** — admin, reporting, money
>
> Match how you'd split it? Rename, merge, or add one?"

STOP. Wait. Adjust (3-5 stages). Number them in flow order ①→④ — that's the pipeline.

### Step 2: Per Skill System — confirm Skills + Digital Assets + the Handoff (inference-first)

For EACH stage, draft all three from existing X-Ray data and confirm in one beat. This is where the swimlanes (→ Skills), the 24 Assets (→ Digital Assets + status), and the Bow-Tie (→ handoff) get re-shaped.

Go ONE stage at a time:
> "**② Sales — Sam.** From what we mapped:
> - **Skills (jobs):** qualify-application · prep-call · follow-up
> - **Digital Assets it runs on:** Offer Doc ✅ · Call Script ✅ · Objection FAQ ⚠️ *(to build)*
> - **Hands to Delivery:** a Signed Client + Intake/Goals doc
>
> Right? Anything to add, cut, or rename?"

STOP. Wait. Repeat per stage.

**Rules:**
- **Skills** = 3-5 recurring jobs, plain verb-led names (`qualify-application`). Distill swimlane activities into named jobs; if a stage's swimlane wasn't mapped, probe: "What does [stage] do that repeats every week?"
- **Digital Assets (in-card)** = the knowledge it *runs on* (SOP, template, FAQ, framework). Pull from the 24 Assets Assessment and mark each **✅ exists** or **⚠️ to build** (from its Green/Yellow/Red score). An asset with no skill is dead weight; a skill with no asset can't run — show both honestly.
- **Handoff** = the ONE key Digital Asset/deliverable this stage produces and passes to the next (Qualified Lead List → Signed Client → Results Report). This is the output that sits *between* the cards.

### Step 3: Tools & platforms per stage (the explicit ask)

Confirm the **tools/platforms** each Skill System plugs into. Start from the Tool Inventory, then ask directly for gaps — one stage at a time.
> "For **Sam (Sales)** I have **Calendly, Notion, Zoom**. Anything else sales runs on — proposals, payment, e-sign?"

STOP. Wait. Keep each stage to its 3-5 most-used tools (note extras; don't crowd the page).

### Step 4: MCP discovery (resolve each tool's tier)

For every distinct tool, set its **MCP tier** from `references/mcp-directory.md` (curated), falling back to a live search (`"<tool> MCP server"` → if none, `"<tool> Zapier integration"` / API). Batch the unknowns, cache within the session, report all at once:
> "Which of your tools an AI can operate directly:
> ✅ **Native MCP:** Notion, Stripe, YouTube
> 🔶 **Via Zapier/API:** Calendly, Kit, Zoom
> ⚪ **No connector yet:** Canva — manual today, or we build a small one.
> The ⚪ ones become 'build a connector' items. Look right?"

STOP. Wait.

> **Don't guess MCP status.** Unverified → search, or mark ⚪. A wrong ✅ sends them down a dead end.

### Step 5: The priority anchor (this orders the build list)

Capture the ONE input that orders "Skill Systems to build first." Combine the bottleneck the X-Ray already surfaced with a direct goal question:
> "Last thing before I draw it. Of these four, **which one running itself would change your week the most?** And is that the same place that eats your time today, or a different one?"

STOP. Wait. Note their pick (= Slot 1) and the bottleneck. If they named a dream/why earlier (freedom, time back), keep it — it sharpens the framing.

### Step 6: Compute the build-first order (the algorithm)

Order the bottom row **left → right = build order**, anchored to Step 5. Reuse the X-Ray roadmap's Impact + Effort + Dependency scores if they exist; otherwise score quickly (1-3 each).

```
SLOT 1 — THE USER'S #1.
  The Skill System that relieves their named bottleneck / "fix one thing" answer.
  → If it needs a Digital Asset still marked ⚠️ to-build, SLOT 1 becomes "Build [that asset]"
    (asset-before-system rule), and the Skill System takes SLOT 2.

SLOTS 2-3 — QUICK WINS.  Rank the rest by:
  score = Impact (hrs saved / revenue)  ×  Readiness  ÷  Effort
  Readiness ↑ when the Digital Asset already exists (✅) AND its tools are ✅ native-MCP.
  (Ready + high-impact + low-effort floats to the top.)

SLOT 4 — DEPENDENCY UNLOCKER.
  The shared asset/system that makes others easier once built (e.g. the CRM/data layer everyone reads from).

SLOT 5 — ⚪ CONNECTOR BUILD.
  The highest-leverage ⚪ tool on a critical path → "build a custom MCP."
```

Cap at 3-5 cards. **Tag each card** so the order is legible:
**⚡ quick win (assets ready)** · **🧱 needs asset first** · **🔗 unlocks others** · **⚪ build connector**.

### Step 7: Checkpoint — full map in text before rendering

> "Here's your Operating System Map:
> **Skill Systems:** Maya · Sam · Dev · Ona
> **Tools:** [X] — [a] ✅ · [b] 🔶 · [c] ⚪
> **Flows:** Qualified Lead → Signed Client → Results → (renewal loops back)
> **Build first (in order):** 1) [#1] 2) [quick win] 3) [quick win] 4) [unlocker] 5) [connector]
> Ready to draw it?"

STOP. Wait.

### Step 8: Generate the diagram

1. Read `references/operating-system-map-template.md` for layout patterns.
2. Generate the **Operating System Map** as an HTML section in the report:
   - **Horizontal legend strip** at top: Skill System / Skill / Tool (tier-colored) / Digital Asset / Handoff.
   - **One card per Skill System**, numbered: blue header → SKILLS zone (blue) → TOOLS zone (tier-colored) → DIGITAL ASSETS zone (purple, status-colored).
   - **Handoff shelves BETWEEN cards** (amber): the purple Digital Asset(s) passed forward, with bold arrows.
   - **Loop-back arrow** (dashed amber) from the last stage to the first: "renewal & referral fuels new leads."
   - **"SKILL SYSTEMS TO BUILD FIRST"** row at the bottom — cards in build order.
3. **Append the section to the report HTML** at `~/hermes-xray-reports/reports/[business-name]-xray-[date].html`.
4. Tell the user: "Operating System Map added to your report."

### Step 8b: Build the file system on disk (automatic — no second interview)

The map IS the picture `business-os` needs, so once the Operating System Map exists, **make it real on disk automatically** — do NOT run a second round of setup questions. Tell the user plainly, then build:

> "Now I'll set up the file structure your business runs on, straight from this map — a folder for each area plus a BUSINESS-MAP.md so any AI you add can navigate it without searching. Setting it up now."

Invoke the `business-os` skill (its `scaffold-departments` flow) and **hand it this map** so it skips its own interview:
- **Skill Systems / stages → departments** (renamed as the map names them; flex the set to the business).
- **The flow + handoffs → the BUSINESS-MAP.md pipeline** (each stage → its folder + the skill that runs it, "none yet" until built, + the metric).
- **Per-stage tools + digital assets → each department's CLAUDE.md index.**

`business-os` scaffolds the folders + BUSINESS-MAP.md from this with no re-interview. **File migration stays gated:** if the workspace already has scattered files, `business-os` shows a move plan and waits for approval before touching anything — never auto-move files. (Only skip the build if the user explicitly says "not yet / don't set up files." Default, once the map exists, is to build it.)

### Step 9: Hand off to building

> "This is the destination, in build order. When you're ready, the **Implementation Router** turns the #1 Skill System into a real skill — and for the ⚪ tools it scaffolds a custom MCP.
> A) **Build #1 now** → Implementation Router
> B) **Update the Roadmap** with this build order
> C) **Stop here** — take the map + resume block"

STOP. Wait.
- **A)** → `workflows/implementation-router.md` (routes to `meta-create-skill` / `meta-create-mcp`)
- **B)** → `workflows/generate-roadmap.md`
- **C)** → Output report HTML + resume block

---

## Genericity Guardrails

- **Adapt to the business.** Stage names, personas, skills, tools, assets all flex. The structure (Skill System → Skills → Tools → Digital Assets, assets passed between, ordered build row) stays fixed; the content changes.
- **Never expose the framing.** Don't say it's "based on an agency example," don't ask the user to reinterpret terms, don't imply the template limits their business.
- **Custom / made-to-order businesses:** the scoping/quoting conversation is **Sales**, not Delivery.
- **Solo operators:** Skill Systems are *jobs you build*, not headcount.
- **Don't fabricate.** No tool that wasn't named; no ✅ that wasn't verified; mark unbuilt assets ⚠️ honestly.

---

## Resume Block Additions

```yaml
# Operating System Map
operating_system_map_complete: [true/false]
skill_systems:
  - stage: [name]            # e.g. Marketing
    persona: [name]          # e.g. Maya
    skills: [list]
    tools: [list]
    digital_assets:          # in-card (knowledge it runs on)
      - {name: ..., status: exists|to_build}
    passes_to_next: [the handoff Digital Asset]
tool_mcp_status:
  native: [✅ tools]
  via_bridge: [🔶 tools]
  no_mcp: [⚪ tools]
priority_anchor: [the user's #1 + bottleneck]
build_first_order:           # ordered, tagged
  - {item: ..., tag: quick_win|needs_asset|unlocks|connector}
```

---

## Cross-Platform Mode

- **Hermes / Hermes Forge:** append the section to `~/hermes-xray-reports/reports/[business-name]-xray-[date].html`.
- **Claude Web / ChatGPT / Gemini:** output the HTML for copy-paste; include the resume block.
