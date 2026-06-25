# Business X-Ray

Source: business-x-ray/workflows/digital-assets-assessment.md
MIME: text/markdown

# 24 Assets Assessment Workflow

**Score all 24 business assets, calculate the Leverage Score, and generate an actionable upgrade plan.**

---

## Purpose

This workflow scores every asset in the business using Daniel Priestley's 24 Assets framework. It runs as an **integrated phase** of the Business X-Ray — after the Business Map, Bow-Tie, and Swimlanes have been mapped. Claude has already been silently accumulating asset signals throughout the interview. Now it's time to formally score them.

It produces:
1. A color-coded 24 Assets Scorecard (.drawio page)
2. A Leverage Score showing business independence from the owner
3. Concrete action steps for upgrading the highest-leverage gaps
4. Asset upgrade items that feed directly into the Action Roadmap

---

## Two Modes

### Integrated Mode (Recommended)
- Runs as part of the progressive interview, after swimlanes are complete
- Claude has been silently tracking asset signals since the Business Map phase
- ~16 assets already have signal data — Claude uses these to ask smarter, faster confirmation questions
- **Claude does NOT pre-score.** It presents what it observed and asks the user to confirm or correct before scoring.

### Standalone Mode
- Triggered directly: "score my assets", "24 assets", "leverage score", "asset assessment"
- No prior interview data — asks all questions from scratch
- Same question flow, just needs slightly more context per question
- If a `.drawio` file exists, Claude reads it first for context (but still asks, never assumes scores)

---

## How Silent Tracking Works (Integrated Mode)

During the progressive interview, Claude maintains an internal `ASSET SIGNALS` tracker (never shown to user). This is NOT scoring — it's noting what surfaced:

```
ASSET SIGNALS (internal — do NOT show to user during interview)
────────────────────────────────────────────
Content: YouTube + Substack mentioned, repurposing system described
Methodology: "My 5-step process" mentioned but not named or documented
Channels: YouTube + newsletter + LinkedIn active
Core Product: $5K coaching program, delivery described
Marketing Systems: Manual follow-up, no automation mentioned
Positioning: [no signal]
Ambassadors: [no signal]
Data: [no signal]
...
```

**What to track silently:**
- Business Map phase → Products, Channels, Team, Positioning signals
- Bow-Tie phase → Gifts (lead magnet), P4P, Marketing Systems, Content signals
- Swimlane phases → Systems assets, Culture assets, Operations assets

**What NOT to do:**
- Do NOT announce asset scores during mapping ("your Methodology is Red")
- Do NOT ask asset-specific questions during other phases
- Do NOT deviate from the current phase to explore an asset
- Just note signals and move on

See `references/24-assets-framework.md` → "Inference Signals" per asset for what to listen for.

---

## Prerequisites

**Integrated Mode:**
- [ ] Business Map complete (at minimum)
- [ ] At least 1 swimlane mapped
- [ ] File path to .drawio known

**Standalone Mode:**
- None — the workflow handles discovery internally

---

## Execution Instructions (Integrated Mode)

### Step 1: Educate — What Are Digital Assets?

When transitioning from swimlanes to the 24 Assets assessment, introduce the framework properly. The user needs to understand WHY this matters.

Say this:
> "Now that we've mapped your operations, let's look at your business through a different lens — your **Digital Assets**.
>
> This comes from Daniel Priestley's **24 Assets** framework. The idea is simple: a business without assets is just a job. **Assets** are the things that generate value without you being in the room — your content library, your brand identity, your systems, your documented processes.
>
> Every business has 24 possible assets across 7 categories:
> - **IP** — Content, Methodology, Registered IP
> - **Brand** — Philosophy, Identity, Ambassadors
> - **Market** — Positioning, Channels, Data
> - **Products** — Gifts, entry offer, core product, recurring offer
> - **Systems** — Marketing, management, and operations systems
> - **Culture** — Key people and team capabilities
> - **Funding** — Business plan, valuation, structure, risk
>
> Each asset gets scored:
> - **Green (Remarkable)** — professionally built, runs without you, people talk about it
> - **Yellow (Basic)** — exists but self-made, inconsistent, or depends on you
> - **Red (Missing)** — doesn't exist, or only lives in your head
>
> From these scores we'll calculate your **Leverage Score** — what percentage of your critical assets are working without you. At 70%+, the business runs and grows without you in every meeting.
>
> I picked up a lot of signals during our mapping, so this should be fast. I'll show you what 'Green' looks like for each asset and ask where you stand. Should take about 10-15 minutes.
>
> Ready?"

