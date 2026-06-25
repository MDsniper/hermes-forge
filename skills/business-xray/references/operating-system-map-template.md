# Business X-Ray

Source: business-x-ray/references/operating-system-map-template.md
MIME: text/markdown

# Operating System Map — Draw.io Template

**XML patterns for the future-state Operating System Map: the business as a pipeline of connected Skill Systems.**

This is the **payoff page**. It reads two ways at once:
- **Down each card:** Skill System → Skills → Tools/MCPs → Digital Assets (what it *is*, *does*, *uses*, *runs on*).
- **Across the page:** numbered stages ①→④ with the **Digital Asset each stage passes** sitting in a **handoff shelf between the cards**, plus a **loop-back** arrow — so you watch the work move down the line and recycle.

It ends with **"Skill Systems to Build First"** — cards in build order (see the ordering algorithm in `workflows/operating-system-map.md`).

> Standard draw.io palette (`references/drawio-standards.md`). Worked examples: `examples/example-operating-system-map.drawio` (agency) and `examples/example-operating-system-map-coach.drawio` (coach). The layout is **business-agnostic** — flex every label.

---

## The 5 Node Types (this is the legend)

| Swatch | Term | What it is | Style |
|--------|------|------------|-------|
| 🟦 blue banner | **Skill System** | A stage run as one AI worker you build | header `fillColor=#3399FF` white bold |
| ⬜ blue chip | **Skill** | One job it runs (`draft-content`) | `fillColor=#ffffff;strokeColor=#6c8ebf;fontColor=#1a56db` |
| 🔌 tiered chip | **Tool / MCP** | What it plugs into (tier-colored) | see MCP tiers below |
| 🟪 purple chip | **Digital Asset** | Knowledge it runs on / passes on | `fillColor=#ffffff;strokeColor=#9370DB;fontColor=#5b3a8c` |
| 🟧 amber | **Handoff** | The Digital Asset passed to the next stage | shelf `fillColor=#fff8e6;strokeColor=#d79b00;dashed=1`; arrows `strokeColor=#d79b00;strokeWidth=3` |

**Zone backgrounds inside a card:** Skills `#eef4fe`/`#a9c4ec` · Tools `#fafafa`/`#d9d9d9` · Digital Assets `#f7f2fc`/`#d6bdea`. **Card frame:** `#ffffff`/`#cfe3f7;shadow=1`.

**Digital Asset status:** mark each in-card asset **✅ exists** or append **⚠️ (to build)** — pull from the 24 Assets Green/Yellow/Red score.

