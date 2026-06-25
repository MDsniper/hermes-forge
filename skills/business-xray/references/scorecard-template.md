# Business X-Ray

Source: business-x-ray/references/scorecard-template.md
MIME: text/markdown

# 24 Assets Scorecard Reference (.drawio)

**Template and standards for generating the 24 Assets Scorecard page in draw.io format.**

---

> **CRITICAL: BAND LAYOUT - NOT A FLOWCHART**
>
> The 24 Assets Scorecard is a **VERTICAL BAND GRID**, not a flowchart with connections.
>
> **CORRECT:**
> - 7 horizontal category bands stacked vertically
> - Each band has a dark header row + asset boxes below it
> - Asset boxes are colored Green/Yellow/Red based on score — NO arrows between them
> - Score summary header at the top shows aggregate leverage score
>
> **WRONG:**
> - Connecting boxes with arrows
> - Single table with text rows
> - Mixing colors inconsistently across bands
> - Leaving out the score summary header
>
> **Each asset = its own colored rectangle.** "Content", "Methodology", "Registered IP" = 3 separate boxes in the IP band.

---

## Overview

The 24 Assets Scorecard visualizes business asset strength across 7 categories:
- **IP Assets** — Intellectual property and proprietary content
- **Brand Assets** — Positioning, identity, and social proof
- **Market Assets** — Market access, channels, and data
- **Product Assets** — Gift → P4P → Core Product → P4C value ladder
- **Systems Assets** — Marketing, management, and operations systems
- **Culture Assets** — Key people and team capabilities
- **Funding Assets** — Secondary tier; financial readiness (muted by default)

Each asset is scored: **Green (Remarkable)**, **Yellow (Basic/Functional)**, or **Red (Not Existing/Missing)**.

Assets that are scored but **not a priority** for the current business model get **deprioritized styling**: gray fill with the scored color as border (e.g., gray fill + red border = "Missing but not urgent").

The **Leverage Score** = Green assets ÷ Active assets (excluding deprioritized) × 100%. Deprioritized assets don't count toward or against the score.

---

## Visual Structure

```
┌──────────────────────────────────────────────────────────────────┐
│  24 ASSETS SCORECARD: [Business Name]                            │  Title
│  Leverage Score: 33%  |  5 Green  |  10 Yellow  |  9 Red        │  Score Summary
├──────────────────────────────────────────────────────────────────┤
│  IP ASSETS  [#424242 header]                                     │  BAND 1
│  ┌──────────┐  ┌──────────────┐  ┌─────────────────┐            │
│  │ Content  │  │ Methodology  │  │  Registered IP  │            │
│  └──────────┘  └──────────────┘  └─────────────────┘            │
├──────────────────────────────────────────────────────────────────┤
│  BRAND ASSETS                                                    │  BAND 2
│  ┌────────────┐  ┌────────────┐  ┌──────────────┐               │
│  │ Philosophy │  │  Identity  │  │ Ambassadors  │               │
│  └────────────┘  └────────────┘  └──────────────┘               │
├──────────────────────────────────────────────────────────────────┤
│  MARKET ASSETS                                                   │  BAND 3
│  ┌─────────────┐  ┌────────────┐  ┌────────┐                    │
│  │ Positioning │  │  Channels  │  │  Data  │                    │
│  └─────────────┘  └────────────┘  └────────┘                    │
├──────────────────────────────────────────────────────────────────┤
│  PRODUCT ASSETS                                                  │  BAND 4
│  ┌────────┐  ┌────────┐  ┌──────────────┐  ┌────────┐          │
│  │ Gifts  │  │  P4P   │  │ Core Product │  │  P4C   │          │
│  └────────┘  └────────┘  └──────────────┘  └────────┘          │
│  ╱ ascending curve line underneath ╱                             │
├──────────────────────────────────────────────────────────────────┤
│  SYSTEMS ASSETS                                                  │  BAND 5
│  ┌────────────────┐  ┌────────────────┐  ┌────────────┐         │
│  │ Marketing &    │  │   Mgmt &       │  │ Operations │         │
│  │ Sales Systems  │  │ Admin Systems  │  │  Systems   │         │
│  └────────────────┘  └────────────────┘  └────────────┘         │
├──────────────────────────────────────────────────────────────────┤
│  CULTURE ASSETS                                                  │  BAND 6
│  ┌──────────────────────────────────────────────────┐            │
│  │            Key People of Influence               │            │
│  └──────────────────────────────────────────────────┘            │
│  ┌────────────────┐  ┌────────────┐  ┌──────────────┐           │
│  │ Sales &        │  │  Mgmt &    │  │ Technicians  │           │
│  │ Marketing      │  │  Admin     │  │              │           │
│  └────────────────┘  └────────────┘  └──────────────┘           │
├──────────────────────────────────────────────────────────────────┤
│  FUNDING ASSETS  [muted if Secondary]                            │  BAND 7
│  ┌─────────────┐ ┌───────────┐ ┌───────────┐ ┌───────────────┐  │
│  │Business Plan│ │ Valuation │ │ Structure │ │Risk Mitigation│  │
│  └─────────────┘ └───────────┘ └───────────┘ └───────────────┘  │
├──────────────────────────────────────────────────────────────────┤
│ LEGEND: 🟢 Remarkable  🟡 Basic/Functional  🔴 Not Existing      │
└──────────────────────────────────────────────────────────────────┘
```

