# Business X-Ray

Source: business-x-ray/references/drawio-standards.md
MIME: text/markdown

# Draw.io Standards for Business X-Ray

**Technical reference for generating consistent, professional draw.io diagrams.**

---

## Annotation System (NEW)

**Apply annotations AFTER mapping the process (review pass).**

| Annotation | Border Style | Border Width | Color | Fill | Meaning |
|------------|--------------|--------------|-------|------|---------|
| **Bottleneck** | Solid | 3px | `#FF6B6B` | `#fff5f5` | Slowing things down |
| **Automate** | Dashed | 2px | `#FFA500` | `#fff8e6` | AI/tool could do this |
| **High Value** | Solid | 3px | `#90EE90` | `#f0fff0` | Human should keep doing |
| **Digital Asset** | Solid | 2px | `#9370DB` | `#f5f0ff` | Needs to be built |
| **Asset Upgrade** | Solid | 2px | `#8B4513` | `#fdf6f0` | From 24 Assets Assessment |
| **Normal** | Solid | 1px | `#666666` | `#f5f5f5` | Standard step |

### Annotation XML Examples

```xml
<!-- Bottleneck (Red, solid thick) -->
<mxCell value="Step Name" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff5f5;strokeColor=#FF6B6B;strokeWidth=3;fontSize=10;" vertex="1" parent="1">
    <mxGeometry x="100" y="100" width="100" height="50" as="geometry"/>
</mxCell>

<!-- Automate (Orange, dashed) -->
<mxCell value="Step Name" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff8e6;strokeColor=#FFA500;strokeWidth=2;dashed=1;fontSize=10;" vertex="1" parent="1">
    <mxGeometry x="100" y="100" width="100" height="50" as="geometry"/>
</mxCell>

<!-- High Value (Green, solid thick) -->
<mxCell value="Step Name" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f0fff0;strokeColor=#90EE90;strokeWidth=3;fontSize=10;" vertex="1" parent="1">
    <mxGeometry x="100" y="100" width="100" height="50" as="geometry"/>
</mxCell>

<!-- Digital Asset (Purple, solid) -->
<mxCell value="Step Name" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f0ff;strokeColor=#9370DB;strokeWidth=2;fontSize=10;" vertex="1" parent="1">
    <mxGeometry x="100" y="100" width="100" height="50" as="geometry"/>
</mxCell>

<!-- Asset Upgrade (Brown, solid) -->
<mxCell value="Step Name" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fdf6f0;strokeColor=#8B4513;strokeWidth=2;fontSize=10;" vertex="1" parent="1">
    <mxGeometry x="100" y="100" width="100" height="50" as="geometry"/>
</mxCell>
```

---

## Page Linking (Navigation)

**Use clickable links to navigate between pages within the .drawio file.**

### Link Syntax

```xml
<!-- Link to another page (by page ID) -->
<mxCell value="Content Creation"
  style="rounded=1;fillColor=#4DA6FF;fontColor=#ffffff;fontStyle=1;"
  vertex="1" parent="1">
  <mxGeometry x="100" y="100" width="120" height="40" as="geometry"/>
  <!-- Add link attribute -->
  <UserObject label="Content Creation" link="data:page/id,page-2" id="nav-content"/>
</mxCell>

<!-- Alternative: Using link in style -->
<mxCell value="Content Creation"
  style="rounded=1;fillColor=#4DA6FF;fontColor=#ffffff;link=data:page/id,page-2;"
  vertex="1" parent="1">
  <mxGeometry x="100" y="100" width="120" height="40" as="geometry"/>
</mxCell>
```

### Back to Overview Link

Add on every detail page:

```xml
<mxCell value="← Back to Overview"
  style="rounded=1;fillColor=#f5f5f5;strokeColor=#666666;fontSize=10;link=data:page/id,page-1;"
  vertex="1" parent="1">
  <mxGeometry x="40" y="20" width="120" height="30" as="geometry"/>
</mxCell>
```

### External URL Links

**Use HTML anchor tags inside the `value` attribute to make cell text link to external URLs.**

