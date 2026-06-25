---
name: [skill-name]
description: "[What it does on a schedule]. USE WHEN user says 'run [X] every morning', 'schedule [X]', 'automate [X] daily', 'set up a recurring [X]'."
---

# [Skill Name] -- Scheduled Automation

Runs on a cron schedule via the Hermes `cronjob` tool.

## Schedule Setup

```
cronjob(
  action="create",
  name="[skill-name]",
  schedule="0 9 * * *",           # Daily at 9am (adjust as needed)
  prompt="[Full self-contained prompt for the skill]",
  deliver="telegram",             # Where to send output
  skills=["[this-skill-name]"]    # Load this skill on each run
)
```

## What It Does

[Description of the recurring task]

## Input Sources

- [Where the skill gets its data -- files, APIs, previous outputs]

## Output

- [What the skill produces]
- [Where it's delivered -- Telegram, file, etc.]

## Safety Rails

- [What conditions should pause or skip a run]
- [What requires human approval]
- [Maximum run time / token budget]

## Monitoring

Check job history:
```
cronjob(action="list")
```

Pause if something's wrong:
```
cronjob(action="pause", job_id="[id]")
```

---
**Version:** 1.0.0