---

## Canvas Settings

```xml
<mxGraphModel dx="992" dy="1400" grid="1" gridSize="10" guides="1"
              tooltips="1" connect="1" arrows="1" fold="1" page="0"
              pageScale="1" pageWidth="900" pageHeight="1600">
```

---

## Element Positioning

Precise pixel coordinates for every element on the page:

| Element | X | Y | Width | Height | Notes |
|---------|---|---|-------|--------|-------|
| Title | 30 | 20 | 840 | 40 | Full width, left-aligned |
| Score summary | 30 | 60 | 840 | 25 | Leverage Score + counts |
| Separator line | 30 | 95 | 840 | 2 | Thin horizontal rule |
| Band 1 header (IP) | 30 | 110 | 840 | 28 | Dark gray #424242 |
| Band 1 box 1 (Content) | 40 | 145 | 260 | 85 | 3-col, 3 lines + tooltip |
| Band 1 box 2 (Methodology) | 310 | 145 | 260 | 85 | |
| Band 1 box 3 (Registered IP) | 580 | 145 | 260 | 85 | |
| Band 2 header (Brand) | 30 | 245 | 840 | 28 | |
| Band 2 box 1 (Philosophy) | 40 | 280 | 260 | 85 | 3-col layout |
| Band 2 box 2 (Identity) | 310 | 280 | 260 | 85 | |
| Band 2 box 3 (Ambassadors) | 580 | 280 | 260 | 85 | |
| Band 3 header (Market) | 30 | 380 | 840 | 28 | |
| Band 3 box 1 (Positioning) | 40 | 415 | 260 | 85 | 3-col layout |
| Band 3 box 2 (Channels) | 310 | 415 | 260 | 85 | |
| Band 3 box 3 (Data) | 580 | 415 | 260 | 85 | |
| Band 4 header (Product) | 30 | 515 | 840 | 28 | |
| Band 4 box 1 (Gifts) | 40 | 550 | 195 | 85 | 4-col layout |
| Band 4 box 2 (P4P) | 245 | 550 | 195 | 85 | |
| Band 4 box 3 (Core Product) | 450 | 550 | 195 | 85 | |
| Band 4 box 4 (P4C) | 655 | 550 | 195 | 85 | |
| Product curve line | 40 | 640 | 810 | 20 | Ascending dotted line |
| Band 5 header (Systems) | 30 | 675 | 840 | 28 | |
| Band 5 box 1 (Marketing & Sales) | 40 | 710 | 260 | 85 | 3-col layout |
| Band 5 box 2 (Mgmt & Admin) | 310 | 710 | 260 | 85 | |
| Band 5 box 3 (Operations) | 580 | 710 | 260 | 85 | |
| Band 6 header (Culture) | 30 | 810 | 840 | 28 | |
| Band 6 KPI box (Key People) | 40 | 845 | 810 | 70 | Full width, 3 lines |
| Band 6 sub-box 1 (Sales & Mktg) | 40 | 925 | 260 | 85 | 3-col layout |
| Band 6 sub-box 2 (Mgmt & Admin) | 310 | 925 | 260 | 85 | |
| Band 6 sub-box 3 (Technicians) | 580 | 925 | 260 | 85 | |
| Band 7 header (Funding) | 30 | 1025 | 840 | 28 | Muted if Secondary |
| Band 7 box 1 (Business Plan) | 40 | 1060 | 195 | 85 | 4-col layout |
| Band 7 box 2 (Valuation) | 245 | 1060 | 195 | 85 | |
| Band 7 box 3 (Structure) | 450 | 1060 | 195 | 85 | |
| Band 7 box 4 (Risk Mitigation) | 655 | 1060 | 195 | 85 | |
| Legend container | 30 | 1165 | 840 | 50 | |
| Back link | 30 | 1230 | 120 | 30 | Bottom left |

---

## Box Position Calculator

**3-column bands** (IP, Brand, Market, Systems):
- Box 1: x=40, width=260
- Box 2: x=310, width=260 (gap = 310 - (40+260) = 10px)
- Box 3: x=580, width=260 (gap = 580 - (310+260) = 10px)

**4-column bands** (Product, Funding):
- Box 1: x=40, width=195
- Box 2: x=245, width=195 (gap = 245 - (40+195) = 10px)
- Box 3: x=450, width=195 (gap = 450 - (245+195) = 10px)
- Box 4: x=655, width=195 (gap = 655 - (450+195) = 10px)

**Culture band special layout:**
- KPI row (Key People): x=40, width=810 (full width, single box)
- Sub-boxes row: 3-column layout starting at y=810

---

## Color System

### Score Colors