```xml
<!-- External URL (clickable text, dark background) -->
<mxCell id="cell-id" value="&lt;a href=&quot;https://example.com&quot; style=&quot;color:#ffffff&quot;&gt;Label Text&lt;/a&gt;"
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#4DA6FF;strokeColor=#3399FF;fontColor=#ffffff;fontSize=10;fontStyle=1;"
  parent="1" vertex="1">
    <mxGeometry x="100" y="100" width="140" height="35" as="geometry"/>
</mxCell>

<!-- External URL (clickable text, light background) -->
<mxCell id="cell-id" value="&lt;a href=&quot;https://example.com&quot; style=&quot;color:#333&quot;&gt;Label Text&lt;/a&gt;"
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#ffffff;strokeColor=#cccccc;fontSize=10;fontStyle=1;"
  parent="1" vertex="1">
    <mxGeometry x="100" y="100" width="140" height="35" as="geometry"/>
</mxCell>
```

### Combined: External URL + Internal Page Navigation

**Use when a cell should show a clickable URL AND navigate to another page on click.**

```xml
<UserObject label="&lt;a href=&quot;https://example.com&quot; style=&quot;color:#ffffff&quot;&gt;Product Name&lt;br&gt;$297&lt;/a&gt;" link="data:page/id,page-purchase" id="cell-id">
    <mxCell style="rounded=1;whiteSpace=wrap;html=1;fillColor=#4DA6FF;strokeColor=#3399FF;fontColor=#ffffff;fontSize=11;fontStyle=1;" parent="1" vertex="1">
        <mxGeometry x="100" y="100" width="180" height="40" as="geometry"/>
    </mxCell>
</UserObject>
```

### Column Sub-Labels

**Use small italic labels to create sub-groups within columns (e.g., "Primary"/"Secondary" in Traffic, "Free"/"Paid" in Products).**

```xml
<mxCell id="label-id" value="Primary" style="text;html=1;strokeColor=none;fillColor=none;align=left;verticalAlign=middle;fontSize=9;fontStyle=2;fontColor=#666666;" parent="1" vertex="1">
    <mxGeometry x="30" y="225" width="60" height="15" as="geometry"/>
</mxCell>
```

Common sub-labels:
- **Traffic:** "Primary" / "Secondary"
- **Products:** "Free" / "Paid"

---

## File Structure

All Business X-Ray outputs go in a **single .drawio file** with multiple pages:

```xml
<mxfile host="app.diagrams.net">
    <diagram name="Business Overview" id="page-1">...</diagram>  <!-- Business Map + Bow-Tie -->
    <diagram name="Content Creation" id="page-2">...</diagram>   <!-- Process swimlane -->
    <diagram name="Lead Conversion Flow" id="page-3">...</diagram>
    <diagram name="Fulfillment Flow" id="page-4">...</diagram>
    <diagram name="Operations Flow" id="page-5">...</diagram>
    <diagram name="System Connection Map" id="page-scm">...</diagram>
    <diagram name="24 Assets Scorecard" id="page-assets">...</diagram>
    <diagram name="90-Day Roadmap" id="page-6">...</diagram>
</mxfile>
```

**Why single file?**
- Works with Claude Web App (users copy XML, save as .drawio)
- No file system dependencies
- All pages linked together for drill-down navigation

---

## Color Coding System

### Business Map Column Colors

**Quick Reference:**
```
TRAFFIC:  🟢 Organic (Green)  |  🔵 Owned (Blue)  |  🔴 Paid (Red)
PRODUCTS: 🔵 Blue
FUNNELS:  🟣 Purple
Active = Darker color  |  Planned = Lighter color + dashed border
```

#### TRAFFIC Sources (3 Types)

| Type | Status | Fill Color | Stroke Color | Font Color | Example |
|------|--------|------------|--------------|------------|---------|
| **Organic** | Active | `#90EE90` | `#82b366` | `#1a1a2e` | YouTube, Substack, SEO |
| **Organic** | Planned | `#d5e8d4` | `#82b366` | `#666666` | Podcast (future) |
| **Owned** | Active | `#4DA6FF` | `#3399FF` | `#ffffff` | Email List, SMS List |
| **Owned** | Planned | `#b3d9ff` | `#3399FF` | `#1a1a2e` | Community (future) |
| **Paid** | Active | `#FF6B6B` | `#FF4444` | `#ffffff` | Facebook Ads, Google Ads |
| **Paid** | Planned | `#ffb3b3` | `#FF4444` | `#1a1a2e` | YouTube Ads (future) |

