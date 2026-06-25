# Business X-Ray

Source: business-x-ray/workflows/rescore-assets.md
MIME: text/markdown

# Re-Score Assets Workflow (Quarterly)

**Update existing 24 Assets scores and track progress over time.**

---

## Purpose

After the initial 24 Assets Assessment, users return periodically to update individual asset scores as they complete roadmap items. This workflow:
1. Reads the existing 24 Assets Scorecard from the report HTML
2. Presents current scores for review
3. Lets the user update changed assets
4. Recalculates the Leverage Score
5. Regenerates the infographic with updated colors
6. Shows before/after comparison

---

## Triggers

- User says "rescore my assets", "update my scores", "check my progress", "re-assess"
- User returns after completing roadmap items and wants to see updated scores

---

## Prerequisites

- [ ] Existing report HTML with a "24 Assets Scorecard" section
- [ ] Previous scores available (in YAML resume block)

---

## Execution Instructions

### Step 1: Load Existing Scores

Read the existing scorecard from the report HTML:
1. Find the "24 Assets Scorecard" section in the HTML
2. Extract current scores per asset (look for color-coded badges: green/yellow/red)
3. Compare to the YAML resume block

If no report HTML exists, ask user to paste their YAML resume block or run a fresh assessment.

### Step 2: Present Current Scores

> "Here are your current 24 Assets scores from your last assessment:
>
> **Leverage Score: [X]%**
>
> | Category | Asset | Current Score |
> |----------|-------|---------------|
> | IP | Content | 🟡 Yellow |
> | IP | Methodology | 🔴 Red |
> | ... | ... | ... |
>
> Which assets have changed since your last assessment?"

STOP. Wait for response.

### Step 3: Update Individual Scores

For each asset the user mentions:
1. Confirm the new score with brief reasoning
2. Apply the 4 quality tests (Remarkability, 90-Day Yachting, Digital Scalability, Evergreen)

> "You documented your methodology and named it. Does it pass the 90-Day Yachting Test — could someone else use the framework without you explaining it?"

STOP. Confirm score change.

### Step 4: Recalculate Leverage Score

Calculate new Leverage Score and show comparison:

> "**Before → After:**
> - Leverage Score: [old]% → [new]%
> - Green: [old] → [new]
> - Yellow: [old] → [new]
> - Red: [old] → [new]
>
> **Assets upgraded:**
> - Methodology: 🔴 → 🟡 (documented and named)
> - Marketing Systems: 🟡 → 🟢 (fully automated)
>
> Nice progress. Your business is [X]% less dependent on you than last quarter."

### Step 5: Regenerate Scorecard

Update the 24 Assets Scorecard page directly:

1. Read `references/scorecard-template.md` for the page standard
2. Update the existing report HTML scorecard section in place
3. Replace the existing '24 Assets Scorecard' page with updated scores and new Leverage Score
4. Write updated file
5. Tell the user: "Scorecard updated with new scores."

### Step 6: Identify Next Upgrades

> "Based on your updated scores, the next highest-leverage upgrades are:
> 1. [Asset] — [why and what to do]
> 2. [Asset] — [why and what to do]
>
> Want me to update your Action Roadmap with these new priorities?"

---

## Resume State

Update the existing YAML resume block with new scores and timestamp:

```yaml
assets_assessment_complete: true
assets_last_scored: "[date]"
leverage_score: [new value]
leverage_score_history:
  - date: "[previous date]"
    score: [previous value]
  - date: "[current date]"
    score: [new value]
```

---

**Created:** 2026-02-26