| Score | Fill | Stroke | Stroke Width | Font Color | Score Label |
|-------|------|--------|--------------|------------|-------------|
| Green (Remarkable) | `#f0fff0` | `#90EE90` | 3 | `#2e7d32` | "Remarkable" |
| Yellow (Basic/Functional) | `#fff8e6` | `#FFD166` | 2 | `#b8860b` | "Basic" |
| Red (Not Existing) | `#fff5f5` | `#FF6B6B` | 2 | `#c62828` | "Missing" |

### Asset Box Content (3 Lines + Tooltip)

Each asset box displays **3 lines of text** plus a **hover tooltip**:

```
Line 1: Asset Name (bold, 12px)
Line 2: Score Label (colored, 10px) — "Remarkable" / "Basic" / "Missing"
Line 3: Short Description (gray, 9px) — 1-line context visible in box
Tooltip: Full scoring reason + upgrade steps (shown on hover)
```

**Short Description examples:**
- Green Content: "YouTube + Substack, repurposing system"
- Yellow Methodology: "Framework exists, not documented"
- Red Registered IP: "No trademarks filed"
- Red P4P: "No entry-level product"

**Tooltip examples:**
- "YouTube + Substack publishing with repurposing system. Passes Remarkability and Digital Scalability tests."
- "CLO-OS framework exists but not publicly named or documented. Upgrade: Document as numbered steps, name it, create one-page visual. Effort: 1-2 days."
- "No trademarks, copyrights, or patent protection. Upgrade: Trademark your business name and methodology name. Effort: 2-4 weeks."

### Band Headers

| State | Fill | Font Color | Font Size | Font Style | Notes |
|-------|------|------------|-----------|------------|-------|
| Normal | `#424242` | `#ffffff` | 12 | Bold (1) | All bands except Funding when secondary |
| Muted (Secondary) | `#9e9e9e` | `#ffffff` | 12 | Bold (1) | Funding band when business is not at scale |

### Muted Asset Boxes (Secondary Tier)

Used for Funding band assets when the business is pre-scale:

| Property | Value |
|----------|-------|
| Fill | `#f9f9f9` |
| Stroke | `#cccccc` |
| Stroke Width | 1 |
| Font Color | `#999999` |
| Sub-label | Add italic note: "Becomes relevant at scale" |

### Deprioritized Asset Boxes (Low Priority for Business Model)

Used when an asset has a real score (Green/Yellow/Red) but is **not a priority** for this specific business model. The box gets gray fill but keeps the scored color as its border — visually signals "we know the status, it's just not where we focus."

**This is different from Muted/Secondary tier.** Secondary = entire category is irrelevant at this stage. Deprioritized = individual asset is scored but not worth acting on now.

| Base Score | Fill | Stroke | Stroke Width | Score Label Color | Notes |
|-----------|------|--------|--------------|-------------------|-------|
| Green (deprioritized) | `#f5f5f5` | `#90EE90` | 3 | `#999999` | Green border, gray fill |
| Yellow (deprioritized) | `#f5f5f5` | `#FFD166` | 2 | `#999999` | Yellow border, gray fill |
| Red (deprioritized) | `#f5f5f5` | `#FF6B6B` | 2 | `#999999` | Red border, gray fill |

**When to apply:**
- User explicitly says an asset isn't a priority
- Business model makes the asset irrelevant (e.g., Data for a fully inbound model, Registered IP for early-stage)
- AI flags it during assessment: "This is Red but low-priority for your model"

**Label format:** Same 3 lines as normal, but Line 2 adds "(Low Priority)" after the score label. Line 3 description text in `#aaaaaa` instead of `#666666`.

```
Line 1: Asset Name (bold, 12px, #999999)
Line 2: "Missing (Low Priority)" (10px, #999999)
Line 3: Short description (9px, #aaaaaa)
Tooltip: Same full detail — score reason + why deprioritized
```

### Title + Score Summary

| Element | Fill | Font Color | Font Size | Font Style |
|---------|------|------------|-----------|------------|
| Title | none (transparent) | `#1a1a2e` | 20 | Bold (1) |
| Score summary | `#f5f5f5` | `#333333` | 11 | Normal |
| Separator | `#e0e0e0` | — | — | — |

---

## ID Naming Convention

```
Page:              page-assets
Title:             sc-title
Score summary:     sc-score-summary
Separator:         sc-sep-1

Band headers:
  sc-hdr-ip
  sc-hdr-brand
  sc-hdr-market
  sc-hdr-product
  sc-hdr-systems
  sc-hdr-culture
  sc-hdr-funding

Asset boxes (sc-[category]-[asset]):
  sc-ip-content
  sc-ip-methodology
  sc-ip-registered
  sc-brand-philosophy
  sc-brand-identity
  sc-brand-ambassadors
  sc-market-positioning
  sc-market-channels
  sc-market-data
  sc-prod-gifts
  sc-prod-p4p
  sc-prod-core
  sc-prod-p4c
  sc-sys-marketing
  sc-sys-management
  sc-sys-operations
  sc-cult-kpi
  sc-cult-sales
  sc-cult-management
  sc-cult-technicians
  sc-fund-plan
  sc-fund-valuation
  sc-fund-structure
  sc-fund-risk

Special elements:
  sc-prod-curve      - Ascending dotted curve under Product band
  sc-legend          - Legend container box
  sc-legend-title    - "LEGEND:" text
  sc-legend-green    - Green swatch + label
  sc-legend-yellow   - Yellow swatch + label
  sc-legend-red      - Red swatch + label
  sc-back            - Back-to-Overview link
```