#### CONVERTERS

| Status | Fill Color | Stroke Color | Font Color | Example |
|--------|------------|--------------|------------|---------|
| All | `#ffffff` | `#cccccc` | `#333333` | Landing pages, signup pages, product pages |

#### PRODUCTS (All Blue)

| Status | Fill Color | Stroke Color | Font Color | Border | Example |
|--------|------------|--------------|------------|--------|---------|
| Established | `#4DA6FF` | `#3399FF` | `#ffffff` | Solid | Business X-Ray Skill |
| Planned | `#B3D9FF` | `#4DA6FF` | `#333333` | `dashed=1` | DWY Partnership |

#### FUNNELS (All Purple — 1:1 with Products)

**Every product MUST have a corresponding funnel cell.** The funnel is the digital selling asset used to close the sale (landing page, VSL, Gamma doc, sales call page, etc.).

| Status | Fill Color | Stroke Color | Font Color | Border | Example |
|--------|------------|--------------|------------|--------|---------|
| Established | `#9370DB` | `#7B68EE` | `#ffffff` | Solid | Framer Landing Page |
| Planned | `#D8BFD8` | `#9370DB` | `#333333` | `dashed=1` | Community Offer |

### Annotation Colors (Process Flows)

| Status | Fill Color | Stroke Color | Font Color | Use For |
|--------|------------|--------------|------------|---------|
| Bottleneck | `#FF6B6B` | `#FF4444` | `#ffffff` | Steps that slow things down |
| AI Opportunity | `#4DA6FF` | `#3399FF` | `#ffffff` | Steps that can be automated |
| Value-Add | `#90EE90` | `#82b366` | `#2d6a4f` | Strategic, high-leverage work |
| Decision | `#FFD166` | `#f4a261` | `#1a1a2e` | Choice points in process |
| Neutral | `#f5f5f5` | `#666666` | `#333333` | Standard process steps |
| Digital Asset | `#9370DB` | `#7B68EE` | `#ffffff` | SOPs, templates to build |
| Complete/Done | `#b2f2bb` | `#2f9e44` | `#1a1a2e` | Completed outputs |

### Swimlane Colors

| Lane Type | Fill Color | Stroke Color | Use For |
|-----------|------------|--------------|---------|
| User/Owner | `#dae8fc` | `#6c8ebf` | Actions done by business owner |
| AI/Automation | `#ffe6cc` | `#d79b00` | Automated steps |
| Team/VA | `#e1d5e7` | `#9673a6` | Delegated to team |
| Output/Result | `#f8cecc` | `#b85450` | Final deliverables |
| Customer | `#d5e8d4` | `#82b366` | Customer-facing touchpoints |

### Legend Standard

**Every Business Map must include a legend below the map.** Include these items:

| Swatch | Label | Color |
|--------|-------|-------|
| Green | Organic Traffic | `#90EE90` |
| Blue | Owned Traffic / Products | `#4DA6FF` |
| Red | Paid Traffic | `#FF6B6B` |
| White | Converters | `#ffffff` |
| Purple | Funnels | `#9370DB` |
| Light + dashed | Planned | `#B3D9FF` or `#D8BFD8` |

---

## Shape Standards

### Process Step (Rounded Rectangle)
```xml
<mxCell value="Step Name" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#666666;fontSize=10;" vertex="1" parent="1">
    <mxGeometry x="100" y="100" width="100" height="50" as="geometry"/>
</mxCell>
```

### Decision Point (Diamond)
```xml
<mxCell value="Decision?" style="rhombus;whiteSpace=wrap;html=1;fillColor=#FFD166;strokeColor=#f4a261;fontSize=9;" vertex="1" parent="1">
    <mxGeometry x="100" y="100" width="60" height="45" as="geometry"/>
</mxCell>
```

### Start/End (Ellipse)
```xml
<mxCell value="START" style="ellipse;whiteSpace=wrap;html=1;fillColor=#38b000;strokeColor=#2d6a4f;fontColor=#ffffff;fontSize=10;fontStyle=1;" vertex="1" parent="1">
    <mxGeometry x="100" y="100" width="60" height="35" as="geometry"/>
</mxCell>
```

### Swimlane Pool (Native stackLayout - PREFERRED)

**Use draw.io's native swimlane with auto-stacking lanes:**

