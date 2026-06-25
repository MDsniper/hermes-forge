# Generate Report -- HTML + Notion Output

Produce a polished client deliverable from the x-ray data. Two output paths: HTML file and Notion page.

---

## When to Use

- After completing any x-ray workflow (progressive-interview, expand-process, etc.)
- User says "generate report", "make a report", "export this", "push to notion"
- Client needs a deliverable they can view without draw.io

---

## Step 1: Gather the Data

Read the current x-ray state from the session context:
- Business model and archetype
- Bow-Tie Funnel (attract/engage/convert/deliver/retain)
- Process map (all expanded areas with annotations)
- Tool inventory
- Opportunities (bottlenecks, automation, high-value, digital assets)
- 24 Assets scores (if assessed)

If data is incomplete, note what's missing and proceed with what exists.

---

## Step 2: Generate the HTML Report

Read `templates/report-template.html` for the structure.

Fill in every `{{PLACEHOLDER}}` with the actual data:

| Placeholder | Source |
|-------------|--------|
| `{{BUSINESS_NAME}}` | From the interview |
| `{{DATE}}` | Today's date |
| `{{ARCHETYPE}}` | From business-archetypes.md matching |
| `{{TOTAL_PROCESSES}}` | Count of mapped processes |
| `{{BOTTLENECKS}}` | Count of red annotations |
| `{{AUTOMATION_OPPS}}` | Count of orange dashed annotations |
| `{{LEVERAGE_SCORE}}` | From 24 Assets assessment (or "Pending") |
| `{{ATTRACT_ITEMS}}` through `{{RETAIN_ITEMS}}` | Bow-Tie data |
| `{{PROCESS_MAP}}` | HTML swimlanes from the process data |
| `{{TOOL_ROWS}}` | Table rows from tool inventory |
| `{{OPPORTUNITY_ROWS}}` | Table rows from identified opportunities |
| `{{DO_FIRST}}` / `{{DO_NEXT}}` / `{{DO_LATER}}` | Roadmap items |
| `{{ASSET_CATEGORIES}}` | 24 Assets grid (or "Not yet assessed") |

**For process maps**, generate HTML swimlanes:
```html
<div class="swimlane">
  <div class="lane-row">
    <div class="lane-label">Lead Gen</div>
    <div class="lane-steps">
      <div class="step">Content creation</div>
      <span class="arrow">→</span>
      <div class="step automate">SEO optimization</div>
      <span class="arrow">→</span>
      <div class="step bottleneck">Manual posting</div>
    </div>
  </div>
</div>
```

Use CSS classes for annotations:
- `bottleneck` = red solid border (slowing down)
- `automate` = orange dashed border (AI could do this)
- `high-value` = green solid border (keep doing)
- `digital-asset` = purple border (needs building)

---

## Step 3: Save the HTML File

Write to the project directory:

```
terminal(command="mkdir -p ~/xray-reports")
write_file(path="~/xray-reports/[business-name]-xray-[date].html", content=html)
```

Tell the user: "Report saved to ~/xray-reports/[name]-xray-[date].html"

---

## Step 4: Push to Notion (Optional)

If the user wants it in Notion:

1. Create a parent page (or use an existing one):

```bash
ntn api v1/pages \
  parent[page_id]=PARENT_PAGE_ID \
  properties[title][0][text][content]="[Business Name] — Business X-Ray"
```

2. Push the report content as markdown blocks:

```bash
ntn api v1/pages/{page_id}/markdown -X PATCH \
  markdown="## Executive Summary
- Processes mapped: N
- Bottlenecks: N
- Automation opportunities: N

## Bow-Tie Funnel
..."
```

3. For the process map and tool inventory, use Notion tables:

```bash
ntn api v1/pages/{page_id}/children -X POST \
  children='[{"object":"block","type":"table",...}]'
```

4. Return the Notion page URL to the user.

---

## Step 5: Update Progress State

Save the current state for session resumption:

```yaml
# ~/xray-reports/[business-name]-state.yaml
business_name: "..."
archetype: coach
date: 2026-06-25
phase: report_generated
processes_mapped: [lead-gen, sales, fulfillment]
tools_inventory: true
assets_assessed: false
report_html: ~/xray-reports/...html
notion_page_id: "..."  # if pushed
```

---

## Output Format Summary

| Output | Format | Location |
|--------|--------|----------|
| HTML Report | Self-contained HTML | ~/xray-reports/ |
| Notion Page | Notion blocks | Notion workspace |
| Progress State | YAML | ~/xray-reports/ |