---

## XML Patterns

### 1. Title + Score Summary

```xml
<!-- Title -->
<mxCell id="sc-title" value="24 ASSETS SCORECARD: [Business Name]"
  style="text;html=1;strokeColor=none;fillColor=none;align=left;
         verticalAlign=middle;fontSize=20;fontStyle=1;fontColor=#1a1a2e;"
  vertex="1" parent="1">
    <mxGeometry x="30" y="20" width="840" height="40" as="geometry"/>
</mxCell>

<!-- Score Summary Bar -->
<mxCell id="sc-score-summary"
  value="Leverage Score: 33%  |  5 Green  |  10 Yellow  |  9 Red"
  style="text;html=1;strokeColor=none;fillColor=#f5f5f5;align=left;
         verticalAlign=middle;fontSize=11;fontColor=#333333;
         spacingLeft=10;rounded=1;"
  vertex="1" parent="1">
    <mxGeometry x="30" y="60" width="840" height="25" as="geometry"/>
</mxCell>

<!-- Separator -->
<mxCell id="sc-sep-1" value=""
  style="line;strokeColor=#e0e0e0;fillColor=none;strokeWidth=2;"
  vertex="1" parent="1">
    <mxGeometry x="30" y="95" width="840" height="2" as="geometry"/>
</mxCell>
```

### 2. Band Header (Normal)

Dark gray, full width. Use for IP, Brand, Market, Product, Systems, Culture.

```xml
<mxCell id="sc-hdr-ip" value="IP ASSETS"
  style="text;html=1;strokeColor=none;fillColor=#424242;align=left;
         verticalAlign=middle;fontSize=12;fontStyle=1;fontColor=#ffffff;
         spacingLeft=10;rounded=0;"
  vertex="1" parent="1">
    <mxGeometry x="30" y="110" width="840" height="28" as="geometry"/>
</mxCell>
```

### 3. Band Header (Muted / Secondary)

Gray, with "(Secondary)" appended to label. Use for Funding band when not at scale.

```xml
<mxCell id="sc-hdr-funding" value="FUNDING ASSETS  (Secondary — Becomes relevant at scale)"
  style="text;html=1;strokeColor=none;fillColor=#9e9e9e;align=left;
         verticalAlign=middle;fontSize=12;fontStyle=1;fontColor=#ffffff;
         spacingLeft=10;rounded=0;"
  vertex="1" parent="1">
    <mxGeometry x="30" y="890" width="840" height="28" as="geometry"/>
</mxCell>
```

### 4. Asset Box — Green (Remarkable)

Green fill, thick border (3px). 3 lines: name, score, description. Tooltip on hover via `UserObject` wrapper.

> **CRITICAL: Tooltip syntax.** Draw.io requires `UserObject` wrapper for tooltips. The `tooltip` attribute does NOT work on `mxCell` directly. Always use `UserObject` with `label` and `tooltip`, then nest `mxCell` inside.

```xml
<UserObject label="&lt;b style='font-size:12px;'&gt;Content&lt;/b&gt;&lt;br/&gt;
         &lt;span style='font-size:10px;color:#2e7d32;'&gt;Remarkable&lt;/span&gt;&lt;br/&gt;
         &lt;span style='font-size:9px;color:#666666;'&gt;YouTube + Substack, repurposing system&lt;/span&gt;"
  tooltip="YouTube + Substack publishing with repurposing system. Passes Remarkability and Digital Scalability tests."
  id="sc-ip-content">
    <mxCell style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f0fff0;
           strokeColor=#90EE90;strokeWidth=3;fontSize=11;
           verticalAlign=middle;align=center;"
      vertex="1" parent="1">
        <mxGeometry x="40" y="145" width="260" height="85" as="geometry"/>
    </mxCell>
</UserObject>
```

### 5. Asset Box — Yellow (Basic/Functional)

Yellow fill, medium border (2px). 3 lines + tooltip with upgrade steps.

```xml
<UserObject label="&lt;b style='font-size:12px;'&gt;Methodology&lt;/b&gt;&lt;br/&gt;
         &lt;span style='font-size:10px;color:#b8860b;'&gt;Basic&lt;/span&gt;&lt;br/&gt;
         &lt;span style='font-size:9px;color:#666666;'&gt;Framework exists, not documented&lt;/span&gt;"
  tooltip="CLO-OS framework exists but not publicly named or documented. Upgrade: Document as numbered steps, name it, create one-page visual. Effort: 1-2 days."
  id="sc-ip-methodology">
    <mxCell style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff8e6;
           strokeColor=#FFD166;strokeWidth=2;fontSize=11;
           verticalAlign=middle;align=center;"
      vertex="1" parent="1">
        <mxGeometry x="310" y="145" width="260" height="85" as="geometry"/>
    </mxCell>
</UserObject>
```