STOP. Wait for acknowledgment.

---

### Step 2: Smart Context Filter

Before asking questions, Claude silently:

1. **Identifies business type** from earlier interview (Coach, Agency, SaaS, etc.)
2. **Flags obviously irrelevant assets** based on what's already known:
   - Solo business with no plans to hire → Culture team assets (18-20) get auto-deprioritized
   - No exit/investment plans mentioned → Funding assets (21-24) get auto-deprioritized
   - One-person operation → Mgmt & Admin Systems may be deprioritized
3. **Groups assets by signal strength:**
   - **Strong signal** (~8-10 assets) — Claude observed clear evidence, can ask a focused confirmation question
   - **Weak signal** (~6-8 assets) — Claude saw hints but needs clarification
   - **No signal** (~6-8 assets) — Never came up, needs fresh questions

This determines pacing: strong-signal assets fly by in seconds, no-signal assets need the full Green-standard question.

---

### Step 3: Score Assets — Category by Category

**For each asset, the pattern is:**

1. **Show the Green standard** — what "Remarkable" looks like for this specific asset. Be concrete.
2. **Reference what Claude observed** (if any signal exists) — "From what we mapped, I noticed [X]..."
3. **Ask an open question** — "Does that pass this bar, or is there more I haven't seen?"
4. **Claude scores** Green/Yellow/Red based on their answer — with a brief explanation
5. **Flag deprioritization** — if the asset clearly isn't relevant for this business model, confirm with user: "This scored Red but sounds like it's not a priority for your model right now — should I gray it out?"

**CRITICAL RULES:**
- **DO NOT pre-score.** Claude presents what it observed and asks — the user's answer determines the score.
- **DO NOT ask the user to pick Green/Yellow/Red.** They describe reality, you score it.
- **BE SMART about irrelevant assets.** Solo business? Don't ask 4 separate questions about team composition. Batch them: "Since you're solo, I'll mark the team assets as Red/deprioritized — unless you have contractors or plans to hire?"
- **Reference the mapping.** "When we mapped your Lead Gen, I noticed there's no automated nurture — that's relevant to your Marketing Systems asset."

**Conversational pacing:** Ask about 1-2 assets, get a response, score them, move to the next. Don't dump all assets in a category at once.

---

#### Category 1: IP Assets

**If Claude has signals from Business Map/Bow-Tie:**

> "Let's start with your **IP Assets**.
>
> **1. Content** — For Green, you'd need a large, organized content library with a repurposing system that runs without you constantly creating every piece.
>
> From our mapping, I saw you have [YouTube/Substack/etc.] and [description of what surfaced]. Does that pass the Green bar, or is it more inconsistent than it looks from the outside?"

STOP. Wait. Score based on answer.

> "**2. Methodology** — For Green, you'd need a *named*, documented process that someone else could follow. Clients can explain your method to others and it's published somewhere.
>
> [If signal]: You mentioned [your X-step process / framework name] earlier. Is that written down anywhere, or does it mostly live in your head?"
>
> [If no signal]: "Do you have a named framework or process that you take every client through?"

STOP. Wait. Score.

> "**3. Registered IP** — For Green: trademarks filed on your business name and methodology, key content copyrighted.
>
> Have you filed any trademarks or formal IP protection?"

STOP. Wait. Score. (This one rarely has signals — always ask fresh.)

---

#### Category 2: Brand Assets

> "**Brand Assets** — how people perceive your business.
>
> **4. Philosophy** — For Green: a written manifesto or 'what we believe' page that's published and polarizing enough to filter people in or out.
>
> [If signal]: Your content seems pretty opinion-led based on what you shared. Is your philosophy written down anywhere, or does it just come through organically?"
>
> [If no signal]: "Do you have your core beliefs and values documented and published?"

STOP. Wait. Score.