```xml
<!-- Pool with auto-stacking lanes -->
<mxCell id="pool-1" value="Process Name" style="swimlane;childLayout=stackLayout;resizeParent=1;resizeParentMax=0;horizontal=0;startSize=20;horizontalStack=0;html=1;fillColor=#f5f5f5;strokeColor=#666666;fontStyle=1;" vertex="1" parent="1">
    <mxGeometry x="40" y="40" width="800" height="400" as="geometry"/>
</mxCell>

<!-- Lanes auto-stack vertically - no manual y-coordinates needed! -->
<mxCell id="lane-1" value="Lane 1" style="swimlane;startSize=20;horizontal=0;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="pool-1">
    <mxGeometry x="20" width="780" height="100" as="geometry"/>
</mxCell>

<mxCell id="lane-2" value="Lane 2" style="swimlane;startSize=20;horizontal=0;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;" vertex="1" parent="pool-1">
    <mxGeometry x="20" y="100" width="780" height="100" as="geometry"/>
</mxCell>

<mxCell id="lane-3" value="Lane 3" style="swimlane;startSize=20;horizontal=0;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="pool-1">
    <mxGeometry x="20" y="200" width="780" height="100" as="geometry"/>
</mxCell>
```

**Key properties:**
- `childLayout=stackLayout` - Lanes auto-stack vertically
- `resizeParent=1` - Pool auto-resizes when lanes change
- `startSize=20` - Compact lane label (vs 100 for wide labels)
- `horizontal=0` - Horizontal swimlane (lanes stack top-to-bottom)

**Benefits over manual positioning:**
- No manual y-coordinate math
- Adding/removing lanes doesn't break layout
- Resize handles work properly
- Matches draw.io UI behavior

### Swimlane Lane (Legacy - for reference only)
```xml
<mxCell value="Lane Name" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;startSize=100;fillColor=#dae8fc;strokeColor=#6c8ebf;fontStyle=1;" vertex="1" parent="pool-id">
    <mxGeometry x="30" width="730" height="130" as="geometry"/>
</mxCell>
```

### Connector Arrow
```xml
<mxCell style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;strokeColor=#666666;strokeWidth=2;" edge="1" parent="1" source="source-id" target="target-id">
    <mxGeometry relative="1" as="geometry"/>
</mxCell>
```

### Expansion Link (Dashed)
```xml
<mxCell value="Expands to" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;strokeColor=#d79b00;strokeWidth=3;dashed=1;fontStyle=1;labelBackgroundColor=#ffffff;" edge="1" parent="1" source="source-id" target="target-id">
    <mxGeometry relative="1" as="geometry"/>
</mxCell>
```

---

## Page Templates

### Page 1: Business Overview (Business Map + Bow-Tie)

Layout: 7-column Business Map on top, Bow-Tie funnel below

**For Bow-Tie Funnel:** See `references/bowtie-funnel.md` for complete XML patterns and grid structure.

> ⚠️ **CRITICAL:** Bow-Tie is a 7-COLUMN GRID, not a flowchart. Each activity = separate rectangle.

Standard dimensions:
- Page width: ~1300px
- Business Map section: y=40, height ~400px
- Bow-Tie section: y=470, height ~350px (includes phase banners, headers, activity boxes, metrics)
- Column headers: 100-150px wide, 30px tall
- Content boxes: 100px wide, 40-50px tall
- Start x: 40

### Pages 2+: Process Flow Swimlanes

Layout: Horizontal swimlanes, left-to-right flow

```
┌─────────────────────────────────────────────────────────┐
│ PROCESS NAME                                             │
├─────────┬───────────────────────────────────────────────┤
│ Owner   │ [Step] → [Step] → [Decision] → [Step]        │
├─────────┼───────────────────────────────────────────────┤
│ AI      │           [Step] → [Step]                     │
├─────────┼───────────────────────────────────────────────┤
│ Output  │                              [Result]         │
└─────────┴───────────────────────────────────────────────┘
```

Standard dimensions:
- Pool width: dynamic — `label_width + (num_columns * 180) + 40` (min 880px)
- Lane height: 100-150px each (increase to 180px if a lane has 2 stacked boxes)
- Step boxes: 120px wide, 50px tall
- Horizontal gap between boxes: 60px minimum
- Start x: 40, y: 40