### 6. Asset Box — Red (Missing/Not Existing)

Red fill, medium border (2px). 3 lines + tooltip with upgrade steps.

```xml
<UserObject label="&lt;b style='font-size:12px;'&gt;Registered IP&lt;/b&gt;&lt;br/&gt;
         &lt;span style='font-size:10px;color:#c62828;'&gt;Missing&lt;/span&gt;&lt;br/&gt;
         &lt;span style='font-size:9px;color:#666666;'&gt;No trademarks filed&lt;/span&gt;"
  tooltip="No trademarks, copyrights, or patent protection. Upgrade: Trademark your business name and methodology name. Effort: 2-4 weeks."
  id="sc-ip-registered">
    <mxCell style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff5f5;
           strokeColor=#FF6B6B;strokeWidth=2;fontSize=11;
           verticalAlign=middle;align=center;"
      vertex="1" parent="1">
        <mxGeometry x="580" y="145" width="260" height="85" as="geometry"/>
    </mxCell>
</UserObject>
```

### 7. Asset Box — Muted (Secondary Tier)

Gray fill, thin border. Used for Funding/Culture when marked Secondary. Still includes description + tooltip.

```xml
<UserObject label="&lt;b style='font-size:12px;color:#999999;'&gt;Business Plan&lt;/b&gt;&lt;br/&gt;
         &lt;span style='font-size:9px;color:#aaaaaa;font-style:italic;'&gt;
           Becomes relevant at scale&lt;/span&gt;"
  tooltip="No written business plan or financial projections. Becomes relevant when seeking investment or at $1M+ ARR."
  id="sc-fund-plan">
    <mxCell style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f9f9f9;
           strokeColor=#cccccc;strokeWidth=1;fontSize=11;
           verticalAlign=middle;align=center;"
      vertex="1" parent="1">
        <mxGeometry x="40" y="1060" width="195" height="85" as="geometry"/>
    </mxCell>
</UserObject>
```

### 8. Asset Box — Deprioritized (Low Priority for Business Model)

Gray fill with scored-color border. Used for any asset that has a real score but isn't a priority for this business model. Three variants — one per score color:

**Deprioritized Red (e.g., Registered IP — missing but not urgent):**

```xml
<UserObject label="&lt;b style='font-size:12px;color:#999999;'&gt;Registered IP&lt;/b&gt;&lt;br/&gt;
         &lt;span style='font-size:10px;color:#999999;'&gt;Missing (Low Priority)&lt;/span&gt;&lt;br/&gt;
         &lt;span style='font-size:9px;color:#aaaaaa;'&gt;No trademarks filed&lt;/span&gt;"
  tooltip="No trademarks, copyrights, or patent protection. Low priority for current business model — inbound model doesn't depend on IP protection at this stage."
  id="sc-ip-registered">
    <mxCell style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f5f5;
           strokeColor=#FF6B6B;strokeWidth=2;fontSize=11;
           verticalAlign=middle;align=center;"
      vertex="1" parent="1">
        <mxGeometry x="580" y="145" width="260" height="85" as="geometry"/>
    </mxCell>
</UserObject>
```

**Deprioritized Yellow (e.g., Data — basic but not blocking growth):**

```xml
<UserObject label="&lt;b style='font-size:12px;color:#999999;'&gt;Data&lt;/b&gt;&lt;br/&gt;
         &lt;span style='font-size:10px;color:#999999;'&gt;Basic (Low Priority)&lt;/span&gt;&lt;br/&gt;
         &lt;span style='font-size:9px;color:#aaaaaa;'&gt;Email list, no CRM needed yet&lt;/span&gt;"
  tooltip="Email list exists with basic segmentation. No CRM or lead scoring — but inbound model works without it for now. Revisit when scaling past $50K/mo."
  id="sc-market-data">
    <mxCell style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f5f5;
           strokeColor=#FFD166;strokeWidth=2;fontSize=11;
           verticalAlign=middle;align=center;"
      vertex="1" parent="1">
        <mxGeometry x="580" y="415" width="260" height="85" as="geometry"/>
    </mxCell>
</UserObject>
```

**Deprioritized Green (rare — asset is strong but not strategic focus):**

```xml
<UserObject label="&lt;b style='font-size:12px;color:#999999;'&gt;[Asset Name]&lt;/b&gt;&lt;br/&gt;
         &lt;span style='font-size:10px;color:#999999;'&gt;Remarkable (Low Priority)&lt;/span&gt;&lt;br/&gt;
         &lt;span style='font-size:9px;color:#aaaaaa;'&gt;[Short description]&lt;/span&gt;"
  tooltip="[Full detail]. Strong asset but not a strategic priority for current growth phase."
  id="sc-[category]-[asset]">
    <mxCell style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f5f5;
           strokeColor=#90EE90;strokeWidth=3;fontSize=11;
           verticalAlign=middle;align=center;"
      vertex="1" parent="1">
        <mxGeometry x="[X]" y="[Y]" width="[W]" height="85" as="geometry"/>
    </mxCell>
</UserObject>
```

