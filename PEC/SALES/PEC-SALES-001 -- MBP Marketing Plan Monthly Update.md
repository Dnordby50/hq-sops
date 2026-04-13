# SOP -- MBP Marketing Plan Monthly Update

tags: #sop #sales #marketing #mbp #dripjobs

---

## SOP Title: MBP Marketing Plan -- Monthly KPI Update

**SOP ID:** PEC-SALES-001
**Company:** PEC
**Owner:** Dylan
**Approved by:** Dylan
**Last updated:** 2026-03-30
**Version:** 1.0

---

## Purpose

Populate the "Marketing Plan" tab in the MBP 2026 Google Sheet with actual monthly KPI data (leads, estimates, and sales by source) pulled from DripJobs Metrics. This keeps the BT Academy MBP current so Dylan can track variance against goals and make informed marketing spend decisions.

**This SOP covers both companies — PEC (Prescott Epoxy Company) and FTP (Finishing Touch Painting).** Both share the same MBP 2026 Google Sheet and Marketing Plan tab. The only difference is the lead source prefix: PEC sources start with "PEC" (e.g., "PEC Google Organic (SEO)") and FTP sources start with "FTP" (e.g., "FTP Google Organic (SEO)"). The same DripJobs-to-MBP workflow applies to both; just pull from the correct company's DripJobs metrics and use the matching prefix when entering data.

---

## Scope

**Who this applies to:** Dylan (or Claude assistant)
**When to use this SOP:** At the end of each month (or early the following month) once all jobs for the period are closed in DripJobs.
**Companies:** PEC and FTP (both use this same process and the same MBP 2026 Google Sheet)

---

## Prerequisites

Before starting, make sure:
- [ ] DripJobs is up to date -- all leads, appointments, and sales for the month are entered
- [ ] You have edit access to the MBP 2026 Google Sheet
- [ ] The month's row block exists in the Marketing Plan tab (if not, add rows following the existing pattern)

---

## Key Resources

| Resource | URL / Location |
|---|---|
| MBP 2026 Google Sheet | `https://docs.google.com/spreadsheets/d/1vlumbi2mh_mjtmO1ZiTxMy0BTXbtNCNV-FOM-LVZ_s0/edit?gid=525666189#gid=525666189` |
| DripJobs Metrics (template) | `https://app.dripjobs.com/metrics?start=MM%2FDD%2FYYYY&end=MM%2FDD%2FYYYY` |
| DripJobs Metrics -- January | `https://app.dripjobs.com/metrics?start=01%2F01%2F2026&end=01%2F31%2F2026` |
| DripJobs Metrics -- February | `https://app.dripjobs.com/metrics?start=02%2F01%2F2026&end=02%2F28%2F2026` |
| DripJobs Metrics -- March | `https://app.dripjobs.com/metrics?start=03%2F01%2F2026&end=03%2F30%2F2026` |

---

## Marketing Plan Tab Structure

**Columns:**
- A = Month
- B = Lead Source
- C = Leads Goal
- D = Leads Actual
- E = Var %
- F = Estimates Goal
- G = Estimates Actual
- H = Var %
- I = Sales Goal
- J = Sales Actual
- K = Var %
- L = Campaign Spend Goal
- M = Campaign Spend Actual
- N = Var %
- O = Return On Goal
- P = Return On Actual
- Q = Var %

**Row Layout:**
- Rows 3-24: YTD subtotals (auto-calculated -- do NOT edit)
- Row 26-27: Column headers
- Rows 28-40: January block (rows 34-40 are empty spares)
- Rows 41-60: February block (rows 48-60 are empty spares)
- Rows 61-80: March block (rows 67-80 are empty spares)
- Pattern continues: each month gets a ~20-row block

**Important:** Columns A (Month) and B (Lead Source) use data validation dropdowns. Select from the dropdown rather than free-typing when entering manually.

---

## DripJobs-to-MBP Source Mapping

The mapping is identical for both companies — just swap the prefix (PEC → FTP). DripJobs source names are the same across both accounts.

### PEC (Prescott Epoxy Company)

| DripJobs Source Name | MBP Lead Source Name |
|---|---|
| Google | PEC Google Organic (SEO) |
| Google PPC | PEC Google PPC |
| Coating Launch | PEC Meta |
| Website | PEC Website |
| angi | PEC Angi |
| Repeat Customer | PEC Repeat Customer |
| Referral | PEC Referral |
| Facebook | PEC Facebook Organic |
| Saw our truck | No MBP mapping -- exclude or add row |
| No Source Selected | No MBP mapping -- exclude |
| Jim self-generated | No MBP mapping -- exclude |
| Other | No MBP mapping -- exclude |
| Yard Sign | No MBP mapping -- exclude or add row |

