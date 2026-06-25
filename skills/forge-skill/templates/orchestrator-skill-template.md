---
name: [orchestrator-name]
description: "[What the pipeline does end-to-end]. USE WHEN user says '[trigger]', 'run the [pipeline]'. Routes to [step-skill-1], [step-skill-2], [step-skill-3] in sequence."
---

# [Orchestrator Name]

Coordinates a multi-step pipeline. Each step is a separate skill.

## Pipeline

```
[orchestrator]
  -> detect intent / classify input
  -> delegate to [step-skill-1]    [delegate_task]
  -> delegate to [step-skill-2]    [delegate_task]
  -> delegate to [step-skill-3]    [delegate_task]
  -> compose final output
```

## Intent Detection

| User wants | Route to |
|-----------|----------|
| [scenario A] | [workflow-a.md] |
| [scenario B] | [workflow-b.md] |

## Step Execution

For each step:
1. Prepare the input context
2. Use `delegate_task` with the step skill's instructions
3. Validate the output before passing to the next step
4. If output fails validation, retry once, then surface to user

## STOP Gates

At irreversible hand-offs (publish, send, delete):
- Pause and show the user the artifact
- Wait for explicit approval before proceeding

## Error Recovery

If any step fails:
1. Name the step that failed
2. Show what was partially applied
3. Ask whether to retry, roll back, or skip

---
**Version:** 1.0.0
