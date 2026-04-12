# PEC-FIN-001 — Protiv ProPay Close-Out

**Company:** Prescott Epoxy (PEC)
**Function:** Finance / Job Costing
**Owner:** Dylan Nordby
**Last Updated:** March 30, 2026
**Created By:** Cowork VA

---

## Purpose

Close out completed ProPays in Protiv so that only active/bonusable jobs remain in "Started" status. This prevents stale ProPays from inflating variance reports and keeps the bonus pipeline clean.

---

## When to Run

Monthly, or when Dylan requests a close-out review. Typical trigger: accumulated Started ProPays that correspond to jobs already marked Complete or Paid in Full in DripJobs.

---

## Prerequisites

- Protiv access (app.protiv.com) — login as Dylan Nordby
- DripJobs access (app.dripjobs.com) — to cross-reference job statuses
- Know the bonus cutoff date (e.g., "only bonus on jobs from February 2026 forward")

---

## Procedure

### Step 1: Pull Started ProPays from Protiv

1. Go to app.protiv.com → ProPay
2. Filter by **Status: Started**
3. Note the total count and export/screenshot the list for reference

### Step 2: Cross-Reference Against DripJobs

1. Open DripJobs → Jobs List
2. Filter by Deal Stage: **Project Complete** + **Paid in Full**
3. Compare each Started ProPay name against DripJobs completed jobs
4. Categorize into:
   - **Ready to close** — DripJobs job is Complete/Paid in Full
   - **Manual review** — no DripJobs match (internal jobs, name mismatches, events, etc.)

### Step 3: Determine What to Close

Per Dylan's standing instructions:
- Close all "manual review" / junk / internal ProPays (Home Show, personal jobs, no-match entries)
- Close all ProPays with end dates before the bonus cutoff month
- Keep only ProPays from the bonus cutoff month forward in Started status

### Step 4: Bulk Close in Protiv

Protiv has no single "Close" button for bulk actions. The pipeline is:

**Started → Completed → Approved** (auto-advances to Closed from there)

1. Filter ProPay list to **Status: Started**
2. Select all rows using the header checkbox
3. **Deselect** the ProPays you want to keep open:
   - UI checkboxes can be unreliable with MUI DataGrid — if clicking doesn't deselect, use browser console JavaScript: `row.querySelector('input[type="checkbox"]').click()`
4. Click **Bulk Action → Complete**
5. Confirm the dialog — if the Confirm button doesn't respond to clicks, use JavaScript: find the button with `textContent === 'Confirm'` and call `.click()`
6. Refresh the page to verify the Started count dropped
7. Switch filter to **Status: Completed**
8. Select all newly completed ProPays
9. Click **Bulk Action → Approve**
10. Confirm and refresh to verify

### Step 5: Verify

- Filter by Started → confirm only the "keep" ProPays remain
- Filter by Approved → newly approved ProPays should auto-advance to Closed
- Note: Protiv indicator counts (Pending/Started/Approved) are stale until page refresh

### Step 6: Pull Bonus Liability

After closing out ProPays, always pull the current bonus liability:

1. Go to **Protiv → Bonuses** (left sidebar)
2. Set date range to cover the current bonus period (e.g., Jan 1 – current date)
3. Record the **Pending Bonuses** total from the indicators bar
4. Page through the Bonus Statements list and capture every **Pending** statement:
   - Ref #, Crew Member Name, Statement Period, Total Bonus
5. Break down pending bonuses by statement period (e.g., Feb vs Mar)
6. Cross-check: the sum of all pending statement amounts should match the Pending Bonuses indicator
7. Flag any deactivated crew members with pending bonuses (may need Dylan's decision)
8. Also check the 11 Started ProPays' "Approved Bonuses" column — if any under-budget ProPay shows $0.00, the bonus pool may not be configured

### Step 7: Report & Document

- Update the close-out report in HQ folder — include bonus liability section
- Send one Slack message to Dylan: what changed, what's still open, bonus owed, any flags
- Flag any ProPays with missing budgets or large variances

---

## Known Protiv Quirks

- **No bulk Close action** — the furthest bulk actions go is Approve. ProPays auto-advance from Approved to Closed.
- **Stale indicator counts** — the Pending/Started/Approved indicator badges don't refresh after bulk actions. Reload the page.
- **MUI DataGrid checkbox issues** — deselecting individual rows after "select all" sometimes doesn't register visually or in the selection count. Use JavaScript `.click()` on the checkbox input as a workaround.
- **Confirm button unreliable** — the Confirm button on bulk action dialogs sometimes doesn't respond to standard clicks. Use JavaScript DOM `.click()` as a fallback.

---

## Escalation

- If a ProPay has no DripJobs match and it's not obviously junk/internal → flag to Dylan before closing.
- If a ProPay shows "Accepted" status in DripJobs (not Complete) but has a Started ProPay → confirm with Dylan if the job is actually done.
- If budget is missing on a ProPay → flag it; can't be properly costed until budget is added.