> "**5. Identity** — For Green: a professional brand guide exists, consistent look across all platforms, someone else could create on-brand materials using the guide alone.
>
> How consistent is your visual brand across platforms? Do you have a brand guide?"

STOP. Wait. Score.

> "**6. Ambassadors** — For Green: documented case studies with real results, an active referral system, people recommend you without being asked.
>
> Do you have case studies, testimonials, or any kind of referral system?"

STOP. Wait. Score.

---

#### Category 3: Market Assets

> "**Market Assets** — your position in the market.
>
> **7. Positioning** — For Green: clear niche ownership validated externally — awards, press, speaking invitations. People in your market know your name.
>
> [If signal]: From your Business Map, your positioning seems to be [X]. Is that recognized externally, or is it still mostly self-described?"
>
> [If no signal]: "How clear is your positioning? Would people in your market recognize you as 'the [X] person'?"

STOP. Wait. Score.

> "**8. Channels** — For Green: multiple active channels driving predictable traffic. You could lose one and still grow. You know your numbers.
>
> [Strong signal — channels were in the Business Map]: We mapped your traffic as [YouTube, newsletter, etc.]. How predictable is that traffic? Could you lose one channel and still grow?"

STOP. Wait. Score.

> "**9. Data** — For Green: CRM with segmented contacts, lead scoring, behavioral tracking. You know conversion rates at each stage.
>
> What do you use to track your audience? Email list, CRM, analytics — what does that look like?"

STOP. Wait. Score.

---

#### Category 4: Product Assets

> "**Product Assets** — your value ladder.
>
> [Strong signal — products were mapped in detail]: We already mapped your products, so let me run through these quickly.
>
> **10. Gifts** — For Green: a remarkable free resource people actively share and tell others about. Not just a PDF — something so good it spreads on its own.
>
> [If lead magnet surfaced]: You have [lead magnet]. Does it generate leads on its own, or is it more of a nice-to-have?"

STOP. Wait. Score.

> "**11. P4P (Product for Prospects)** — For Green: a clear, named entry offer ($47-$497) with its own landing page that converts cold leads predictably.
>
> [If low-ticket surfaced]: Your [workshop/mini-course] — is that packaged with its own page and delivery system, or more ad-hoc?"
>
> [If nothing below main offer]: "Do you have anything in the $47-$497 range? A workshop, mini-course, diagnostic?"

STOP. Wait. Score.

> "**12. Core Product** — For Green: named offer with documented delivery. Could be delivered by someone else following your system. Clients get consistent results.
>
> [Strong signal]: Your [product name] at [$X] — could someone else deliver it using your process, or does it depend on you being in the room?"

STOP. Wait. Score.

> "**13. P4C (Products for Clients)** — For Green: active recurring revenue — membership, community, retainer — that keeps clients paying month over month.
>
> Do you have any recurring revenue from existing clients?"

STOP. Wait. Score.

---

#### Category 5: Systems Assets

> "**Systems Assets** — how your business runs.
>
> [Strong signal — swimlanes revealed these]: This is where our swimlane mapping really pays off. I can already see a lot here.
>
> **14. Marketing & Sales Systems** — For Green: fully automated lead capture → nurture → sales pipeline. Leads convert without you manually chasing.
>
> [Reference swimlane]: When we mapped your [Lead Gen/Sales] process, I noticed [specific observation — e.g., 'the nurture step is completely manual' or 'you have automation from signup to welcome sequence but then it drops off']. Does that capture it, or is there more automation I didn't see?"

STOP. Wait. Score.

> "**15. Management & Admin Systems** — For Green: real-time dashboard, documented admin processes, someone else could handle all admin using your systems.
>
> How do you handle finances, scheduling, and project tracking?"

STOP. Wait. Score.

> "**16. Operations Systems** — For Green: documented SOPs for your delivery processes. A new team member could follow them and deliver consistent quality.
>
> [Reference swimlane]: When we mapped your [Fulfillment] process, the delivery steps were [observation]. Are those documented anywhere, or does it all live in your head?"

STOP. Wait. Score.

---

#### Category 6: Culture Assets

**If solo operator (most common), batch these:**