### FTP (Finishing Touch Painting)

**Note:** FTP has its own lead sources in DripJobs which may differ from PEC's. The mapping below was pulled from actual DripJobs data (January 2026). If a new source appears, ask Dylan before adding a row.

| DripJobs Source Name | MBP Lead Source Name |
|---|---|
| Google | FTP Google Organic (SEO) |
| angi | FTP Angi |
| Repeat Customer | FTP Repeat Customer |
| Referral | FTP Referral |
| Other | No MBP mapping -- exclude |

---

## Steps

### Part 0: Select the Correct Company in DripJobs

1. Before pulling any data, confirm you are viewing the correct company in DripJobs.
2. Look for the **building icon** at the top of the DripJobs interface — this is the company switcher.
3. Click the building icon and select the target company (PEC or FTP).
4. Verify the correct company is selected before proceeding to pull metrics.

**Important:** Always check this first. If you pull metrics without switching companies, you'll enter the wrong data into the MBP.

### Part 1: Pull Leads By Source from DripJobs

1. Open DripJobs Metrics for the target month using the URL pattern above (adjust start/end dates).
2. The page loads with KPI summary cards at the top, then the **Leads By Source** section.
3. Record each source name and lead count.

### Part 2: Pull Leads To Appointments (Estimates) from DripJobs

4. On the same Metrics page, look at the **Leads To Appointments** section (right side, same vertical position as Leads By Source).
5. Record each source name and appointment count. This is the "Estimates Actual" value.

### Part 3: Pull Sales By Source from DripJobs

6. **Scroll far down** on the Metrics page. The Sales By Source section is well below the fold -- you must scroll past Leads By Source and Leads To Appointments to find it. The page order is:
   - KPI summary cards
   - Leads By Source | Leads To Appointments
   - **Sales By Source** | Closing Ratio by Salesperson
   - Sales By Salesperson | Sales By Zip Code
   - Closing Ratio by Source | Closing Ratio by Zip Code
7. Record each source name and dollar amount from **Sales By Source**.

### Part 4: Enter Data into MBP Marketing Plan

8. Open the MBP 2026 Google Sheet, Marketing Plan tab.
9. Navigate to the target month's row block using the **Name Box** (top-left cell reference box):
   - Click the Name Box
   - Type the target cell (e.g., `A41` for February row 1, `A61` for March row 1)
   - Press Enter to jump there
10. **ALWAYS fill rows from the top down, using the first empty row in the month's block.** Never skip rows or leave gaps. If a month block has rows 41-60, start at 41 and work down consecutively.
11. For each lead source with data, fill in the row:
    - Column A: Select the month from dropdown
    - Column B: Select the MBP lead source name from dropdown (use the mapping table above)
    - Column D: Enter Leads Actual count
    - Column G: Enter Estimates Actual count
    - Column J: Enter Sales Actual dollar amount (numbers only, no $ sign -- the column is formatted as currency)
12. Repeat for every source that has data for the month.
13. Leave Goal columns (C, F, I, L) and Spend columns (L, M) alone unless you have that data separately.

### Part 5: Verify

14. Scroll back to the top and check the YTD subtotals (rows 3-24). They should auto-sum all monthly rows. Confirm the totals match what DripJobs shows at the top of the Metrics page (Total Leads, Appointments Booked, Sales).
15. Spot-check a few individual source subtotals (rows 5-11) against your entered data.

---

## Decision Points

| Situation | Action |
|---|---|
| A DripJobs source has no MBP mapping (e.g., "Saw our truck", "No Source Selected") | Exclude from MBP. The MBP only tracks sources with active marketing spend or strategic tracking. |
| Facebook leads appear in DripJobs | Map to PEC Facebook Organic. Row added to MBP as of March 2026. |
| A source has leads/estimates but $0 in sales | Still enter the leads and estimates. Leave column J blank or enter 0. |
| DripJobs shows a source not in the mapping table | Ask Dylan before adding a new MBP source row. The dropdown in column B must have the value available. |
| Month's row block doesn't have enough rows | Insert rows before the next month's block, copy formatting from existing rows in the same month. |

---

## Escalation

Escalate to Dylan when:
- A new lead source appears in DripJobs that isn't in the mapping table
- YTD subtotals don't match DripJobs totals (possible formula issue)
- Column B dropdown doesn't include a needed source name

---

## Quality Check