> **CRITICAL: Read the Swimlane Placement Algorithm section below BEFORE generating any swimlane XML.** Element placement determines arrow quality. Place elements to serve the arrows, not the other way around.

---

## Swimlane Placement Algorithm (MANDATORY)

**This section controls how elements are positioned inside swimlanes. Follow this BEFORE writing any XML.**

### Why This Matters

Clean swimlanes vs messy swimlanes comes down to ONE thing: **where you place the boxes**. If boxes are placed well, arrows route themselves. If boxes are crammed into columns, arrows tangle.

**What humans do naturally:** Place the next element wherever the arrow can reach it cleanly — even if that means shifting it right, skipping a column, or leaving white space.

**What AI does wrong:** Cram all elements into rigid phase columns, stack them vertically, then hope draw.io routes arrows around the mess.

### The Core Rules

**Rule 1: One element per slot.** A "slot" = one lane × one X-position. Never stack two elements vertically in the same phase column. If you have 2 activities in the same lane in the same phase, spread them horizontally — give each its own X-position.

**Rule 2: Arrows go RIGHT or DOWN only — NEVER UP, NEVER LEFT, NEVER through another element.** Before placing any element, check: "Will the arrow from the previous element reach this one without crossing through another box?" If no, move this element right until the path is clear. The only exception: cross-lane return arrows (e.g., AI lane back to Owner lane) may go UP as an L-shape when the target is to the RIGHT of the source.

**Rule 3: Down-arrows are DIRECT.** An arrow should only go downward when the target element is directly below the source (same or very close X-position). If you need to go down AND right, offset the target element to the right first so the arrow can make a clean L-shape.

**Rule 4: Leave horizontal space between phases.** The gap between the last element of Phase 1 and the first element of Phase 2 should be at least 60px. This gives arrows room to route vertically in the gap without crossing elements.

**Rule 5: Wider is better than taller.** When in doubt, add horizontal space. A swimlane that's 1200px wide with clean arrows is better than one that's 760px wide with spaghetti.

**Rule 6: Fan-out targets go on DIFFERENT rows, converge target goes RIGHT of both.** When one element fans out to two targets that later converge into a single element:
- Place the first fan-out target on Row 1 (same row as source)
- Place the second fan-out target on Row 2 (shifted RIGHT of the first)
- Place the converge target on Row 2, to the RIGHT of BOTH fan-out targets
- This ensures both arrows into the converge target go RIGHT — never UP

```
GOOD (fan-out → converge, all arrows RIGHT or DOWN):

AI Row1: [Edit Video] ──exitY=0.25→ [CTA Plays]
                       ──exitY=0.75→                ↘ (RIGHT-DOWN)
AI Row2:                              [Desc Link] → [Substack Captures]
                                                     ↑ both arrive from LEFT

BAD (converge target on Row 1 forces upward arrow):

AI Row1: [Edit Video] → [CTA Plays] → [Substack Captures]
                                              ↑ UPWARD!
AI Row2:                 [Desc Link] ─────────┘
```

**Rule 7: In multi-row lanes, every element gets its own X — even across rows.** Two elements at the same X but different Y values create a vertical traffic jam. Arrows passing through that X-column will cross one of them. Stagger everything horizontally.

### The 5-Step Placement Process

Follow this process every time you generate a swimlane:

#### Step 1: Build the Connection Map

Before touching any coordinates, list every element and its connections:

```
ELEMENT LIST (Lead Gen example):
1. Ideate Content Topics (Owner) → Record YouTube Videos (Owner)
2. Record YouTube Videos (Owner) → Edit Video (AI)
3. Ideate Content Topics (Owner) → Post Community Tab Content (Owner)
4. Edit Video (AI) → Mid-Video CTA Plays (AI)
5. Edit Video (AI) → Description Link (AI)
6. ... etc.
```

#### Step 2: Find the Main Flow Path

Identify the longest path from start to finish. This becomes the "spine" of your diagram — it gets the prime real estate (horizontally across the middle).

```
MAIN PATH (bold line through the diagram):
Ideate → Record → Edit Video → CTA Plays → Write Newsletter → Newsletter CTAs → Qualification
```

#### Step 3: Place the Main Path First

Walk the main path left-to-right. Each time the path switches lanes, offset the next element to the right:

