# Business X-Ray

Source: business-x-ray/references/system-connection-template.md
MIME: text/markdown

# System Connection Map — Draw.io Template

**XML patterns for generating hub-and-spoke network diagrams showing tool connections.**

---

## Page Structure

The System Connection Map is a single .drawio page added between the last process swimlane and the Action Roadmap.

```xml
<diagram name="System Connection Map" id="page-scm">
    <mxGraphModel dx="1260" dy="1067" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="0" pageScale="1" pageWidth="1600" pageHeight="900" math="0" shadow="0">
        <root>
            <mxCell id="0"/>
            <mxCell id="1" parent="0"/>
            <!-- Title -->
            <!-- Category zones -->
            <!-- Tool nodes -->
            <!-- Connection edges -->
            <!-- Opportunity badges -->
            <!-- Legend -->
            <!-- Stats box -->
        </root>
    </mxGraphModel>
</diagram>
```

---

## Layout Dimensions

| Element | Position | Size |
|---------|----------|------|
| **Title** | x=40, y=20 | 700x40 |
| **Zone 1 (Content)** | x=40, y=80 | 500x180 |
| **Zone 2 (Sales)** | x=40, y=290 | 500x180 |
| **Zone 3 (Delivery)** | x=40, y=500 | 500x180 |
| **Zone 4 (Admin)** | x=40, y=710 | 500x180 |
| **Legend** | x=600, y=80 | 200x160 |
| **Opportunities** | x=600, y=270 | 350xAuto |
| **Stats** | x=600, y=700 | 200x80 |

**Adjust zone count and heights based on actual categories.** Standard 4-zone layout shown. If only 3 categories, distribute space evenly.

---

## Title

```xml
<mxCell id="scm-title" value="SYSTEM CONNECTION MAP: [Business Name]" style="text;html=1;fontSize=16;fontStyle=1;fontColor=#1a1a2e;align=left;verticalAlign=middle;" vertex="1" parent="1">
    <mxGeometry x="40" y="20" width="700" height="40" as="geometry"/>
</mxCell>

<mxCell id="scm-subtitle" value="How your tools and systems connect across your business" style="text;html=1;fontSize=10;fontColor=#666666;align=left;verticalAlign=top;" vertex="1" parent="1">
    <mxGeometry x="40" y="50" width="500" height="20" as="geometry"/>
</mxCell>
```

---

## Category Zones

Zones group tools by business function. Tools sit inside their primary zone; connections cross zones freely.

```xml
<!-- Content & Marketing zone -->
<mxCell id="scm-zone-content" value="CONTENT &amp; MARKETING" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f0f9f0;strokeColor=#82b366;strokeWidth=1;dashed=1;fontSize=11;fontStyle=1;fontColor=#2d6a4f;verticalAlign=top;align=left;spacingTop=5;spacingLeft=10;" vertex="1" parent="1">
    <mxGeometry x="40" y="80" width="500" height="180" as="geometry"/>
</mxCell>

<!-- Sales zone -->
<mxCell id="scm-zone-sales" value="SALES" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#e8f0fe;strokeColor=#6c8ebf;strokeWidth=1;dashed=1;fontSize=11;fontStyle=1;fontColor=#1a56db;verticalAlign=top;align=left;spacingTop=5;spacingLeft=10;" vertex="1" parent="1">
    <mxGeometry x="40" y="290" width="500" height="180" as="geometry"/>
</mxCell>

<!-- Delivery zone -->
<mxCell id="scm-zone-delivery" value="DELIVERY" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fef3e2;strokeColor=#d79b00;strokeWidth=1;dashed=1;fontSize=11;fontStyle=1;fontColor=#8a6914;verticalAlign=top;align=left;spacingTop=5;spacingLeft=10;" vertex="1" parent="1">
    <mxGeometry x="40" y="500" width="500" height="180" as="geometry"/>
</mxCell>

<!-- Admin zone -->
<mxCell id="scm-zone-admin" value="ADMIN / OPERATIONS" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f0ff;strokeColor=#9673a6;strokeWidth=1;dashed=1;fontSize=11;fontStyle=1;fontColor=#5b3a8c;verticalAlign=top;align=left;spacingTop=5;spacingLeft=10;" vertex="1" parent="1">
    <mxGeometry x="40" y="710" width="500" height="180" as="geometry"/>
</mxCell>
```

### Zone Color Reference

| Zone | Fill | Stroke | Font |
|------|------|--------|------|
| Content & Marketing | `#f0f9f0` | `#82b366` | `#2d6a4f` |
| Sales | `#e8f0fe` | `#6c8ebf` | `#1a56db` |
| Delivery | `#fef3e2` | `#d79b00` | `#8a6914` |
| Admin / Operations | `#f5f0ff` | `#9673a6` | `#5b3a8c` |

