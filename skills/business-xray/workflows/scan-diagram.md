# Scan Existing Report

**Read an existing HTML report and reconstruct the business state for continued work.**

---

## When to Use

- User has an existing report and wants to continue work
- "load my report", "read my x-ray", "continue from last session", "what did we figure out last time"
- Loading a resume YAML block to pick up where we left off

---

## Inputs

The user can provide input two ways:

1. **Resume YAML block** (paste it into chat):
   > "Here's my resume block from last time, let's pick up where we left off."

2. **Report file path** (local file):
   > "Here's the path to my report (e.g., `~/hermes-xray-reports/reports/[name]-xray-[date].html`)"

---

## Step 1: Read the Resume Block or Report

### If Resume YAML

Parse the YAML and restore session state:
- business_name, business_type
- business_map_complete, bowtie_complete
- pain_points, selected_process
- expanded_processes
- tool_inventory, connections_known
- assets_scores, leverage_score

Confirm to user:
> "I can see you were working on [business name] (last updated [date]). You had completed [business map / bow-tie / N swimlanes] and your [Leverage Score] was [X / pending]. What's next?"

### If Report HTML

Open the HTML file and extract:
- All `.item` divs inside `.business-map` (the 7-column data)
- All `.bowtie-stage` divs (the funnel data)
- All `.lane-row` blocks (process swimlanes)
- All annotation classes (`bottleneck`, `automate`, `high-value`, `digital-asset`)
- The 24 Assets section (if present)
- The 90-Day Roadmap (if present)

Then reconstruct:
```
business_name: [from h1]
date: [from subtitle]
archetype: [from archetype badge if present]
traffic: [from col-traffic .item elements]
converters: [from col-converters .item elements]
products: [from col-products .item elements]
funnels: [from col-funnels .item elements]
math: [from col-math .item elements]
team: [from col-team .item elements]
goals: [from col-goals .item elements]
bowtie: [from .bowtie-stage elements]
processes: [from .lane-row blocks per process]
opportunities: [from annotation classes]
```

---

## Step 2: Confirm Reconstruction

> "Here's what I reconstructed from your report:
>
> **Business:** [Name] ([Archetype])
> **Last updated:** [Date]
> **Completed:**
> - [x] Business Map (7 columns)
> - [x] Bow-Tie Funnel
> - [x] Lead Generation swimlane
> - [ ] Sales swimlane
> - [ ] Fulfillment swimlane
>
> **Bottlenecks flagged:** [N]
> **Automation opportunities:** [N]
> **Digital assets needed:** [N]
>
> What would you like to do next?"

---

## Step 3: Resume Work

Based on what's incomplete, offer the next workflow:

- If only Business Map done → propose Bow-Tie confirmation, then process mapping
- If Lead Gen mapped but not Sales/Fulfillment → propose next area
- If 2+ areas mapped → propose System Connection Map
- If System Connection Map done → propose Operating System Map
- If 24 Assets not done → propose `workflows/digital-assets-assessment.md`
- If everything done → propose `workflows/generate-roadmap.md`

---

## Standalone Output

**Standalone output:** Single HTML report with all completed sections, no separate working file needed.

---

## Error Handling

> "The file doesn't appear to be a valid HTML report. Make sure it's at `~/hermes-xray-reports/reports/[name]-xray-[date].html` and try again."