# 24 Assets Scorecard Reference (HTML)

**Template and standards for rendering the 24 Assets Scorecard in the HTML report.**

---

## Overview

The 24 Assets framework (Daniel Priestley) categorizes everything a business owns into 7 families. Each asset gets a score: green (mature), yellow (developing), or red (missing or broken). The Leverage Score is calculated from these and represents how independent the business is from the owner.

---

## The 7 Categories

| # | Category | Relevance | What's In It |
|---|----------|-----------|--------------|
| 1 | **IP** | Critical | Content, Methodology, Registered IP |
| 2 | **Brand** | Important | Philosophy, Identity, Ambassadors |
| 3 | **Market** | Critical | Positioning, Channels, Data |
| 4 | **Product** | Critical | Gifts, P4P, Core Product, P4C |
| 5 | **Systems** | Critical | Marketing/Sales, Mgmt/Admin, Operations |
| 6 | **Culture** | Important | Key People, S&M People, M&A People, Technicians |
| 7 | **Funding** | Secondary | Plan, Valuation, Structure, Risk |

---

## HTML Pattern

```html
<section class="assets-scorecard">
  <h2>24 Assets Scorecard</h2>
  <p class="leverage-score">Leverage Score: <strong>62</strong> / 100</p>

  <div class="asset-grid">
    <div class="asset-category">
      <h3>IP <span class="relevance">Critical</span></h3>
      <div class="asset green">
        <strong>Content</strong> — published weekly, SEO-optimized
      </div>
      <div class="asset yellow">
        <strong>Methodology</strong> — documented but not trademarked
      </div>
      <div class="asset red">
        <strong>Registered IP</strong> — none
      </div>
    </div>

    <div class="asset-category">
      <h3>Brand <span class="relevance">Important</span></h3>
      <div class="asset green">
        <strong>Philosophy</strong> — clear, articulated everywhere
      </div>
      <div class="asset yellow">
        <strong>Identity</strong> — logo + colors but inconsistent application
      </div>
      <div class="asset red">
        <strong>Ambassadors</strong> — no formal program
      </div>
    </div>

    <!-- ... 5 more categories ... -->
  </div>
</section>
```

---

## Required CSS

```css
.assets-scorecard {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 1.5rem;
  margin: 1.5rem 0;
}
.leverage-score {
  font-size: 1.25rem;
  margin-bottom: 1rem;
}
.leverage-score strong { color: var(--accent); font-size: 1.75rem; }
.asset-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1rem;
}
.asset-category {
  background: rgba(255,255,255,0.03);
  border: 1px solid var(--border);
  border-radius: 6px;
  padding: 1rem;
}
.asset-category h3 {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.5rem;
}
.relevance {
  font-size: 0.7rem;
  padding: 0.15rem 0.5rem;
  border-radius: 999px;
  background: rgba(88,166,255,0.2);
  color: var(--accent);
}
.asset {
  padding: 0.5rem;
  margin-bottom: 0.5rem;
  border-radius: 4px;
  font-size: 0.85rem;
  border-left: 3px solid;
}
.asset.green { border-color: var(--green); }
.asset.yellow { border-color: var(--yellow); }
.asset.red { border-color: var(--red); }
```

---

## Leverage Score Formula

```
Leverage Score = sum(asset_weight * maturity_score) / total_weight * 100

where:
  asset_weight = 3 if Critical, 2 if Important, 1 if Secondary
  maturity_score = 1.0 (green), 0.5 (yellow), 0.0 (red)
```

| Score | Meaning |
|-------|---------|
| 0-30 | Owner-dependent. No systems, no leverage. |
| 31-60 | Some leverage. Brand + IP working. Systems incomplete. |
| 61-85 | Strong leverage. Most assets mature. |
| 86-100 | Fully leveraged. Business runs without owner. |

---

## Inference Signals

For each asset, watch the conversation for these signals:

**IP — Content:** Does the user publish regularly? Where? What's the cadence?
**IP — Methodology:** Do they have a named process or framework? Documented anywhere?
**IP — Registered:** Trademarks, patents, copyrights registered?

**Brand — Philosophy:** Can they articulate why they exist beyond money?
**Brand — Identity:** Logo, colors, fonts, voice — consistent everywhere?
**Brand — Ambassadors:** Active referral program? Brand evangelists?

**Market — Positioning:** Clear niche? Differentiated from competitors?
**Market — Channels:** Multiple traffic sources? Active distribution?
**Market — Data:** Email list, CRM, customer database — what's tracked?

**Product — Gifts:** Free lead magnets, samples, demos?
**Product — P4P (Paid for Promise):** Low-ticket entry offers?
**Product — Core:** Main high-ticket offer with clear value?
**Product — P4C (Paid for Continuity):** Subscription, retainer, membership?

**Systems — Marketing/Sales:** Funnels, automation, sequences running?
**Systems — Mgmt/Admin:** Bookkeeping, legal, ops automated?
**Systems — Operations:** Delivery systems, SOPs, repeatable processes?

**Culture — Key People:** Senior leadership, partners, advisors?
**Culture — S&M People:** Sales team, marketing team?
**Culture — M&A People:** Ops, finance, HR?
**Culture — Technicians:** Deliverers, customer-facing roles?

**Funding — Plan:** Written business plan, financial model?
**Funding — Valuation:** Knows what the business is worth?
**Funding — Structure:** Right legal entity, tax setup?
**Funding — Risk Mitigation:** Insurance, contracts, contingency?

---

## Purpose

Standard reference for generating 24 Assets Scorecards in the HTML report.