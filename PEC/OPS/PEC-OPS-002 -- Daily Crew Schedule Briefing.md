# PEC Daily Crew Schedule — Standard Operating Procedure

**Purpose:** Generate a condensed daily schedule briefing for each crew lead, pulling job data from DripJobs and incorporating Dylan's specific instructions for each job. Output is a Slack canvas that Dylan reviews and forwards to the crew lead.

---

## When to Run

- Daily, ideally in the afternoon/evening before the next work day
- Dylan initiates by providing: which crew, which jobs (in order), and any special instructions per job

---

## Step-by-Step Process

### 1. Confirm Inputs from Dylan

Before pulling any data, confirm you have:

- **Which crew lead** the schedule is for (Justin, Mike, or Jay)
- **The jobs in order** (1st, 2nd, 3rd, etc.)
- **Special instructions per job** — Dylan often overrides the standard work order scope. Capture these exactly. Common overrides include:
  - T&M repairs vs. original scope
  - Specific tasks (regrind, clear redo, seal only, etc.)
  - Materials to grab from the shop
  - Special equipment reminders (polishing pucks, 20" machine, etc.)

### 2. Switch to PEC Account in DripJobs

- Navigate to `app.dripjobs.com`
- If logged into Finishing Touch Painting, click the grid icon (top right, next to bell) to access Branches
- Click "Switch Account" next to Prescott Epoxy Company
- Confirm top-left sidebar shows "Prescott Epoxy Co"

### 3. Pull Job Data from DripJobs

For each job, search by customer last name in the global search bar:

**From the Job/Proposal page, capture:**
- Customer full name
- Full address (street, city, state, zip)
- Phone number
- Proposal number
- Job value (total including change orders)
- Line items (product/service descriptions)
- Job status (Scheduled, In Progress, etc.)

**From the Notes tab (scroll down past line items), capture Crew Notes:**
- Square footage per area
- Stem walls (yes/no)
- Moisture reading
- MOHs hardness
- Color selections
- Access notes
- Any special prep flags (carpet glue, patching, cracks, etc.)
- Concrete past garage door (yes/no)

**Important DripJobs navigation notes:**
- Multiple jobs may exist for the same customer — look for the one marked "Job (Scheduled)" not "Deal" or "Cancelled"
- If there are multiple scheduled jobs at different addresses, confirm with Dylan which one
- Notes tab is at the bottom of the proposal page — scroll past line items and totals
- Crew Notes (Team view only) are the primary source; Client Notes and Company Notes are supplemental

### 4. Build the Slack Canvas

Create a Slack canvas using `slack_create_canvas` with this structure:

```
Title: [Crew Lead]'s Schedule — [Day of Week], [Month Day, Year]

# [Crew Lead]'s Schedule — [Day of Week], [Month Day, Year]

**Crew [#] ([Lead Name]) | [X] Jobs**
Work orders and materials are at the shop. Review below for the day overview.

---

## Job [#] — [Customer Last Name] ([Brief Scope Description])

**Address:** [Full address]
**Customer:** [Full name] | [Phone]

**Scope:** [Dylan's specific instructions for this job. If it differs from the work order, call this out prominently with a warning.]

**DripJobs Notes (for reference):**
- [Key crew notes — sq ft, color, hardness, moisture, access, special prep, etc.]

---

[Repeat for each job]

---

**Reminders:**
- [Consolidated list of things to grab from shop, special equipment, key warnings]
```

**Formatting rules:**
- If Dylan says the job is NOT what's on the work order, lead with a prominent warning
- Always include addresses — crew needs them for navigation
- Include phone numbers in case crew needs to contact customer
- Keep DripJobs notes as reference context, but Dylan's instructions are the primary scope
- End with a consolidated reminders section for quick reference

### 5. Send Draft to Dylan for Review

- Use `slack_send_message_draft` to Dylan's DM (channel: D06BG7SKNNB, user: U06BTRQE005)
- Include a brief summary of the jobs and a link to the canvas
- Dylan reviews, edits if needed, then forwards to the crew lead

### 6. Update Job Cache (if maintained)

If the PEC Job Cache is active, update it with any new data pulled from DripJobs during this process.

---

## Common Scenarios

### T&M / Warranty / Redo Jobs
Dylan will specify when a job is a fix, redo, or T&M. The work order in DripJobs may show the original scope. Always lead with Dylan's override and note clearly that the work order does NOT apply.

### Multi-Day Jobs
If a job is too large for one day (>750 sqft or heavy prep), Dylan will specify which portion to tackle. Note the day's scope clearly.

### Multiple Customers at Same Address
Search results may show multiple entries. Look at the job status and address to pick the right one.

### Missing Data
If DripJobs is missing key fields (sqft, crew assignment, etc.), flag it to Dylan in the Slack draft rather than guessing.

---

## Reference Data

- **DripJobs URL:** app.dripjobs.com
- **PEC Account:** Prescott Epoxy Company (switch from Finishing Touch Painting if needed)
- **Dylan's Slack DM channel:** D06BG7SKNNB
- **Dylan's Slack user ID:** U06BTRQE005
- **Crew roster:** Justin (Crew 1), Mike (Crew 2), Jay (Crew 3)
- **Shop address:** 1030 Sandretto Dr Suite K, Prescott, AZ 86305
