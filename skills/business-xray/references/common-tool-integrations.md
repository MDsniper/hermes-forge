# Business X-Ray

Source: business-x-ray/references/common-tool-integrations.md
MIME: text/markdown

# Common Tool Integrations Reference

**Helps Claude infer what tools CAN connect and how, for smarter connection probing during Business X-Ray.**

---

## How to Use This Reference

During Level 2/3 expansion and the System Connection Map synthesis:
1. When a tool appears, check this reference for known integrations
2. Use integration data to make better inference guesses
3. Suggest specific integration methods when presenting opportunities

---

## Common Tool Pairs

### Native Integrations (built-in, no middleware)

| Tool A | Tool B | Integration | Notes |
|--------|--------|-------------|-------|
| Calendly | Zoom | Auto-generates meeting links | Built-in, just enable |
| Calendly | Google Calendar | Two-way sync | Built-in |
| Calendly | Stripe | Payment collection on booking | Built-in |
| ConvertKit | Stripe | Payment triggers sequences | Built-in |
| ConvertKit | Teachable | Student enrollment triggers | Built-in |
| Stripe | QuickBooks | Auto-sync transactions | Built-in |
| Notion | Slack | Notifications, page embeds | Built-in |
| Gmail | Google Contacts | Contact sync | Built-in (if configured) |
| Gmail | Google Calendar | Event creation from emails | Built-in |
| Google Drive | Gmail | Attachment sharing | Built-in |
| Slack | Google Drive | File sharing, notifications | Built-in |

### Zapier/Make Integrations (middleware needed)

| Tool A | Tool B | via Zapier/Make | Common Trigger |
|--------|--------|-----------------|----------------|
| YouTube | ConvertKit | New subscriber from comments | Video published |
| ConvertKit | Notion | New subscriber → Notion page | Subscriber added |
| Stripe | Notion | Payment → Notion database row | Payment received |
| Typeform | Notion | Form submission → Notion page | Form completed |
| Calendly | Notion | Booking → Notion page | Event scheduled |
| Calendly | ConvertKit | Booking → tag subscriber | Event scheduled |
| Tally | Notion | Form response → database | Submission |
| Tally | ConvertKit | Form → email sequence | Submission |
| Loom | Notion | Video recorded → page update | Recording complete |

### API/Custom Integrations (code or scripts needed)

| Tool A | Tool B | Method | Difficulty |
|--------|--------|--------|------------|
| Claude | Any tool | Custom Python scripts | Medium |
| Notion | Custom apps | Notion API | Medium |
| Stripe | Custom dashboards | Stripe API | Medium |
| Google Sheets | Custom tools | Google Sheets API | Easy |
| Airtable | Custom tools | Airtable API | Easy |

### No Native Connection (always manual unless automated)

| Tool | Limitation | Workaround |
|------|-----------|------------|
| Excel | No real-time API, file-based only | Export CSV, or use Google Sheets instead |
| WorkFlowy | No API, no integrations | Manual only, or migrate to Notion/Todoist |
| Dropbox | File sync only, no workflow triggers | Use Google Drive for collaboration |
| Canva | Limited API, no content push | Download + upload manually, or use Buffer |
| PDF tools | Static output, no data flow | Export + manual distribution |

---

## Tool Stacks by Business Archetype

### Coach / Consultant

**Typical stack:**
| Category | Common Tools |
|----------|-------------|
| Content | YouTube, LinkedIn, Substack/ConvertKit |
| Sales | Calendly, Zoom, Notion (CRM), Stripe |
| Delivery | Zoom, Google Drive, Notion, Loom |
| Admin | Google Calendar, QuickBooks/Wave, Excel |

**Common gaps:**
- No formal CRM (uses spreadsheet or memory)
- Manual follow-up after sales calls
- No onboarding automation
- Content creation disconnected from distribution

**Typical connection profile:**
- 2-3 automated (Calendly↔Zoom, Calendar sync)
- 4-6 manual bridges (most things copy-paste)
- 1-2 disconnected (filing/admin tools)

---