```
PLACEMENT RULES FOR MAIN PATH:
- Same lane, next step:      X += 180  (box width + gap)
- Different lane, next step:  X += 140  (slightly less, creates diagonal)
- Center each element vertically in its lane
```

```
AFTER PLACING MAIN PATH:

Owner │ [Ideate]──────→[Record]─────────────────────→[Write Newsletter]
      │    x=100          x=280                            x=820
──────┤                      ↘
AI    │                   [Edit Video]→[CTA Plays]                    →[Newsletter CTAs]
      │                      x=420       x=600                          x=1000
──────┤
Output│                                                                         →[Qualification]
      │                                                                            x=1180
```

#### Step 4: Place Branch Elements

For each element NOT on the main path, find where it connects and place it:

- **Same lane as its source, parallel activity:** Place at same X but use the Y space above or below the main path element. Only do this if there's room AND no arrow from this box would cross the main path.
- **Different lane:** Place at an X position between its source and its target, in the correct lane.

**THE KEY TEST:** After placing each branch element, trace every arrow to/from it with your finger. Does it cross through any other box? If yes → move this element right until clear.

```
ADDING BRANCHES:

Owner │ [Ideate]──→[Record]──→[Post Community Tab]──→[Write Newsletter]
      │    x=100     x=280          x=460                  x=820
──────┤                 ↘
AI    │ [Research]→[Edit Video]→[CTA]→[Desc Link]     [Claude Draft]→[Substack]→[CTAs]→[Gamma Doc]
      │   x=100      x=420     x=600   x=600(below)    x=640          x=820     x=1000   x=1000
──────┤                                              [Substack Email]→[Welcome]
      │                                                  x=460          x=640
──────┤
Output│                                [New Sub]──────→[Warm Reader]──────→[Ready to Buy]
      │                                  x=460            x=820              x=1180
```

#### Step 5: The Arrow Audit

Go through EVERY arrow and check these three things:

1. **Does it cross through another element?** → Move the target right
2. **Does it run parallel and overlap another arrow?** → Offset one arrow's source/target anchor (use `exitY=0.25` vs `exitY=0.75`)
3. **Is it a long diagonal?** → Add a waypoint to make it an L-shape (horizontal then vertical, or vertical then horizontal)

### Visual Patterns: Good vs Bad

#### Pattern: Cross-Lane Handoff

```
BAD (arrow crosses through "Post Community"):

Owner │ [Ideate]→[Record]→[Post Community]
      │            │  ↑ arrow crosses through Post!
──────┤            ↓
AI    │         [Edit Video]

GOOD (target offset right, arrow has clear path):

Owner │ [Ideate]→[Record]────────→[Post Community]
      │             ↘
──────┤              ↘             (clear vertical gap)
AI    │           [Edit Video]
```

#### Pattern: Fan-Out (One Source, Multiple Targets)

```
BAD (all targets at same X, arrows overlap):

Owner │ [Record]──┐
──────┤           ├──→[Edit Video]
AI    │           ├──→[Description]
──────┤           └──→[CTA Overlay]
Output│

GOOD (targets staggered right, each arrow has its own path):

Owner │ [Record]──────┐
──────┤               ↘
AI    │            [Edit Video]───→[Description]
──────┤                                  ↘
Output│                              [CTA Overlay]
```

#### Pattern: Parallel Activities (Same Lane, Same Phase)

```
BAD (stacked vertically, arrows from both go right and cross):

Owner │ [Ideate]
      │ [Record]     ← arrows from both go right and tangle
──────┤

GOOD (side by side, sequential connection):

Owner │ [Ideate]───→[Record]
──────┤

OR if truly parallel (both feed same target):

Owner │ [Ideate]─────────→ ...
      │         ↘
──────┤          [Record]→ ...
AI    │
```

#### Pattern: Converging Arrows (Multiple Sources, One Target)

```
BAD (all arrows arrive at same point):

AI    │ [Claude Draft]──┐
      │ [Substack]──────┤→[Final Output]    ← arrows pile up on left side
──────┤                 │
Output│ [Review]────────┘

GOOD (targets arrive from different sides/anchors):

AI    │ [Claude Draft]──→[Substack Delivers]
──────┤                          ↘
Output│                    [Final Output]←──[Review]
```

### Spacing Reference