### 9. Culture Assets — Special Layout

Culture band has TWO rows: a full-width KPI box on top, then 3 sub-boxes below.

```xml
<!-- Band 6 Header -->
<mxCell id="sc-hdr-culture" value="CULTURE ASSETS"
  style="text;html=1;strokeColor=none;fillColor=#424242;align=left;
         verticalAlign=middle;fontSize=12;fontStyle=1;fontColor=#ffffff;
         spacingLeft=10;rounded=0;"
  vertex="1" parent="1">
    <mxGeometry x="30" y="710" width="840" height="28" as="geometry"/>
</mxCell>

<!-- Full-width KPI box (Key People of Influence) — 3 lines + tooltip -->
<mxCell id="sc-cult-kpi"
  value="&lt;b style='font-size:12px;'&gt;Key People of Influence&lt;/b&gt;&lt;br/&gt;
         &lt;span style='font-size:10px;color:#b8860b;'&gt;Basic&lt;/span&gt;&lt;br/&gt;
         &lt;span style='font-size:9px;color:#666666;'&gt;Building personal brand, not yet systematic&lt;/span&gt;"
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff8e6;
         strokeColor=#FFD166;strokeWidth=2;fontSize=11;
         verticalAlign=middle;align=center;"
  tooltip="Building personal brand through YouTube and content. Not yet systematic — no KPI program or ambassador network. Upgrade: Identify 5 industry contacts, create collaboration template, run 2 collaborations per quarter."
  vertex="1" parent="1">
    <mxGeometry x="40" y="845" width="810" height="70" as="geometry"/>
</mxCell>

<!-- Sub-box 1: Sales & Marketing — 3 lines + tooltip -->
<mxCell id="sc-cult-sales"
  value="&lt;b style='font-size:12px;'&gt;Sales &amp;amp; Marketing&lt;/b&gt;&lt;br/&gt;
         &lt;span style='font-size:10px;color:#c62828;'&gt;Missing&lt;/span&gt;&lt;br/&gt;
         &lt;span style='font-size:9px;color:#666666;'&gt;Solo, no sales team&lt;/span&gt;"
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff5f5;
         strokeColor=#FF6B6B;strokeWidth=2;fontSize=11;
         verticalAlign=middle;align=center;"
  tooltip="No dedicated sales or marketing team. All outreach, content, and sales handled by owner. Upgrade: Hire VA for content repurposing, then consider fractional marketing support."
  vertex="1" parent="1">
    <mxGeometry x="40" y="925" width="260" height="85" as="geometry"/>
</mxCell>

<!-- Sub-box 2: Mgmt & Admin — 3 lines + tooltip -->
<mxCell id="sc-cult-management"
  value="&lt;b style='font-size:12px;'&gt;Mgmt &amp;amp; Admin&lt;/b&gt;&lt;br/&gt;
         &lt;span style='font-size:10px;color:#c62828;'&gt;Missing&lt;/span&gt;&lt;br/&gt;
         &lt;span style='font-size:9px;color:#666666;'&gt;Solo, no admin team&lt;/span&gt;"
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff5f5;
         strokeColor=#FF6B6B;strokeWidth=2;fontSize=11;
         verticalAlign=middle;align=center;"
  tooltip="No management or admin staff. Bookkeeping, scheduling, and operations all handled by owner. Upgrade: Start with bookkeeper/virtual admin, then add ops manager as revenue grows."
  vertex="1" parent="1">
    <mxGeometry x="310" y="925" width="260" height="85" as="geometry"/>
</mxCell>

<!-- Sub-box 3: Technicians — 3 lines + tooltip -->
<mxCell id="sc-cult-technicians"
  value="&lt;b style='font-size:12px;'&gt;Technicians&lt;/b&gt;&lt;br/&gt;
         &lt;span style='font-size:10px;color:#c62828;'&gt;Missing&lt;/span&gt;&lt;br/&gt;
         &lt;span style='font-size:9px;color:#666666;'&gt;Solo, no delivery team&lt;/span&gt;"
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff5f5;
         strokeColor=#FF6B6B;strokeWidth=2;fontSize=11;
         verticalAlign=middle;align=center;"
  tooltip="No delivery specialists or technicians. All client work done by owner. Upgrade: Document delivery processes first (Operations Systems), then hire specialist contractors."
  vertex="1" parent="1">
    <mxGeometry x="580" y="925" width="260" height="85" as="geometry"/>
</mxCell>
```

### 9. Product Curve Line

Ascending dotted line underneath the 4 Product asset boxes. Represents the value ladder progression from free (Gifts) to highest-tier (P4C).

```xml
<mxCell id="sc-prod-curve" value=""
  style="curved=1;endArrow=none;html=1;strokeColor=#aaaaaa;
         strokeWidth=2;dashed=1;dashPattern=6 4;
         exitX=0;exitY=1;entryX=1;entryY=0;"
  edge="1" parent="1">
    <mxGeometry width="50" height="50" relative="1" as="geometry">
        <mxPoint x="40" y="640" as="sourcePoint"/>
        <mxPoint x="850" y="620" as="targetPoint"/>
        <Array as="points">
            <mxPoint x="40" y="643"/>
            <mxPoint x="245" y="637"/>
            <mxPoint x="450" y="629"/>
            <mxPoint x="850" y="620"/>
        </Array>
    </mxGeometry>
</mxCell>
```

