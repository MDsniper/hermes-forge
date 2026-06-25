---
name: lead-gen-monitor
description: "Watch benniewilliams.com for new inquiries, qualify them, send a 4-email nurture sequence (confirmation, reminder, prep questions, day-before brief), and hand you a 1-page call brief before each 15-min consult. USE WHEN user says 'check for new leads', 'any new inquiries', 'who booked a call', 'prep me for today's calls', 'run the lead gen agent', 'monitor for leads', 'who reached out', 'did anyone book', 'prep my next call'. Do NOT use when user wants to map business processes -- route to `business-xray`."
---

# Lead Gen Monitor -- Bennie Williams AI Employee

Watches for new leads on benniewilliams.com, qualifies them, sends the nurture sequence, and briefs you before each call.

---

## What This Skill Does

Runs on a schedule (cron) to:

1. **Check for new inquiries** -- pulls the latest Calendly bookings + contact form submissions since last run
2. **Qualify each lead** -- scores on fit (company size, urgency, budget signals)
3. **Send nurture emails** -- 4-touch sequence: confirmation → reminder → prep questions → day-before brief
4. **Generate call brief** -- 1-page summary you read before the 15-min call
5. **Post-call follow-up** -- if you tag a call as "closed" or "no close", sends the right follow-up

---

## Inputs

| Source | What it pulls | How |
|--------|---------------|-----|
| Calendly | New bookings, scheduled times, invitee info | Calendly API or webhook |
| Website contact form | New submissions | Form webhook or polled endpoint |
| Email replies | Lead replies to nurture sequence | Polled IMAP or forwarder |
| Manual tags | What happened on the call (closed / no close / not now) | You say "tag [name] as closed" |

---

## Lead Scoring (4 dimensions)

| Dimension | Signal | Weight |
|-----------|--------|--------|
| **Urgency** | "asap", "this week", "urgent" in inquiry | 0-3 |
| **Fit** | Matches one of your services (AI coaching / web dev) | 0-3 |
| **Budget** | Mentions budget, project scope, company name | 0-3 |
| **Specificity** | Asks a specific question vs vague "tell me more" | 0-3 |

**Total: 0-12**
- **9-12:** HOT -- prep thoroughly, lead the call
- **5-8:** WARM -- standard call brief
- **0-4:** COOL -- qualify hard, refer out if no fit

---

## Nurture Sequence (4 emails, 7 days)

### Email 1 -- Day 0 (right after booking)
**Subject:** Your call with Bennie is confirmed
**Body:** Thanks for booking. Here's what to bring: (1) one specific thing you're stuck on, (2) any context you've already tried. The call is 15 minutes -- we'll figure out if I can help and what that looks like.

### Email 2 -- Day 1
**Subject:** Quick reminder + a question
**Body:** Hey, looking forward to tomorrow's call. Quick one: what's the one outcome you want from our 15 minutes? Reply with one sentence and I'll come prepared.

### Email 3 -- Day 4 (3 days before if call is later)
**Subject:** Prep doc -- read before our call
**Body:** Attached: 3 questions I'll likely ask + 3 case studies of similar work. Skim if you can, no prep needed.

### Email 4 -- Day 6 (day before)
**Subject:** Tomorrow at [time] -- final brief
**Body:** Hey, we're on for [time] tomorrow. Call link: [zoom link]. I've put together a 1-page brief on what I think you're working on. See you then.

---

## Call Brief (1 page)

Generated before each call. Read this 5 min before:

```
CALL BRIEF -- [Lead Name] -- [Date/Time]

LEAD INFO
- Name:
- Company (if any):
- Email:
- Source: [Calendly / contact form / referral]

WHAT THEY ASKED
[verbatim quote from their inquiry]

SCORING
- Urgency: X/3
- Fit: X/3
- Budget: X/3
- Specificity: X/3
- TOTAL: X/12 → [HOT / WARM / COOL]

WHAT I THINK THEY WANT
[inferred from inquiry, 1-2 sentences]

3 QUESTIONS TO ASK
1. [based on their inquiry]
2. [based on scoring gaps]
3. [based on service fit]

3 THINGS TO OFFER
1. [service match]
2. [case study or example]
3. [next step if good fit]

WATCH FOR
- [buying signal X]
- [objection Y]
```

---

## Workflows

### 1. Check for New Leads
**Trigger:** Cron -- runs every 4 hours + on-demand
1. Pull new Calendly bookings (API or webhook payload)
2. Pull new contact form submissions (webhook or polled endpoint)
3. Pull email replies from leads in active sequence
4. For each new lead, run `2. Qualify Lead`
5. Add qualified leads to nurture sequence
6. Update internal lead database

### 2. Qualify Lead
**Trigger:** New lead detected
1. Score on 4 dimensions (urgency / fit / budget / specificity)
2. Calculate total + assign HOT / WARM / COOL
3. Generate 1-page call brief
4. Enroll in nurture sequence (Day 0 email)
5. Notify Bennie via Telegram: "New lead: [name], [score], [call time]"

### 3. Send Nurture Sequence
**Trigger:** Cron -- daily at 9am, checks each lead's day-count
1. For each active lead, check if today matches Day 1/4/6
2. Send the appropriate email from the sequence
3. Log the send + track open/reply
4. If lead replies, notify Bennie immediately

### 4. Generate Call Brief
**Trigger:** Cron -- 6 hours before each scheduled call
1. Pull lead info + scoring
2. Pull any email replies from the lead
3. Generate the 1-page brief
4. Save to `~/briefs/[lead-name]-[date].md`
5. Notify Bennie via Telegram: "Brief ready: [name]"

