# Build Skill System -- Multi-Step Automation Chains

Build a chain of step-skills + an orchestrator that runs them as one operation.

---

## When to Use

- "build a skill system", "automate this whole operation"
- "turn this process into a system"
- The operation is SEVERAL jobs wired in sequence, not one job
- After `business-xray` surfaces a process to automate

**Rule of thumb:** one job -> `create-skill.md`; an operation of several jobs -> this workflow.

---

## Step 1: Decompose the Operation

Ask the user to describe the full process end-to-end. Then break it into discrete steps:

1. **List every distinct job** in the operation (each job = one skill)
2. **Map the handoffs** -- what does each step receive and produce?
3. **Identify dependencies** -- which steps must complete before others?
4. **Find the STOP gates** -- which handoffs need human approval?

Output: a step map like:
```
Step 1: Research (input: topic, output: research brief)
Step 2: Outline (input: research brief, output: structured outline)
Step 3: Draft (input: outline, output: first draft)
  STOP: User reviews draft
Step 4: Edit (input: draft + user feedback, output: final version)
Step 5: Publish (input: final version, output: published URL)
```

---

## Step 2: Build Each Step-Skill

For each step in the map, create a standalone skill:

```
skill_manage(action=create, name="[system-name]-step[N]-[action]", content="...")
```

Each step-skill should:
- Accept its input clearly (what data does it need?)
- Produce its output in a predictable format
- Include validation (did it succeed?)
- Be independently testable

Use `delegate_task` to build skills in parallel if they're independent.

---

## Step 3: Build the Orchestrator

Create the orchestrator skill that chains the steps:

```
skill_manage(action=create, name="[system-name]", content="...")
```

The orchestrator's SKILL.md:
```yaml
---
name: [system-name]
description: "Run the full [operation] pipeline. USE WHEN user says 'run [operation]', 'do [operation]'."
---

# [System Name] Orchestrator

## Pipeline

1. Load Step 1: `[step-1-skill]` -> produces [output]
2. Load Step 2: `[step-2-skill]` -> takes [input], produces [output]
   STOP: [if human approval needed]
3. Load Step 3: `[step-3-skill]` -> takes [input], produces [output]
...

## Error Handling

If any step fails:
1. Name the step that failed
2. Show partial output
3. Ask: retry, skip, or abort?

## State Tracking

Track progress in a temp file:
~/[system-name]-state.yaml
```

---

## Step 4: Wire the Handoffs

Each handoff needs:
- **Format agreement** -- Step 1's output matches Step 2's expected input
- **Validation** -- Check that output has required fields before passing on
- **STOP gate** -- If the handoff is irreversible, require user approval

For STOP gates:
```
### Step 3: Publish
[Instructions]

**STOP:** Show the user the final artifact. Wait for explicit approval before publishing.
```

---

## Step 5: Test End-to-End

Run the full pipeline with a real input:

1. Feed a realistic test case through the orchestrator
2. Verify each step receives correct input and produces correct output
3. Verify STOP gates pause correctly
4. Verify error handling works (break one step on purpose)

---

## Step 6: Graduate to Cron (Optional)

If the system runs repeatedly:

```
cronjob(action=create, schedule="0 9 * * *",
  prompt="Run the [system-name] pipeline with [input source]",
  deliver="telegram",
  skills=["[system-name]"])
```

---

## Exit Checklist

- [ ] Each step is an independently testable skill
- [ ] Handoff formats are documented and validated
- [ ] STOP gates at irreversible hand-offs
- [ ] Orchestrator handles step failures gracefully
- [ ] End-to-end test passed with real input
- [ ] State tracking works for resumption