---

## Tool Nodes

### Standard Tool (1-2 connections)

```xml
<mxCell id="scm-node-[toolname]" value="[Tool Name]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#666666;strokeWidth=1;fontSize=10;fontStyle=1;shadow=1;" vertex="1" parent="1">
    <mxGeometry x="[x]" y="[y]" width="110" height="40" as="geometry"/>
</mxCell>
```

### Hub Tool (3+ connections — well-integrated)

```xml
<mxCell id="scm-node-[toolname]" value="[Tool Name]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f0fff0;strokeColor=#82b366;strokeWidth=3;fontSize=10;fontStyle=1;shadow=1;" vertex="1" parent="1">
    <mxGeometry x="[x]" y="[y]" width="110" height="40" as="geometry"/>
</mxCell>
```

### Disconnected Tool (0 connections — isolated)

```xml
<mxCell id="scm-node-[toolname]" value="[Tool Name]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff5f5;strokeColor=#FF6B6B;strokeWidth=3;fontSize=10;fontStyle=1;shadow=1;" vertex="1" parent="1">
    <mxGeometry x="[x]" y="[y]" width="110" height="40" as="geometry"/>
</mxCell>
```

### Redundant Tool (same job as another — consolidation candidate)

```xml
<mxCell id="scm-node-[toolname]" value="[Tool Name]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff8e6;strokeColor=#FFA500;strokeWidth=2;dashed=1;fontSize=10;fontStyle=1;shadow=1;" vertex="1" parent="1">
    <mxGeometry x="[x]" y="[y]" width="110" height="40" as="geometry"/>
</mxCell>
```

### Multi-Zone Tool (appears in multiple categories)

Place in primary zone. Add a small label below showing secondary uses:

```xml
<!-- Main node in primary zone -->
<mxCell id="scm-node-notion" value="Notion" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f0fff0;strokeColor=#82b366;strokeWidth=3;fontSize=10;fontStyle=1;shadow=1;" vertex="1" parent="1">
    <mxGeometry x="200" y="320" width="110" height="40" as="geometry"/>
</mxCell>

<!-- Secondary use label -->
<mxCell id="scm-node-notion-label" value="also: Content Calendar, Client Portal" style="text;html=1;fontSize=8;fontColor=#888888;align=center;fontStyle=2;" vertex="1" parent="1">
    <mxGeometry x="185" y="360" width="140" height="16" as="geometry"/>
</mxCell>
```

---

## Connection Edges

### Automated Connection (green solid — API/native)

```xml
<mxCell id="scm-edge-[n]" value="API" style="edgeStyle=orthogonalEdgeStyle;rounded=1;orthogonalLoop=1;html=1;strokeColor=#82b366;strokeWidth=2;fontSize=8;fontStyle=2;fontColor=#82b366;" edge="1" parent="1" source="scm-node-[source]" target="scm-node-[target]">
    <mxGeometry relative="1" as="geometry"/>
</mxCell>
```

### Manual Bridge (orange dashed — human copy-paste/export)

```xml
<mxCell id="scm-edge-[n]" value="manual" style="edgeStyle=orthogonalEdgeStyle;rounded=1;orthogonalLoop=1;html=1;strokeColor=#FFA500;strokeWidth=2;dashed=1;fontSize=8;fontStyle=2;fontColor=#FFA500;" edge="1" parent="1" source="scm-node-[source]" target="scm-node-[target]">
    <mxGeometry relative="1" as="geometry"/>
</mxCell>
```

### Broken/Missing Connection (red dotted — should exist but doesn't)

```xml
<mxCell id="scm-edge-[n]" value="???" style="edgeStyle=orthogonalEdgeStyle;rounded=1;orthogonalLoop=1;html=1;strokeColor=#FF6B6B;strokeWidth=2;dashed=1;dashPattern=3 3;fontSize=8;fontStyle=1;fontColor=#FF6B6B;" edge="1" parent="1" source="scm-node-[source]" target="scm-node-[target]">
    <mxGeometry relative="1" as="geometry"/>
</mxCell>
```

### Planned Connection (purple dashed — future, not yet built)

```xml
<mxCell id="scm-edge-[n]" value="planned" style="edgeStyle=orthogonalEdgeStyle;rounded=1;orthogonalLoop=1;html=1;strokeColor=#9370DB;strokeWidth=1;dashed=1;fontSize=8;fontStyle=2;fontColor=#9370DB;" edge="1" parent="1" source="scm-node-[source]" target="scm-node-[target]">
    <mxGeometry relative="1" as="geometry"/>
</mxCell>
```

---

## Opportunity Badges

Small annotation boxes placed near flagged tools or connections:

```xml
<mxCell id="scm-opp-[n]" value="[n] [Brief description]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff8e6;strokeColor=#FFA500;strokeWidth=1;fontSize=8;fontStyle=2;fontColor=#8a6914;align=left;spacingLeft=5;" vertex="1" parent="1">
    <mxGeometry x="600" y="[y]" width="300" height="30" as="geometry"/>
</mxCell>
```

### Opportunity List Layout

Stack opportunities vertically starting at x=600, y=270:

```xml
<!-- Opportunity header -->
<mxCell id="scm-opp-header" value="OPPORTUNITIES" style="text;html=1;fontSize=12;fontStyle=1;fontColor=#1a1a2e;align=left;" vertex="1" parent="1">
    <mxGeometry x="600" y="270" width="200" height="25" as="geometry"/>
</mxCell>

<!-- Opportunity 1 -->
<mxCell id="scm-opp-1" value="[1] YouTube → ConvertKit: Zapier can automate subscriber sync" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff8e6;strokeColor=#FFA500;strokeWidth=1;fontSize=8;fontStyle=2;fontColor=#8a6914;align=left;spacingLeft=5;" vertex="1" parent="1">
    <mxGeometry x="600" y="300" width="330" height="30" as="geometry"/>
</mxCell>

<!-- Opportunity 2 (y += 40) -->
<mxCell id="scm-opp-2" value="[2] Dropbox isolated — consolidate to Google Drive" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff5f5;strokeColor=#FF6B6B;strokeWidth=1;fontSize=8;fontStyle=2;fontColor=#8b0000;align=left;spacingLeft=5;" vertex="1" parent="1">
    <mxGeometry x="600" y="340" width="330" height="30" as="geometry"/>
</mxCell>
```

**Opportunity badge colors by type:**

| Type | Fill | Stroke | Font |
|------|------|--------|------|
| Automate (manual → auto) | `#fff8e6` | `#FFA500` | `#8a6914` |
| Consolidate (redundant tool) | `#fff8e6` | `#FFA500` | `#8a6914` |
| Disconnected (isolated tool) | `#fff5f5` | `#FF6B6B` | `#8b0000` |
| Missing tool | `#f5f0ff` | `#9370DB` | `#5b3a8c` |

---

## Legend

```xml
<!-- Legend container -->
<mxCell id="scm-legend-box" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f9f9f9;strokeColor=#e0e0e0;strokeWidth=1;" vertex="1" parent="1">
    <mxGeometry x="600" y="80" width="200" height="160" as="geometry"/>
</mxCell>

<mxCell id="scm-legend-title" value="LEGEND" style="text;html=1;fontSize=11;fontStyle=1;fontColor=#1a1a2e;align=center;" vertex="1" parent="1">
    <mxGeometry x="600" y="85" width="200" height="20" as="geometry"/>
</mxCell>

<!-- Connection types -->
<mxCell id="scm-leg-auto-line" value="" style="endArrow=classic;html=1;strokeColor=#82b366;strokeWidth=2;" edge="1" parent="1">
    <mxGeometry relative="1" as="geometry">
        <mxPoint x="620" y="120" as="sourcePoint"/>
        <mxPoint x="670" y="120" as="targetPoint"/>
    </mxGeometry>
</mxCell>
<mxCell id="scm-leg-auto-label" value="Automated (API)" style="text;html=1;fontSize=9;fontColor=#333333;align=left;" vertex="1" parent="1">
    <mxGeometry x="680" y="112" width="110" height="16" as="geometry"/>
</mxCell>

<mxCell id="scm-leg-manual-line" value="" style="endArrow=classic;html=1;strokeColor=#FFA500;strokeWidth=2;dashed=1;" edge="1" parent="1">
    <mxGeometry relative="1" as="geometry">
        <mxPoint x="620" y="145" as="sourcePoint"/>
        <mxPoint x="670" y="145" as="targetPoint"/>
    </mxGeometry>
</mxCell>
<mxCell id="scm-leg-manual-label" value="Manual (copy-paste)" style="text;html=1;fontSize=9;fontColor=#333333;align=left;" vertex="1" parent="1">
    <mxGeometry x="680" y="137" width="110" height="16" as="geometry"/>
</mxCell>

<mxCell id="scm-leg-broken-line" value="" style="endArrow=classic;html=1;strokeColor=#FF6B6B;strokeWidth=2;dashed=1;dashPattern=3 3;" edge="1" parent="1">
    <mxGeometry relative="1" as="geometry">
        <mxPoint x="620" y="170" as="sourcePoint"/>
        <mxPoint x="670" y="170" as="targetPoint"/>
    </mxGeometry>
</mxCell>
<mxCell id="scm-leg-broken-label" value="Broken / Missing" style="text;html=1;fontSize=9;fontColor=#333333;align=left;" vertex="1" parent="1">
    <mxGeometry x="680" y="162" width="110" height="16" as="geometry"/>
</mxCell>

<!-- Node types -->
<mxCell id="scm-leg-hub" value="" style="rounded=1;fillColor=#f0fff0;strokeColor=#82b366;strokeWidth=2;" vertex="1" parent="1">
    <mxGeometry x="620" y="192" width="14" height="14" as="geometry"/>
</mxCell>
<mxCell id="scm-leg-hub-label" value="Hub tool (3+ connections)" style="text;html=1;fontSize=9;fontColor=#333333;align=left;" vertex="1" parent="1">
    <mxGeometry x="640" y="189" width="150" height="16" as="geometry"/>
</mxCell>

<mxCell id="scm-leg-isolated" value="" style="rounded=1;fillColor=#fff5f5;strokeColor=#FF6B6B;strokeWidth=2;" vertex="1" parent="1">
    <mxGeometry x="620" y="214" width="14" height="14" as="geometry"/>
</mxCell>
<mxCell id="scm-leg-isolated-label" value="Disconnected / Isolated" style="text;html=1;fontSize=9;fontColor=#333333;align=left;" vertex="1" parent="1">
    <mxGeometry x="640" y="211" width="150" height="16" as="geometry"/>
</mxCell>
```