| Measurement | Value | When |
|-------------|-------|------|
| Same-lane next step | X += 180px | Normal forward flow |
| Cross-lane next step | X += 140px | Handoff to different actor |
| Phase gap (between phase columns) | 60px clear | Always |
| Min box horizontal gap | 60px | Between any two boxes |
| Lane height (1 box) | 100-120px | Standard |
| Lane height (2 boxes) | 160-180px | Max 2 stacked — beyond this, expand to sub-process |
| Max elements per lane per phase | 2 | Hard limit — use Level 2 expansion for more |
| Pool width | Dynamic | `80 + (columns * 180) + 40`, min 880px |

### Arrow Style

All swimlane arrows use this base style:

```xml
<mxCell style="edgeStyle=orthogonalEdgeStyle;rounded=1;orthogonalLoop=1;jettySize=auto;html=1;strokeColor=#666666;strokeWidth=2;" edge="1" parent="pool-id" source="step-a" target="step-b">
    <mxGeometry relative="1" as="geometry"/>
</mxCell>
```

**Key:** `rounded=1` (softens bends), `orthogonalEdgeStyle` (right-angle routing), and `jettySize=auto` (smart spacing from box edges).

**Exit/Entry anchors for cross-lane arrows:**
- Going RIGHT and DOWN: `exitX=1;exitY=0.5` (exit right) → `entryX=0;entryY=0.5` (enter left)
- Going straight DOWN: `exitX=0.5;exitY=1` (exit bottom) → `entryX=0.5;entryY=0` (enter top)
- If two arrows exit same box: use `exitY=0.25` for one and `exitY=0.75` for the other

**Backward arrows (loops/retries):** Route below boxes using `exitX=0.5;exitY=1;entryX=0.5;entryY=1` with explicit waypoints. Use `dashed=1` style to distinguish from forward flow.

### Quality Checklist (Arrows)

Before finalizing any swimlane:

- [ ] No arrow passes through any element
- [ ] No two arrows overlap for more than 20px
- [ ] Every down-arrow connects to an element directly below (close X)
- [ ] Every cross-lane arrow makes a clean L-shape, not a diagonal
- [ ] Fan-out targets are staggered (not all at same X)
- [ ] Max 2 elements stacked per lane per phase
- [ ] Pool width is wide enough — white space is OK

### Page 6: Action Roadmap

Layout: Simple prioritized checklist (single column, vertical list)

```
┌─────────────────────────────────────────────────────────────┐
│                    ACTION ROADMAP                            │
│                                                              │
│  DO FIRST                                                    │
│  ────────                                                    │
│  ☐ 🔴 Fix content bottleneck                                │
│     Create batch workflow for weekly content                 │
│                                                              │
│  ☐ 🟠 Automate email follow-ups                             │
│     Set up ConvertKit sequences                              │
│                                                              │
│  DO NEXT                                                     │
│  ────────                                                    │
│  ☐ 🟣 Build lead magnet landing page                        │
│     Create opt-in page with Carrd or similar                 │
│                                                              │
│  DO LATER                                                    │
│  ────────                                                    │
│  ☐ 🟠 Set up social scheduling                              │
│     Batch create + schedule with Buffer/Later                │
└─────────────────────────────────────────────────────────────┘
```

Standard dimensions:
- Page width: 400px
- Section header: fontSize=14, fontStyle=1 (bold)
- Task title: fontSize=11, with checkbox prefix
- Task description: fontSize=9, indented, gray text
- Spacing: 60px between items, 80px between sections

---

## ID Naming Conventions

Use consistent, descriptive IDs for all elements:

```
Page 1 (Business Overview):
- p1-header-traffic, p1-header-converters, etc.
- p1-traffic-1, p1-traffic-2, etc.
- p1-income-title, p1-income-r1c1, etc.

Page 1 (Bow-Tie section):
- p1-bowtie-title
- p1-bt-awareness, p1-bt-nurture, p1-bt-consider, p1-bt-commit
- p1-bt-onboard, p1-bt-launch, p1-bt-results
- p1-bt-arrow-1, p1-bt-arrow-2, etc.

Page 2+ (Process Flows):
- p2-pool, p2-lane-owner, p2-lane-ai, p2-lane-output
- p2-step-1, p2-step-2, p2-decision-1
- p2-arrow-1, p2-arrow-2

Last Page (Roadmap):
- p6-title, p6-section-first, p6-section-next, p6-section-later
- p6-task-1, p6-task-2, p6-task-3
- p6-desc-1, p6-desc-2, p6-desc-3
```