> "**Culture Assets** — your team and key people.
>
> Since you're running solo, I'll keep this quick.
>
> **17. Key People of Influence** — This is about YOU. For Green: invited to speak, featured in media, people seek you out without you pitching.
>
> How's your personal brand? Do opportunities come to you, or are you still chasing attention?"

STOP. Wait. Score.

> "**18-20. Sales & Marketing People, Mgmt & Admin People, Technicians** — Since you're solo, these are all Red by definition. But they're also not a priority until you're ready to build a team.
>
> Unless you have contractors or VAs helping — anyone I should know about?"

STOP. Wait. Score all three. Auto-deprioritize if confirmed solo.

**If team exists:** Ask each role individually, focusing on whether training materials and documented processes exist for each function.

---

#### Category 7: Funding Assets

**If no exit/investment signals (most cases), batch:**

> "Last category — **Funding Assets**. These matter most when you're raising capital or planning an exit. Quick round:
>
> **21. Business Plan** — Do you have a written plan with financial projections?
> **22. Valuation** — Do you know what your business is worth?
> **23. Structure** — What's your business structure? (Ltd, LLC, sole trader?)
> **24. Risk Mitigation** — Any business insurance or legal protections in place?
>
> Quick answers work fine here."

STOP. Wait. Score all four. Deprioritize the whole category if user confirms no exit/investment plans.

**If user mentioned exit or investors:** Ask each one individually with full Green standard.

---

### Step 4: Final Score Tally + Leverage Score

Calculate and present:

> "Here's your 24 Assets score:
>
> **Green (Remarkable):** [X] assets — [list them]
> **Yellow (Basic):** [Y] assets — [list them]
> **Red (Missing):** [Z] assets — [list them]
> **Deprioritized:** [D] assets — [list them] *(excluded from Leverage Score)*
>
> **Your Leverage Score: [X]%**
> *(Green assets ÷ Active assets [excluding deprioritized] × 100)*
>
> At [X]%, [contextual interpretation — see framework reference for ranges].
> Your biggest leverage gaps are in [top 2-3 areas]."

---

### Step 5: Action Guidance for Top Gaps

For the **top 3 highest-leverage Red/Yellow assets** (non-deprioritized only), present specific upgrade steps from `references/24-assets-framework.md`.

Prioritize by:
1. **Load-bearing assets** — directly blocking revenue growth
2. **Keystone assets** — unlocking multiple other assets (Methodology, Content, Core Product, Marketing Systems)
3. **Quick wins** — Red→Yellow in under 2 weeks
4. **Connected to swimlane findings** — "This connects to the bottleneck we found in your Lead Gen process"