### 5. Post-Call Follow-up
**Trigger:** Bennie says "tag [name] as closed" or "tag [name] as no close"
1. If CLOSED: send welcome packet + kickoff scheduling link
2. If NO CLOSE: send 3-email follow-up sequence (Day 1, 7, 30)
3. If NOT NOW: tag for 90-day re-engagement
4. Log outcome in lead database

---

## Scheduling

| Job | Cron | What it does |
|-----|------|--------------|
| Lead check | Every 4 hours | Pull new leads, qualify, enroll |
| Nurture send | Daily 9am | Send sequence emails |
| Call brief | 6h before each call | Generate + notify |
| Follow-up | Hourly | Check for new tags, trigger sequences |

---

## Outputs

| Output | Where | Format |
|--------|-------|--------|
| Call briefs | `~/briefs/` | Markdown 1-pager (see `assets/sample-call-brief.md`) |
| Lead database | `~/leads/leads.json` | JSON |
| Email log | `~/leads/email-log.json` | JSON |
| Telegram notifications | @benniehermes_bot | Plain text |

## Email Templates (gold-standard examples)

Reference these for tone, length, and structure when generating nurture emails:

- `assets/email-day-0-confirmation.md` -- right after booking
- `assets/email-day-1-reminder.md` -- day before / day of
- `assets/email-day-4-prep.md` -- 3 days before call
- `assets/email-day-6-final-brief.md` -- day before call

**Voice rules across all emails:**
- Plain language, no jargon
- One ask per email (reply with X / read this doc / show up at time Y)
- No hype, no "I'm excited" filler
- Sign as Bennie, not "The Team" or "Bennie W."
- Always offer an out (reschedule, cancel, change mind)

## Reference Files

- `references/hermes-multi-profile-context.md` -- **Read before choosing Mode 3** or deciding which profile to install this skill in. Covers Hermes profiles, the Kanban board, and how they map to AIEB/Claude-Code concepts from the YouTube demos.

---

## When to Activate

**Activate when user says:**
- "check for new leads"
- "any new inquiries"
- "who booked a call"
- "prep me for today's calls"
- "run the lead gen agent"
- "monitor for leads"
- "who reached out"
- "did anyone book"
- "prep my next call"

**Do NOT activate when:**
- User wants to map or redesign the funnel -> route to `business-xray`
- User wants to update the skill itself -> route to `forge-skill` ("update existing skill")

---

## Required Setup

Before this skill can run in autopilot mode:

- [ ] Calendly API key in env: `CALENDLY_API_KEY`
- [ ] SendGrid (or SMTP) for sending emails: `SENDGRID_API_KEY` or SMTP creds
- [ ] Telegram bot for notifications: `TELEGRAM_BOT_TOKEN`, `TELEGRAM_CHAT_ID`
- [ ] Webhook endpoint for contact form: `LEAD_WEBHOOK_URL` (or polling config)
- [ ] Lead database initialized: `~/leads/leads.json`
- [ ] Cron jobs scheduled (see Scheduling section above)

---

## Activation Pathways -- Manual vs Autopilot

**Three ways this skill can run, in increasing order of setup effort:**

### Mode 1 -- Manual (works today, 0 setup)

You open Hermes, say any of the trigger phrases, and I load this skill, ask you for the inquiry text, score it, draft the emails, hand you the call brief. You copy-paste and send.

**Time per check:** ~30 seconds of typing on your end.
**Use when:** You're starting out, don't have API keys, or want to test the AI employee before wiring up integrations.

### Mode 2 -- Autopilot via cron + APIs

Schedule the skill to run every 4 hours via `cronjob`. It pulls from Calendly, sends real emails through SendGrid, notifies you via Telegram.

**Setup time:** 1-2 hours.
**Use when:** You have a few real inquiries per week and want to be hands-off.

### Mode 3 -- Kanban worker profile

Create a dedicated Hermes profile (`hermes profile create leads`) with this skill installed only there. That profile runs as a Kanban worker, claiming lead-check tasks from the shared board and writing results back. Your general `work` profile stays separate.

**Setup time:** 2-4 hours.
**Use when:** You want full separation between hands-on coaching/webdev work and always-on lead gen. See `references/hermes-multi-profile-context.md` for how Hermes profiles and the Kanban board fit together.

---

## Pitfalls -- Lessons From the First Build

### Don't skip the manual mode

If you go straight to autopilot without ever running the skill manually, you'll discover the scoring is off, the email tone is wrong, or the brief format doesn't match how you think. Run Mode 1 for at least a week first.

### Don't promise what the skill can't do yet

If a lead comes in and the skill has no API access, the cron won't fire, the email won't send, and the lead will sit. Either wire up the APIs or run manually. Never claim "the agent is handling your leads" when it isn't.

### Voice is everything

The nurture emails work because they sound like Bennie. If you let the model improvise without referring to `assets/email-day-*.md`, the tone will drift to generic AI-speak. Always reference the gold-standard templates.

### Don't overdo the swimlanes before building

A common failure mode: spending an hour building the perfect Bow-Tie + swimlanes + 24-assets assessment when the goal was to ship an AI employee. The x-ray is INPUT for designing the skill, not a gate. Build a minimum-viable version of this skill first, iterate on it with real inquiries, then circle back to refine the x-ray.

---

## Version

**Version:** 1.0.0
**Created:** 2026-06-25
**For:** Bennie Williams / benniewilliams.com
**Source methodology:** AIEB AI Employee Builder (now Hermes Forge)
**Tests:** Manual trigger against sample inquiry