Before marking this task complete, confirm:
- [ ] All sources with leads > 0 have a row in the Marketing Plan
- [ ] Leads Actual, Estimates Actual, and Sales Actual are all filled for each source
- [ ] YTD subtotal row (row 3) totals match DripJobs monthly totals when summed
- [ ] No data was entered in the wrong month's row block
- [ ] Unmapped sources were noted (not silently dropped)

---

## Data Entered To Date (Reference)

### January (Rows 28-33) -- COMPLETE
| Row | Source | Leads | Estimates | Sales |
|---|---|---|---|---|
| 28 | PEC Google PPC | 1 | 1 | $11,580 |
| 29 | PEC Google Organic (SEO) | 9 | 9 | $54,956 |
| 30 | PEC Website | 11 | 9 | $20,703 |
| 31 | PEC Meta | 42 | 16 | $17,967 |
| 32 | PEC Repeat Customer | 0 | 0 | $5,025 |
| 33 | PEC Angi | 6 | 1 | $0 |

### February (Rows 41-47) -- Leads & Estimates COMPLETE, Sales PENDING
| Row | Source | Leads | Estimates | Sales (to enter) |
|---|---|---|---|---|
| 41 | PEC Google PPC | 1 | 1 | (no data) |
| 42 | PEC Google Organic (SEO) | 14 | 14 | $20,292 |
| 43 | PEC Meta | 37 | 11 | $12,960 |
| 44 | PEC Website | 3 | 2 | $10,400 |
| 45 | PEC Angi | 6 | 1 | $2,925 |
| 46 | PEC Repeat Customer | 3 | 2 | $8,600 |
| 47 | PEC Referral | 3 | 2 | $3,950 |

Unmapped Feb sales: Saw our truck ($6,075), No Source Selected ($4,532.50), Jim self-generated ($600)

### March (Rows 61-66) -- Leads & Estimates COMPLETE, Sales PENDING
| Row | Source | Leads | Estimates | Sales (to enter) |
|---|---|---|---|---|
| 61 | PEC Google Organic (SEO) | 17 | 11 | $12,755.50 |
| 62 | PEC Meta | 14 | 3 | $0 |
| 63 | PEC Website | 3 | 3 | $9,420 |
| 64 | PEC Angi | 3 | 0 | $2,950 |
| 65 | PEC Repeat Customer | 3 | 0 | $1 |
| 66 | PEC Referral | 4 | 4 | $13,090 |

Unmapped March sales: Other ($1,880)
March Facebook leads (11) now mapped to PEC Facebook Organic -- needs row added to March block

### FTP January (Rows 34-37) -- COMPLETE
| Row | Source | Leads | Estimates | Sales |
|---|---|---|---|---|
| 34 | FTP Google Organic (SEO) | 3 | 3 | $9,814.20 |
| 35 | FTP Angi | 8 | 4 | $0 |
| 36 | FTP Repeat Customer | 8 | 8 | $73,915 |
| 37 | FTP Referral | 2 | 2 | $19,789 |

Unmapped FTP Jan sources: Other (1 lead, 1 appointment, $0 sales)

---

## Tips for Claude Assistant

- **DripJobs scrolling:** The Sales By Source section is far down the Metrics page. Use aggressive scrolling (scroll_amount: 10) or the End key, then scroll up. The section is between "Leads To Appointments" and "Sales By Salesperson."
- **Google Sheets navigation:** Use the Name Box (click it, type cell ref like `J41`, press Enter) to jump directly to cells. This is faster and more reliable than scrolling.
- **Data entry in Sheets:** Type the value, then press Tab to move right or Enter to move down. For column J specifically, just navigate to the cell, type the number, and press Enter.
- **Dropdowns:** Columns A and B have data validation. If typing directly, make sure the value matches exactly (case-sensitive). Selecting from dropdown is safer.

---

## Related SOPs / Notes

- PEC Sales SOP (Google Drive: `docs.google.com/document/d/1wDaBV-z5UMWtH2k7vf1RVnGhVqlV7SSlqBrhDQJPn84`)
- MBP 2026 is part of the BT Academy coaching framework

---

## Revision History

| Version | Date | Change |
|---|---|---|
| 1.0 | 2026-03-30 | Initial version -- covers leads, estimates, and sales data entry from DripJobs to MBP Marketing Plan |
| 1.1 | 2026-03-30 | Added PEC Facebook Organic to source mapping (Dylan added it to MBP dropdown) |
| 1.2 | 2026-03-30 | Expanded SOP to cover both PEC and FTP -- same MBP 2026 Google Sheet, same process, different source prefixes |
| 1.3 | 2026-03-31 | Added company switcher instructions (Part 0), confirmed FTP source mapping from DripJobs, added FTP January data reference |