> "Your 3 highest-leverage asset upgrades:
>
> **1. [Asset]** [score]→[target] *(why it matters)*
> - [Action step 1]
> - [Action step 2]
> - **Effort:** [estimate]
> - **Connects to:** [reference specific swimlane finding if applicable]
>
> [repeat for #2 and #3]
>
> Ready to generate your **24 Assets Scorecard** diagram?"

STOP. Wait for confirmation.

---

### Step 6: Generate 24 Assets Scorecard Diagram

Generate the 24 Assets Scorecard page directly:

1. Read `references/scorecard-template.md` for the COMPLETE page standard including:
   - Visual structure (7 stacked category bands)
   - Precise pixel positions for all elements
   - XML patterns for every element type (including UserObject wrapper for tooltips)
   - Color codes for Green/Yellow/Red scoring
   - Deprioritized styling (gray fill + colored border)
   - Muted styling for Secondary-tier categories
   - ID naming convention
2. Read `references/drawio-standards.md` for general XML standards
3. Generate scorecard XML with all 24 asset scores applied
4. Add as new page to existing .drawio file
   - Page name: '24 Assets Scorecard'
   - Page ID: 'page-assets'
   - Position: After System Connection Map page, before Action Roadmap page
5. Tell the user: "24 Assets Scorecard added to your diagram."

---

### Step 7: Revenue Planning

Connect scored gaps to the user's revenue target.

> "Let's connect your asset gaps to revenue.
>
> **Current:** $[X]/month (from your Math column)
> **Target:** What revenue target are we working toward?"

STOP. Wait for response.

Then present the revenue connection:

> "To close the gap from $[current] to $[target]/month, here are the assets that move the needle most:
>
> 1. **[Asset]** — [how upgrading it unlocks revenue, specific to their business]
> 2. **[Asset]** — [connection to revenue]
> 3. **[Asset]** — [connection to revenue]
>
> Want me to add these as priority items in your Action Roadmap?"

STOP. Wait.

---

### Step 8: Feed Into Action Roadmap

Asset upgrade action steps become items in the Action Roadmap as a new category:

**Category:** Asset Upgrades
**Symbol:** brown circle
**Color:** Brown (`#8B4513` stroke, `#fdf6f0` fill)

Each upgrade item gets scored using the same Impact + Effort + Dependency framework as other roadmap items. The roadmap combines:
- **Swimlane findings** — bottlenecks, automation opportunities, missing steps
- **Asset gaps** — Red/Yellow assets with upgrade action steps
- **One unified priority list** — not two separate sections

Hand off to `workflows/generate-roadmap.md` with the asset upgrade items included.

---

## Execution Instructions (Standalone Mode)

When running WITHOUT a prior Business X-Ray session.

### Standalone Step 1: Opening + Context Gathering

> "Let's run a **24 Assets Assessment** on your business — a framework from Daniel Priestley that scores 24 key assets across 7 categories.
>
> Before we score each asset, I need a quick picture of your business so I can ask the right questions.
>
> **What type of business do you run, and what do you sell?**"

STOP. Wait.

### Standalone Step 2: Quick Context (2-3 Questions, ONE at a time)

1. **Business type + products** → Identifies archetype, informs which assets to deprioritize
2. **Team size** → "Is it just you, or do you have a team?" → Determines Culture relevance
3. **Revenue stage** → "Roughly where are you revenue-wise — pre-revenue, under $10K/mo, $10-50K, $50K+?" → Sets Funding tier relevance

**After context gathering:** Proceed to Step 1 (Educate) and Step 3 (Score) of the main flow. Same question pattern — show Green standard, ask, score. Just no swimlane references to draw from.

---

## Leverage Score Calculation

```
Active Assets = Total 24 - Deprioritized count
Leverage Score = (Green assets in Active pool) / Active Assets × 100%
```

**Deprioritized assets are EXCLUDED from both numerator and denominator.** They don't count toward or against the score. This means a solo coach who correctly deprioritizes 6 team/funding assets gets scored on 18 assets — a more honest picture.

**Score ranges:**

| Score Range | Interpretation |
|-------------|----------------|
| 0–30% | Owner-dependent. Revenue stops if you step back. |
| 31–50% | Some leverage. Business runs partly without you. |
| 51–69% | Functional leverage. Can take short breaks. |
| 70%+ | Business runs without you. Investable and scalable. |

---

## Resume State

Add these fields to the YAML resume block:

```yaml
assets_assessment_complete: false
assets_scores:
  ip:
    content: null       # green/yellow/red
    methodology: null
    registered_ip: null
  brand:
    philosophy: null
    identity: null
    ambassadors: null
  market:
    positioning: null
    channels: null
    data: null
  product:
    gifts: null
    p4p: null
    core_product: null
    p4c: null
  systems:
    marketing_sales: null
    mgmt_admin: null
    operations: null
  culture:
    key_people: null
    sales_marketing_people: null
    mgmt_admin_people: null
    technicians: null
  funding:
    business_plan: null
    valuation: null
    structure: null
    risk_mitigation: null
deprioritized_assets: []  # list of asset IDs, e.g. ["registered_ip", "data"]
leverage_score: null
revenue_current: null
revenue_target: null
asset_upgrades_identified: []
```

---

## Next Workflow

After 24 Assets Assessment is complete:
- **Generate Roadmap:** → `workflows/generate-roadmap.md` (combines swimlane findings + asset upgrades into one priority list)
- **Stop here:** Output .drawio + resume block

---

## References (Load On-Demand)

| Reference | When to Load |
|-----------|-------------|
| `references/24-assets-framework.md` | At Step 3 — scoring criteria, Green standards, inference signals, and action playbook |
| `references/scorecard-template.md` | At Step 6 — read this to generate the .drawio scorecard page |
| `references/business-archetypes.md` | At Step 2 — default relevance tiers per archetype |

---

**Created:** 2026-02-26
**Updated:** 2026-02-26