---

## Stats Box

```xml
<mxCell id="scm-stats-box" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f9f9f9;strokeColor=#e0e0e0;strokeWidth=1;" vertex="1" parent="1">
    <mxGeometry x="600" y="700" width="200" height="80" as="geometry"/>
</mxCell>

<mxCell id="scm-stats-title" value="SUMMARY" style="text;html=1;fontSize=10;fontStyle=1;fontColor=#1a1a2e;align=center;" vertex="1" parent="1">
    <mxGeometry x="600" y="705" width="200" height="16" as="geometry"/>
</mxCell>

<mxCell id="scm-stats-content" value="[X] tools  |  [Y] automated  |  [Z] manual  |  [W] isolated" style="text;html=1;fontSize=9;fontColor=#666666;align=center;whiteSpace=wrap;" vertex="1" parent="1">
    <mxGeometry x="610" y="725" width="180" height="40" as="geometry"/>
</mxCell>
```

---

## Node Positioning Formula

**Within each zone, distribute tools evenly:**

```
Zone inner padding: 20px top (for label), 15px sides
Tools per row: max 3 (at 110px width + 30px gap = 420px fits in 500px zone)
Tool start y: zone.y + 35 (clear zone label)

Row 1: y = zone.y + 35
Row 2: y = zone.y + 90 (35 + 40 height + 15 gap)

Col 1: x = zone.x + 20
Col 2: x = zone.x + 170 (20 + 110 + 40 gap)
Col 3: x = zone.x + 320 (170 + 110 + 40 gap)
```

**Example for Sales zone at y=290:**
- Tool 1: x=60, y=325
- Tool 2: x=210, y=325
- Tool 3: x=360, y=325
- Tool 4: x=60, y=380 (second row)

---

## ID Naming Conventions

```
Page: page-scm

Title/Subtitle:
  scm-title, scm-subtitle

Category zones:
  scm-zone-content, scm-zone-sales, scm-zone-delivery, scm-zone-admin

Tool nodes:
  scm-node-[toolname]       e.g., scm-node-notion, scm-node-youtube
  scm-node-[toolname]-label  (secondary use labels)

Connection edges:
  scm-edge-[n]              Sequential: scm-edge-1, scm-edge-2, etc.

Opportunity badges:
  scm-opp-header
  scm-opp-[n]               Sequential: scm-opp-1, scm-opp-2, etc.

Legend:
  scm-legend-box, scm-legend-title
  scm-leg-auto-line, scm-leg-auto-label
  scm-leg-manual-line, scm-leg-manual-label
  scm-leg-broken-line, scm-leg-broken-label
  scm-leg-hub, scm-leg-hub-label
  scm-leg-isolated, scm-leg-isolated-label

Stats:
  scm-stats-box, scm-stats-title, scm-stats-content
```

---

## Quality Checklist

Before outputting System Connection Map:

- [ ] All tool nodes have unique IDs (`scm-node-[toolname]`)
- [ ] All edges reference valid source/target node IDs
- [ ] Hub tools (3+ connections) have green thick border
- [ ] Disconnected tools (0 connections) have red thick border
- [ ] Edge colors match connection type (green=auto, orange=manual, red=broken)
- [ ] Each zone contains only tools in that business function
- [ ] Multi-zone tools placed in PRIMARY zone with secondary label
- [ ] Opportunity badges reference specific tool pairs or tools
- [ ] Legend matches the connection types actually used
- [ ] Stats box reflects accurate counts
- [ ] Back to Overview link included