### 11. Legend

Colored swatches with text labels. Sits below all bands. Includes deprioritized indicator.

```xml
<!-- Legend container -->
<mxCell id="sc-legend" value=""
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f5f5;
         strokeColor=#e9ecef;"
  vertex="1" parent="1">
    <mxGeometry x="30" y="1165" width="840" height="50" as="geometry"/>
</mxCell>

<!-- Legend title -->
<mxCell id="sc-legend-title" value="LEGEND:"
  style="text;html=1;strokeColor=none;fillColor=none;align=left;
         verticalAlign=middle;fontSize=10;fontStyle=1;fontColor=#333333;"
  vertex="1" parent="1">
    <mxGeometry x="42" y="1177" width="60" height="20" as="geometry"/>
</mxCell>

<!-- Green swatch -->
<mxCell id="sc-legend-green-swatch" value=""
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f0fff0;
         strokeColor=#90EE90;strokeWidth=3;"
  vertex="1" parent="1">
    <mxGeometry x="108" y="1179" width="16" height="16" as="geometry"/>
</mxCell>
<mxCell id="sc-legend-green" value="Remarkable"
  style="text;html=1;strokeColor=none;fillColor=none;align=left;
         fontSize=9;fontColor=#2e7d32;"
  vertex="1" parent="1">
    <mxGeometry x="128" y="1177" width="80" height="20" as="geometry"/>
</mxCell>

<!-- Yellow swatch -->
<mxCell id="sc-legend-yellow-swatch" value=""
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff8e6;
         strokeColor=#FFD166;strokeWidth=2;"
  vertex="1" parent="1">
    <mxGeometry x="218" y="1179" width="16" height="16" as="geometry"/>
</mxCell>
<mxCell id="sc-legend-yellow" value="Basic / Functional"
  style="text;html=1;strokeColor=none;fillColor=none;align=left;
         fontSize=9;fontColor=#b8860b;"
  vertex="1" parent="1">
    <mxGeometry x="238" y="1177" width="105" height="20" as="geometry"/>
</mxCell>

<!-- Red swatch -->
<mxCell id="sc-legend-red-swatch" value=""
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff5f5;
         strokeColor=#FF6B6B;strokeWidth=2;"
  vertex="1" parent="1">
    <mxGeometry x="353" y="1179" width="16" height="16" as="geometry"/>
</mxCell>
<mxCell id="sc-legend-red" value="Not Existing / Missing"
  style="text;html=1;strokeColor=none;fillColor=none;align=left;
         fontSize=9;fontColor=#c62828;"
  vertex="1" parent="1">
    <mxGeometry x="373" y="1177" width="130" height="20" as="geometry"/>
</mxCell>

<!-- Deprioritized swatch (gray fill + red border as example) -->
<mxCell id="sc-legend-depri-swatch" value=""
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f5f5;
         strokeColor=#FF6B6B;strokeWidth=2;"
  vertex="1" parent="1">
    <mxGeometry x="513" y="1179" width="16" height="16" as="geometry"/>
</mxCell>
<mxCell id="sc-legend-depri" value="Low Priority"
  style="text;html=1;strokeColor=none;fillColor=none;align=left;
         fontSize=9;fontColor=#999999;"
  vertex="1" parent="1">
    <mxGeometry x="533" y="1177" width="80" height="20" as="geometry"/>
</mxCell>
```

### 11. Back-to-Overview Link

Place at top-left on every detail page, per draw.io standards:

```xml
<mxCell id="sc-back" value="← Back to Overview"
  style="rounded=1;fillColor=#f5f5f5;strokeColor=#666666;fontSize=10;
         link=data:page/id,page-1;"
  vertex="1" parent="1">
    <mxGeometry x="30" y="1230" width="130" height="30" as="geometry"/>
</mxCell>
```

---

## The 24 Assets: Full Reference Table