**Stages:** default Marketing · Sales · Delivery · Operations; rename to the real value chain. 3-5 cards, numbered ①→④ in flow order. **3 items per zone** (merge if more — it's a map, not an inventory).

---

## MCP Tier Coloring (Tools/MCPs)

Pull each tier from `references/mcp-directory.md`. Prefix the symbol AND color the border.

| Tier | Prefix | Fill | Stroke | Width | Dashed |
|------|--------|------|--------|-------|--------|
| ✅ Native MCP | `✅ ` | `#f0fff0` | `#82b366` | 2 | no |
| 🔶 Via Zapier/API | `🔶 ` | `#fff8e6` | `#d79b00` | 2 | no |
| ⚪ No MCP yet | `⚪ ` | `#f4f4f4` | `#999999` | 1 | yes |

---

## Page + Geometry

```
pageWidth ≈ 1880   pageHeight ≈ 980   (4 stages; widen for 5)

CARDS (slim, 3 zones): width 300, one per stage.
  Card c left edge:  Cx = 40 + c*500   →  c0=40 · c1=540 · c2=1040 · c3=1540
  frame:        x=Cx,    y=130, w=300, h=560
  header:       x=Cx,    y=130, w=300, h=62     (🟦 Skill System, value "①…")
  SKILLS zone:  x=Cx+10, y=206, w=280, h=146 ; label x=Cx+18,y=212 ; chips x=Cx+20, y=236/272/308, w=260,h=30
  TOOLS zone:   x=Cx+10, y=364, w=280, h=158 ; label x=Cx+18,y=370 ; chips x=Cx+20, y=394/430/466, w=260,h=30
  ASSETS zone:  x=Cx+10, y=534, w=280, h=146 ; label x=Cx+18,y=540 ; chips x=Cx+20, y=564/600/636, w=260,h=30

HANDOFF SHELVES (between card g and g+1): in the 200px gap.
  Gx = 340 + g*500   →  g0=340 · g1=840 · g2=1340
  shelf:   x=Gx+25, y=330, w=150, h=160 ; label x=Gx+33,y=336 "📄 PASSES →"
  passed Digital Asset tokens (purple): x=Gx+33, y=360 / 400, w=134, h=34
  flow arrow IN:  source=osm-frame-g   target=osm-shelf-g       (exitX=1,entryX=0, mid-height)
  flow arrow OUT: source=osm-shelf-g   target=osm-frame-(g+1)   (exitX=1,entryX=0, mid-height)

LOOP-BACK: source=osm-frame-[last] (exitX=0.5,exitY=1) → target=osm-frame-0 (entryX=0.5,entryY=1),
  dashed amber, waypoints at y=720 (just below the cards), label "↺ renewal & referral fuels new leads".

BUILD-FIRST ROW (bottom): divider line y=752; header y=762.
  Card j: x=40 + j*362, y=794, w=340, h=128   →  j0=40 · j1=402 · j2=764 · j3=1126 · j4=1488

LEGEND: horizontal strip box x=40,y=84,w=1800,h=30 + one text cell (emoji swatches).
Back link: x=40, y=938, w=150, h=30.
```

---

## Element Snippets

### Title + Subtitle + Legend strip
```xml
<mxCell id="osm-title" value="[BUSINESS] — OPERATING SYSTEM" style="text;html=1;fontSize=20;fontStyle=1;fontColor=#1a1a2e;align=left;verticalAlign=middle;" vertex="1" parent="1"><mxGeometry x="40" y="20" width="1200" height="32" as="geometry"/></mxCell>
<mxCell id="osm-subtitle" value="Your business as connected Skill Systems — each runs Skills on its Digital Assets, and passes a Digital Asset to the next stage" style="text;html=1;fontSize=12;fontColor=#666666;align=left;verticalAlign=top;" vertex="1" parent="1"><mxGeometry x="40" y="54" width="1300" height="20" as="geometry"/></mxCell>

<mxCell id="osm-legend-box" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f9f9f9;strokeColor=#e0e0e0;" vertex="1" parent="1"><mxGeometry x="40" y="84" width="1800" height="30" as="geometry"/></mxCell>
<mxCell id="osm-legend-text" value="🟦 Skill System (AI worker you build)     ·     ⬜ Skill (one job it runs)     ·     🔌 Tool / MCP:  ✅ native MCP · 🔶 via Zapier/API · ⚪ none yet     ·     🟪 Digital Asset (knowledge it runs on &amp; passes on)     ·     🟧 Handoff (asset passed to the next stage)" style="text;html=1;fontSize=11;fontColor=#333333;align=left;verticalAlign=middle;" vertex="1" parent="1"><mxGeometry x="54" y="84" width="1780" height="30" as="geometry"/></mxCell>
```

### One Card (repeat per stage; Cx = 40 + c*500)
```xml
<mxCell id="osm-frame-[c]" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#ffffff;strokeColor=#cfe3f7;strokeWidth=1;shadow=1;" vertex="1" parent="1"><mxGeometry x="[Cx]" y="130" width="300" height="560" as="geometry"/></mxCell>
<mxCell id="osm-emp-[c]" value="&lt;b&gt;① [STAGE] SKILL SYSTEM&lt;/b&gt;&#10;🤖 [Persona] · [function]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#3399FF;strokeColor=#1a56db;fontColor=#ffffff;fontSize=12;spacing=4;" vertex="1" parent="1"><mxGeometry x="[Cx]" y="130" width="300" height="62" as="geometry"/></mxCell>

<mxCell id="osm-zone-skills-[c]" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#eef4fe;strokeColor=#a9c4ec;" vertex="1" parent="1"><mxGeometry x="[Cx+10]" y="206" width="280" height="146" as="geometry"/></mxCell>
<mxCell id="osm-lbl-skills-[c]" value="⚙  SKILLS — jobs it runs" style="text;html=1;fontSize=11;fontStyle=1;fontColor=#1a56db;align=left;" vertex="1" parent="1"><mxGeometry x="[Cx+18]" y="212" width="240" height="18" as="geometry"/></mxCell>
<mxCell id="osm-skill-[c]-0" value="[skill]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#ffffff;strokeColor=#6c8ebf;fontColor=#1a56db;fontSize=11;" vertex="1" parent="1"><mxGeometry x="[Cx+20]" y="236" width="260" height="30" as="geometry"/></mxCell>
<!-- skill-[c]-1 at y=272, skill-[c]-2 at y=308 -->

<mxCell id="osm-zone-tools-[c]" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fafafa;strokeColor=#d9d9d9;" vertex="1" parent="1"><mxGeometry x="[Cx+10]" y="364" width="280" height="158" as="geometry"/></mxCell>
<mxCell id="osm-lbl-tools-[c]" value="🔌  TOOLS / MCPs — what it plugs into" style="text;html=1;fontSize=11;fontStyle=1;fontColor=#555555;align=left;" vertex="1" parent="1"><mxGeometry x="[Cx+18]" y="370" width="270" height="18" as="geometry"/></mxCell>
<mxCell id="osm-tool-[c]-0" value="✅ [Tool]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f0fff0;strokeColor=#82b366;strokeWidth=2;fontColor=#2d6a4f;fontSize=11;" vertex="1" parent="1"><mxGeometry x="[Cx+20]" y="394" width="260" height="30" as="geometry"/></mxCell>
<!-- tool-[c]-1 at y=430, tool-[c]-2 at y=466 ; recolor by tier (✅/🔶/⚪) -->

<mxCell id="osm-zone-assets-[c]" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f7f2fc;strokeColor=#d6bdea;" vertex="1" parent="1"><mxGeometry x="[Cx+10]" y="534" width="280" height="146" as="geometry"/></mxCell>
<mxCell id="osm-lbl-assets-[c]" value="📄  DIGITAL ASSETS — knowledge it runs on" style="text;html=1;fontSize=11;fontStyle=1;fontColor=#5b3a8c;align=left;" vertex="1" parent="1"><mxGeometry x="[Cx+18]" y="540" width="270" height="18" as="geometry"/></mxCell>
<mxCell id="osm-asset-[c]-0" value="[Asset]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#ffffff;strokeColor=#9370DB;fontColor=#5b3a8c;fontSize=11;" vertex="1" parent="1"><mxGeometry x="[Cx+20]" y="564" width="260" height="30" as="geometry"/></mxCell>
<!-- asset-[c]-1 at y=600, asset-[c]-2 at y=636 ; append " ⚠️" to unbuilt assets -->
```

### Handoff shelf + flow arrows (between card g and g+1; Gx = 340 + g*500)
```xml
<mxCell id="osm-shelf-[g]" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff8e6;strokeColor=#d79b00;dashed=1;" vertex="1" parent="1"><mxGeometry x="[Gx+25]" y="330" width="150" height="160" as="geometry"/></mxCell>
<mxCell id="osm-shelf-lbl-[g]" value="📄 PASSES  →" style="text;html=1;fontSize=10;fontStyle=1;fontColor=#8a6914;align=left;" vertex="1" parent="1"><mxGeometry x="[Gx+33]" y="336" width="134" height="16" as="geometry"/></mxCell>
<mxCell id="osm-pass-[g]-0" value="[Digital Asset passed]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#ffffff;strokeColor=#9370DB;fontColor=#5b3a8c;fontSize=10;fontStyle=1;" vertex="1" parent="1"><mxGeometry x="[Gx+33]" y="360" width="134" height="34" as="geometry"/></mxCell>
<!-- pass-[g]-1 at y=400 (optional 2nd) -->
<mxCell id="osm-flowin-[g]" value="" style="endArrow=block;html=1;rounded=0;strokeColor=#d79b00;strokeWidth=3;exitX=1;exitY=0.5;entryX=0;entryY=0.5;" edge="1" parent="1" source="osm-frame-[g]" target="osm-shelf-[g]"><mxGeometry relative="1" as="geometry"/></mxCell>
<mxCell id="osm-flowout-[g]" value="" style="endArrow=block;html=1;rounded=0;strokeColor=#d79b00;strokeWidth=3;exitX=1;exitY=0.5;entryX=0;entryY=0.5;" edge="1" parent="1" source="osm-shelf-[g]" target="osm-frame-[g+1]"><mxGeometry relative="1" as="geometry"/></mxCell>
```

### Loop-back
```xml
<mxCell id="osm-loopback" value="↺  renewal &amp; referral fuels new leads" style="endArrow=block;html=1;rounded=1;strokeColor=#d79b00;strokeWidth=2;dashed=1;fontSize=10;fontStyle=2;fontColor=#8a6914;labelBackgroundColor=#ffffff;exitX=0.5;exitY=1;entryX=0.5;entryY=1;" edge="1" parent="1" source="osm-frame-[last]" target="osm-frame-0">
  <mxGeometry relative="1" as="geometry"><Array as="points"><mxPoint x="[last card center x]" y="720"/><mxPoint x="190" y="720"/></Array></mxGeometry>
</mxCell>
```

### Skill Systems to Build First (ordered, tagged)
```xml
<mxCell id="osm-opp-divider" value="" style="line;strokeColor=#e0e0e0;strokeWidth=1;html=1;" vertex="1" parent="1"><mxGeometry x="40" y="752" width="1800" height="8" as="geometry"/></mxCell>
<mxCell id="osm-opp-header" value="⚡ SKILL SYSTEMS TO BUILD FIRST" style="text;html=1;fontSize=15;fontStyle=1;fontColor=#1a1a2e;align=left;verticalAlign=middle;" vertex="1" parent="1"><mxGeometry x="40" y="762" width="1000" height="28" as="geometry"/></mxCell>
<!-- Card j in BUILD ORDER (left = first). Tag in the title: ⚡ quick win · 🧱 needs asset first · 🔗 unlocks others · ⚪ build connector -->
<mxCell id="osm-opp-[j]" value="&lt;b&gt;[Skill System to build]&lt;/b&gt;  ·  [persona]&#10;&#10;[the job it takes over + the win].  [tag]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f0fff0;strokeColor=#82b366;strokeWidth=2;fontColor=#2d6a4f;fontSize=11;align=left;verticalAlign=top;spacingLeft=10;spacingTop=10;spacingRight=10;" vertex="1" parent="1"><mxGeometry x="[40 + j*362]" y="794" width="340" height="128" as="geometry"/></mxCell>
```

### Back link
```xml
<mxCell id="osm-back" value="← Back to Overview" style="rounded=1;fillColor=#f5f5f5;strokeColor=#666666;fontSize=11;link=data:page/id,page-1;" vertex="1" parent="1"><mxGeometry x="40" y="938" width="150" height="30" as="geometry"/></mxCell>
```

---

## ID Naming
```
page-osmap · osm-title · osm-subtitle · osm-legend-box · osm-legend-text
per card c:  osm-frame-[c] · osm-emp-[c] · osm-zone-{skills,tools,assets}-[c] · osm-lbl-{skills,tools,assets}-[c] · osm-skill-[c]-[i] · osm-tool-[c]-[i] · osm-asset-[c]-[i]
per gap g:   osm-shelf-[g] · osm-shelf-lbl-[g] · osm-pass-[g]-[i] · osm-flowin-[g] · osm-flowout-[g]
osm-loopback · osm-opp-divider · osm-opp-header · osm-opp-[j] · osm-back
```

---

## Quality Checklist
- [ ] Cards numbered ①→④ in flow order; headers say "[STAGE] SKILL SYSTEM · 🤖 [persona]"
- [ ] Each card has all 3 zones (Skills · Tools/MCPs · Digital Assets), 3 items each
- [ ] Tools tier-tagged (✅/🔶/⚪) from `mcp-directory.md` — not guessed
- [ ] In-card Digital Assets marked ✅ exists / ⚠️ to build (from 24 Assets)
- [ ] Each handoff shelf sits BETWEEN cards with a purple passed-asset + flow arrows IN and OUT
- [ ] Loop-back arrow present (retention/referral)
- [ ] Build-first row in BUILD ORDER (Slot 1 = the user's #1) and each card tagged (⚡/🧱/🔗/⚪)
- [ ] Horizontal legend strip with all 5 node types; Back link present
- [ ] Every cell unique id; every `&` written `&amp;`; page added to the existing `.drawio` file
```
