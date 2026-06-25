# Bow-Tie Funnel Reference (HTML)

**Template and standards for rendering bow-tie funnels in the HTML report.**

---

## Overview

The Bow-Tie Funnel is a 3-column grid that visualizes the customer journey from first touch through delivery. It gets its name from the shape: the customer pool narrows on the left (acquisition), ties at the center (commit), and expands on the right (delivery).

---

## HTML Pattern

```html
<div class="bowtie">
  <div class="bowtie-side acquisition">
    <h3>ACQUISITION</h3>
    <div class="bowtie-stage">
      <strong>1. Awareness</strong>
      [How strangers discover you]
    </div>
    <div class="bowtie-stage">
      <strong>2. Nurturing</strong>
      [How they warm up to you]
    </div>
    <div class="bowtie-stage">
      <strong>3. Consideration</strong>
      [How they evaluate buying]
    </div>
  </div>
  <div class="bowtie-knot">COMMIT</div>
  <div class="bowtie-side delivery">
    <h3>DELIVERY</h3>
    <div class="bowtie-stage">
      <strong>4. Onboarding</strong>
      [How new clients get started]
    </div>
    <div class="bowtie-stage">
      <strong>5. Launch</strong>
      [First real interaction]
    </div>
    <div class="bowtie-stage">
      <strong>6. Results</strong>
      [Outcomes + testimonials + referrals]
    </div>
  </div>
</div>
```

---

## Required CSS

```css
.bowtie {
  display: grid;
  grid-template-columns: 1fr 80px 1fr;
  gap: 1rem;
  align-items: center;
  margin: 1.5rem 0;
}
.bowtie-side {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 1rem;
}
.bowtie-side.acquisition { border-top: 3px solid var(--blue); }
.bowtie-side.delivery { border-top: 3px solid var(--green); }
.bowtie-knot {
  text-align: center;
  background: var(--surface);
  border: 2px solid var(--accent);
  border-radius: 50%;
  width: 80px;
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  font-size: 0.75rem;
  margin: 0 auto;
}
.bowtie-stage {
  padding: 0.5rem;
  border-bottom: 1px solid var(--border);
  font-size: 0.875rem;
}
.bowtie-stage:last-child { border-bottom: none; }
.bowtie-stage strong { color: var(--accent); display: block; margin-bottom: 0.25rem; }
```

---

## Inference Rules

When inferring stages from a Business Map, use these heuristics:

| Stage | Infer From | Common Examples |
|-------|------------|-----------------|
| **Awareness** | TRAFFIC column | YouTube, Instagram, LinkedIn, blog, podcast |
| **Nurturing** | CONVERTERS + email sequence | Lead magnet, newsletter, retargeting |
| **Consideration** | FUNNELS column | Application, webinar, DMs, free trial |
| **Commit** | PRODUCTS column | Call → Payment, checkout, contract |
| **Onboarding** | Fulfillment kickoff | Intake form, welcome sequence, kickoff call |
| **Launch** | First delivery | First session, module access, first deliverable |
| **Results** | Ongoing + retention | Outcomes, testimonials, upsells, referrals |

---

## Variants

**Service Provider** (3 stages per side, not 3+3): combine Nurturing + Consideration into "Evaluation", keep the rest the same.

**E-commerce / Course Creator:** "Commit" becomes "Purchase" (no call), and Delivery includes "Access Granted" instead of "Onboarding Call".

**High-ticket Coach / Consultant:** "Commit" is "Sales Call" → "Payment" (two stages).

---

## Purpose

Standard reference for generating bow-tie funnels in the HTML report.