| Band | Asset | ID Suffix | Notes |
|------|-------|-----------|-------|
| IP | Content | `sc-ip-content` | Written, video, audio IP |
| IP | Methodology | `sc-ip-methodology` | Proprietary frameworks/processes |
| IP | Registered IP | `sc-ip-registered` | Patents, trademarks, copyrights |
| Brand | Philosophy | `sc-brand-philosophy` | Beliefs, mission, POV |
| Brand | Identity | `sc-brand-identity` | Name, visual design, voice |
| Brand | Ambassadors | `sc-brand-ambassadors` | Testimonials, referrers, advocates |
| Market | Positioning | `sc-market-positioning` | Niche, offer clarity, differentiation |
| Market | Channels | `sc-market-channels` | Traffic sources, distribution |
| Market | Data | `sc-market-data` | Email list, audience data, analytics |
| Product | Gifts | `sc-prod-gifts` | Free value, lead magnets |
| Product | P4P (Pay for Proof) | `sc-prod-p4p` | Entry-level paid offer |
| Product | Core Product | `sc-prod-core` | Primary revenue driver |
| Product | P4C (Pay for Community) | `sc-prod-p4c` | Premium/ongoing relationship tier |
| Systems | Marketing & Sales | `sc-sys-marketing` | Lead gen, conversion systems |
| Systems | Mgmt & Admin | `sc-sys-management` | Finance, HR, compliance systems |
| Systems | Operations | `sc-sys-operations` | Delivery, fulfillment systems |
| Culture | Key People of Influence | `sc-cult-kpi` | Founders, leads — full-width row |
| Culture | Sales & Marketing | `sc-cult-sales` | Sales/marketing team capability |
| Culture | Mgmt & Admin | `sc-cult-management` | Operations/admin team capability |
| Culture | Technicians | `sc-cult-technicians` | Delivery/specialist team capability |
| Funding | Business Plan | `sc-fund-plan` | Strategic plan + financials |
| Funding | Valuation | `sc-fund-valuation` | Business valuation readiness |
| Funding | Structure | `sc-fund-structure` | Legal/ownership structure |
| Funding | Risk Mitigation | `sc-fund-risk` | Insurance, contracts, protections |

---

## Page Position in File

The scorecard page sits **after the System Connection Map page** and **before the Action Roadmap page**.

```xml
<mxfile host="app.diagrams.net">
    <diagram name="Business Overview" id="page-1">...</diagram>
    <!-- Process flow pages (page-2, page-3, ...) -->
    <diagram name="System Connection Map" id="page-sys">...</diagram>
    <diagram name="24 Assets Scorecard" id="page-assets">...</diagram>  <!-- ← HERE -->
    <diagram name="Action Roadmap" id="page-roadmap">...</diagram>
</mxfile>
```

The back link on this page links to `page-1` (Business Overview):
```xml
link=data:page/id,page-1
```

---

## Scoring Logic

When populating the scorecard from interview data, apply these rules:

| Score | Criteria |
|-------|----------|
| **Green (Remarkable)** | Asset exists, is differentiated, actively generates business value, would be hard to replicate |
| **Yellow (Basic/Functional)** | Asset exists in some form but is generic, underdeveloped, or not actively leveraged |
| **Red (Missing)** | Asset does not exist or is so underdeveloped it provides no competitive value |

**Leverage Score calculation:**
```
Active Assets = 24 - Deprioritized count
Leverage Score = (Count of Green assets in Active pool / Active Assets) × 100
Round to nearest whole percent
```

Deprioritized assets are EXCLUDED from both numerator and denominator. A solo coach who deprioritizes 6 team/funding assets gets scored on 18 assets — a more honest picture.

**Score summary string format:**
```
Leverage Score: [X]%  |  [G] Green  |  [Y] Yellow  |  [R] Red  |  [D] Deprioritized
```
Where G + Y + R + D = 24.

**Funding band default:** Mark as muted (Secondary) unless the business is actively seeking investment or is at scale (typically $1M+ ARR). When muted: use gray header, gray boxes, and "Becomes relevant at scale" note on each box. Do NOT score Funding boxes Green/Yellow/Red when muted — leave all as muted style.

---

## Generation Checklist

Before outputting a scorecard page:

**Structure:**
- [ ] Title includes business name
- [ ] Score summary shows Leverage Score %, Green count, Yellow count, Red count
- [ ] All 7 band headers present
- [ ] All 24 asset boxes present and positioned correctly

**Scoring:**
- [ ] Every non-muted box has exactly one of: Green fill / Yellow fill / Red fill / Deprioritized (gray fill + colored border)
- [ ] Score label inside box matches fill color (Remarkable / Basic / Missing)
- [ ] Deprioritized boxes add "(Low Priority)" after score label, use gray text colors
- [ ] Green boxes use strokeWidth=3, Yellow/Red use strokeWidth=2 (same for deprioritized variants)
- [ ] Every non-muted box has a 3rd line: short description in gray (9px)
- [ ] Every box uses `UserObject` wrapper with `tooltip` attribute (NOT tooltip on mxCell)
- [ ] Tooltip includes full scoring reason + upgrade steps (or why deprioritized)
- [ ] Leverage Score in header matches actual Green count ÷ Active assets (24 minus deprioritized count)

**Special Elements:**
- [ ] Culture band has full-width KPI box at y=845 PLUS 3 sub-boxes at y=925
- [ ] Product band has ascending dotted curve line below the 4 boxes
- [ ] Funding band uses muted style (gray) unless business is at scale
- [ ] Muted Funding boxes show italic "Becomes relevant at scale" sub-label

**IDs:**
- [ ] All elements use `sc-` prefix naming convention
- [ ] No duplicate IDs on the page
- [ ] Back link present, links to page-1

**Legend:**
- [ ] Legend shows all 4 visual states: Green, Yellow, Red, Low Priority (gray + colored border)
- [ ] Legend is at y=1165 inside a rounded container box

---

**Created:** 2026-02-26
**Purpose:** Standard reference for generating the 24 Assets Scorecard page in .drawio format