### Course Creator

**Typical stack:**
| Category | Common Tools |
|----------|-------------|
| Content | YouTube, Canva, Descript/CapCut |
| Sales | Teachable/Kajabi, ConvertKit, Stripe |
| Delivery | Teachable/Kajabi, Circle/Skool, Zoom |
| Admin | Google Sheets, Stripe Dashboard |

**Common gaps:**
- Course platform isolated from email (no completion triggers)
- No cart abandonment follow-up
- Community engagement not tracked
- Content repurposing is fully manual

**Typical connection profile:**
- 3-4 automated (ConvertKit↔Stripe, Platform↔Email)
- 3-5 manual bridges (content distribution, community management)
- 1-2 disconnected (design tools, analytics)

---

### Agency

**Typical stack:**
| Category | Common Tools |
|----------|-------------|
| Content | Case studies, LinkedIn, Portfolio site |
| Sales | HubSpot/Pipedrive, Notion, Gmail |
| Delivery | Slack, Notion/Asana, Google Drive, Loom |
| Admin | QuickBooks, Toggl, Google Sheets |

**Common gaps:**
- Project management disconnected from billing
- No automatic time tracking → invoice generation
- Client communication scattered across tools
- No systematic case study capture

**Typical connection profile:**
- 3-5 automated (CRM↔email, PM↔notifications)
- 3-4 manual bridges (billing, reporting)
- 1-2 disconnected (time tracking, portfolio)

---

### Service Provider (Solo)

**Typical stack:**
| Category | Common Tools |
|----------|-------------|
| Content | Word of mouth, LinkedIn, Gmail |
| Sales | Gmail, Google Contacts, Calendly |
| Delivery | Google Drive, Email, Zoom/Phone |
| Admin | Excel/Sheets, Gmail, Calendar |

**Common gaps:**
- Everything manual — no automation at all
- No CRM (contacts in Gmail or spreadsheet)
- No follow-up system
- No results tracking or testimonial capture

**Typical connection profile:**
- 1-2 automated (Calendly↔Calendar at most)
- 5-8 manual bridges (nearly everything)
- 2-3 disconnected (spreadsheets, file storage)

---

### Creator / Influencer

**Typical stack:**
| Category | Common Tools |
|----------|-------------|
| Content | YouTube, Instagram, TikTok, Canva, CapCut |
| Sales | Gumroad/LemonSqueezy, LinkTree, ConvertKit |
| Delivery | Digital downloads, Community platform |
| Admin | Google Sheets, PayPal/Stripe dashboard |

**Common gaps:**
- Monetization disconnected from audience
- No email capture from social platforms
- Content scheduling manual
- Analytics across platforms not unified

**Typical connection profile:**
- 2-3 automated (payment↔email, scheduling)
- 4-6 manual bridges (content distribution, analytics)
- 2-3 disconnected (analytics, file storage)

---

## Integration Opportunity Templates

Use these when presenting opportunities during the synthesis step:

### Manual Bridge → Automation

> **[Tool A] → [Tool B]**: Currently manual ([describe what user does]).
> **Fix:** [Zapier/Make/Native] integration available. Triggers on [event], automatically [action].
> **Effort:** [Low/Medium/High]

### Disconnected Tool → Connect or Eliminate

> **[Tool]**: Not connected to any other system. Used for [purpose].
> **Options:**
> - Connect via [method] to [other tool]
> - Replace with [alternative] that integrates natively
> - Eliminate if [other tool] can serve the same purpose

### Redundant Tools → Consolidate

> **[Tool A] and [Tool B]**: Both used for [similar purpose].
> **Fix:** Consolidate to [recommended tool]. Migrate [data type] from [other tool].
> **Benefit:** One less tool to manage, data in one place.

### Missing Tool → Fill Gap

> **Gap:** No tool for [function] between [Tool A] and [Tool B].
> **Impact:** [What happens without it — manual work, lost data, etc.]
> **Options:**
> - [Tool recommendation 1] — [why it fits]
> - [Tool recommendation 2] — [why it fits]