---

## Multi-Level Drill-Down Pattern

To link a high-level step to a detailed sub-process:

1. **On the high-level page:** Add an expansion arrow pointing off-page
```xml
<mxCell value="Expands to Page 3" style="...dashed=1..." edge="1" source="step-id">
    <mxGeometry relative="1" as="geometry">
        <mxPoint x="800" y="200" as="targetPoint"/>
    </mxGeometry>
</mxCell>
```

2. **Use consistent naming:**
   - High-level: "Content Creation"
   - Detail page name: "Content Creation - Detail"
   - Sub-detail: "Content Creation - Thread Writing"

3. **Add "Back to Overview" link** on detail pages

---

## Table Patterns (For MATH Section)

### Income Table
```xml
<!-- Title Row -->
<mxCell value="INCOME" style="text;fillColor=#2d6a4f;fontColor=#ffffff;fontStyle=1;..." />

<!-- Header Row -->
<mxCell value="Product" style="text;fillColor=#e8f5e9;fontStyle=1;..." />
<mxCell value="Price" style="text;fillColor=#e8f5e9;fontStyle=1;..." />
<mxCell value="Cap" style="text;fillColor=#e8f5e9;fontStyle=1;..." />
<mxCell value="$/Month" style="text;fillColor=#e8f5e9;fontStyle=1;..." />
<mxCell value="$/Year" style="text;fillColor=#e8f5e9;fontStyle=1;..." />

<!-- Data Rows (alternating white/#f9f9f9) -->
<mxCell value="Product Name" style="text;fillColor=#ffffff;align=left;..." />
<mxCell value="$X" style="text;fillColor=#ffffff;align=center;..." />
...

<!-- Total Row -->
<mxCell value="TOTAL" style="text;fillColor=#2d6a4f;fontColor=#ffffff;fontStyle=1;..." />
```

### Expense Table
Same pattern but with:
- Title: `fillColor=#c62828` (red)
- Headers: `fillColor=#ffebee` (light red)

---

## Legend Box Pattern

Include on process flow pages:

```xml
<mxCell value="" style="rounded=1;fillColor=#f5f5f5;strokeColor=#e9ecef;" vertex="1">
    <mxGeometry x="540" y="530" width="170" height="100" as="geometry"/>
</mxCell>
<mxCell value="LEGEND" style="text;fontStyle=1;fontSize=10;" />
<!-- Color swatches with labels -->
<mxCell value="" style="ellipse;fillColor=#FF6B6B;" /> <!-- Bottleneck -->
<mxCell value="" style="rounded=1;fillColor=#4DA6FF;" /> <!-- AI Opportunity -->
<mxCell value="" style="rhombus;fillColor=#FFD166;" /> <!-- Decision -->
```

---

## XML Template (Complete File Structure)

```xml
<mxfile host="app.diagrams.net">
    <diagram name="Business Overview" id="page-1">
        <mxGraphModel dx="1260" dy="1067" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="0" pageScale="1" pageWidth="1600" pageHeight="900" math="0" shadow="0">
            <root>
                <mxCell id="0"/>
                <mxCell id="1" parent="0"/>
                <!-- Business Overview content here -->
            </root>
        </mxGraphModel>
    </diagram>
    <diagram name="Lead Generation Flow" id="page-2">
        <mxGraphModel ...>
            <root>
                <mxCell id="0"/>
                <mxCell id="1" parent="0"/>
                <!-- Lead Gen swimlane content here -->
            </root>
        </mxGraphModel>
    </diagram>
    <!-- Additional pages... -->
</mxfile>
```

---

## Quality Checklist

Before outputting any diagram:

- [ ] All elements have unique, descriptive IDs
- [ ] Colors follow the standard (bottleneck=red, AI=blue, etc.)
- [ ] Swimlanes have consistent heights
- [ ] Arrows connect properly (source/target IDs exist)
- [ ] Text is readable (fontSize >= 8)
- [ ] Page names are descriptive
- [ ] Expansion links use dashed style
- [ ] Tables have proper alignment
