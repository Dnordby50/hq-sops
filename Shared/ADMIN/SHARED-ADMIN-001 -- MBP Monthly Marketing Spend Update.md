# SHARED-ADMIN-001 -- MBP Monthly Marketing Spend Update

**SOP ID:** SHARED-ADMIN-001
**Title:** Monthly Marketing Plan Update (Campaign Spend + DripJobs Data) into MBP 2026
**Company:** Shared (PEC + FTP)
**Department:** ADMIN
**Version:** 2.1
**Effective Date:** April 7, 2026
**Owner:** Dylan Nordby

---

## PURPOSE

Enter actual monthly campaign spend figures (column M) and actual leads, estimates/booked, and sales figures from DripJobs Metrics (columns D, G, J) into the MBP 2026 Google Sheet (Marketing Plan tab) so BT Academy coaching metrics and ROI calculations stay current. This prevents months from going untracked and keeps the monthly business review accurate.

## SCOPE

Applies to Cowork VA and Dylan. Run monthly by the 5th of the following month (e.g., January spend entered by February 5). Both Prescott Epoxy (PEC) and Finishing Touch Painting (FTP) campaign spend is entered in the same session.

## ASSETS & LINKS

- **MBP 2026 Google Sheet:** "MBP 2026 - Finishing Touch Painting"
- **Sheet ID:** `1vlumbi2mh_mjtmO1ZiTxMy0BTXbtNCNV-FOM-LVZ_s0`
- **Marketing Plan tab GID:** `525666189`
- **Direct link:** `https://docs.google.com/spreadsheets/d/1vlumbi2mh_mjtmO1ZiTxMy0BTXbtNCNV-FOM-LVZ_s0/edit#gid=525666189`
- **Google account:** dylan@finishingtouchpaintingaz.com
- **DripJobs Metrics:** `https://app.dripjobs.com/metrics` (two accounts: PEC and FTP, switch via Tenant Admin)
- **Lead Source Mapping Doc:** `HQ/06 - Automations & Tech/Active Automations/PEC-FTP-DripJobs-to-MBP-LeadSourceMapping-2026-04-07.md`
- **Coating Launch weekly emails:** Search Outlook for sender ads@coatinglaunch.com, subject contains "Weekly Lead Report"

---

## RECURRING MONTHLY COSTS (as of April 2026)

### SEO Management (Coating Launch) -- Fixed
- Total fee: $1,600/month across both companies
- Each company gets $400 in Google Organic (SEO) + $400 in Website
- Enters into 4 cells per month:
  - **PEC Google Organic (SEO)**: $400
  - **PEC Website**: $400
  - **FTP Google Organic (SEO)**: $400
  - **FTP Website**: $400

### Google Ads PPC Management (Coating Launch) -- Semi-variable
- Management fee: $700/month per company (fixed)
- PEC ad spend: varies month to month (check Google Ads invoices or ask Dylan)
- FTP ad spend: $0 as of Q1 2026 (confirm if ads have been turned on)
- Enters into:
  - **PEC Google PPC**: $700 + actual PEC ad spend
  - **FTP Google PPC**: $700 + actual FTP ad spend (if row exists -- see Known Row Gaps)

### PEC Meta Ads (Coating Launch) -- Variable
- **This is NOT a fixed amount.** It varies monthly based on actual ad performance.
- To calculate: pull Coating Launch weekly emails from Outlook for the target month. Each email contains "leads generated" and "avg CPL" for that week. Multiply leads x CPL for each week, then sum the weekly totals.
- Example (January 2026):
  - Week 1: 15 leads x $30.50 CPL = $457.50
  - Week 2: 12 leads x $28.00 CPL = $336.00
  - (continue for all weeks in the month)
  - Total = sum of all weeks
- If a weekly email is missing, average the surrounding weeks to estimate.
- Enters into: **PEC Meta** row, column M

### PEC Angi -- Semi-variable
- Confirm with Dylan each month. Was $350/month in Q1 2026.
- Enters into: **PEC Angi** row, column M

### FTP Angi -- Semi-variable
- Confirm with Dylan each month. Was $1,000/month in Feb-Mar 2026.
- Enters into: **FTP Angi** row, column M

### Zero-spend sources
- All other lead sources (Repeat Customer, Referral, Facebook Organic, Word of Mouth, Walk In, Other) get $0 entered in column M so the variance formula calculates correctly.

---

## PROCEDURE

### Step 1. Gather Data

1. **Ask Dylan** for:
   - PEC Google Ads spend for the month (on top of $700 mgmt fee)
   - FTP Google Ads spend (or confirm still $0)
   - PEC Angi spend
   - FTP Angi spend
   - Any changes to SEO fees or other recurring costs
   - Any one-off campaign costs

2. **Pull Coating Launch emails** from Outlook:
   - Search: sender = ads@coatinglaunch.com
   - Filter to emails within the target month
   - From each "Weekly Lead Report" email, extract: leads generated and avg CPL
   - Calculate: leads x CPL for each week
   - Sum all weeks for the monthly PEC Meta total

### Step 2. Find the Correct Row Numbers

Row numbers shift as months accumulate. **Always verify before editing.** Export CSV via JavaScript in the Chrome console on the Marketing Plan tab:

```javascript
(async () => {
  const resp = await fetch('https://docs.google.com/spreadsheets/d/1vlumbi2mh_mjtmO1ZiTxMy0BTXbtNCNV-FOM-LVZ_s0/export?format=csv&gid=525666189');
  const text = await resp.text();
  const lines = text.split('\n');
  function parseCSVLine(line) {
    const result = []; let current = ''; let inQuotes = false;
    for (let i = 0; i < line.length; i++) {
      if (line[i] === '"') { inQuotes = !inQuotes; }
      else if (line[i] === ',' && !inQuotes) { result.push(current.trim()); current = ''; }
      else { current += line[i]; }
    }
    result.push(current.trim());
    return result;
  }
  return lines.map((line, i) => {
    const cols = parseCSVLine(line);
    if (cols[0] && cols[1]) return `Row${i+1}: ${cols[0]} | ${cols[1]} | M=${cols[12]}`;
    return null;
  }).filter(Boolean).join('\n');
})();
```

This returns every row with its month, lead source, and current column M value.

### Step 3. Enter Values in Column M

1. Click the Name Box (cell reference box, top-left corner of the sheet)
2. Type the cell address (e.g., "M61") and press Enter to navigate
3. Type the dollar amount as a plain number (no $ sign, no commas)
4. Press **Tab** to confirm (Tab moves right, avoiding accidental edits to rows below)
5. Repeat for each cell

**Cells to update each month (typical):**

| Lead Source Row | Value |
|----------------|-------|
| PEC Google PPC | $700 + PEC ad spend |
| PEC Google Organic (SEO) | $400 |
| PEC Website | $400 |
| PEC Meta | Calculated from Coating Launch emails |
| PEC Angi | Confirm with Dylan |
| PEC Repeat Customer | $0 |
| PEC Referral | $0 |
| PEC Facebook Organic | $0 |
| FTP Google Organic (SEO) | $400 |
| FTP Website | $400 |
| FTP Google PPC | $700 + FTP ad spend (if row exists) |
| FTP Angi | Confirm with Dylan |
| FTP Repeat Customer | $0 |
| FTP Referral | $0 |
| FTP Facebook Organic | $0 |
| FTP Word of Mouth | $0 |
| FTP Walk In | $0 |
| FTP Other | $0 |
| PEC Other | $0 |

### Step 4. Verify Campaign Spend

Re-run the CSV export JavaScript to confirm all column M values saved correctly. Cross-check the summary section (rows 3-24) by changing the period dropdown in B3 to the month you just updated.

---

## LEADS, ESTIMATES, AND SALES DATA (Columns D, G, J)

This section covers entering actual performance data from DripJobs Metrics into the MBP Marketing Plan tab. Run this after campaign spend is entered, or as a separate pass.

### Step 5. Pull Data from DripJobs Metrics

1. Go to `https://app.dripjobs.com/metrics`
2. Switch to the **PEC** account via Tenant Admin (building icon, top-right header)
3. Set the date range to the target month (1st through last day)
4. For each lead source shown in DripJobs, record:
   - **Leads** (new leads created that month)
   - **Estimates/Booked** (jobs won/booked)
   - **Sales $** (total revenue from booked jobs)
5. Switch to the **FTP** account and repeat

### Step 6. Map DripJobs Sources to MBP Categories

Use the Lead Source Mapping Doc (see ASSETS & LINKS) to convert DripJobs source names to MBP row categories. Key mappings:

**PEC:**
- Coating Launch = PEC Meta
- Google = PEC Google Organic (SEO)
- Google PPC = PEC Google PPC
- Website = PEC Website
- angi = PEC Angi
- Facebook = PEC Facebook Organic
- Other, Saw our truck, Yard Sign, Walk In, Jim self-gen = PEC Other

**FTP:**
- angi = FTP Angi
- Repeat Customer = FTP Repeat Customer
- Referral = FTP Referral
- Google = FTP Google Organic (SEO)
- Contact Form = FTP Website
- Other, Exterior, Exterior Painting, Vehicle/Ad, Yard Sign = FTP Other

**Exclusion:** "No Lead Source" entries = DO NOT COUNT. Flag these for Dusty to tag in DripJobs before they hit the MBP.

### Step 7. Enter Values in Columns D, G, and J

1. Use the Name Box to navigate to each cell (e.g., "D28")
2. Type the value as a plain number (no $ sign for columns D and G; sales in column J also plain number)
3. Press **Tab** to confirm (not Enter)
4. Repeat for all rows in the target month

**Columns:**
- **D** = Leads Actual (count of new leads)
- **G** = Estimates/Booked Actual (count of jobs won)
- **J** = Sales Actual (dollar amount of booked jobs)

### Step 8. Verify All Data

Re-run the CSV export JavaScript (see Step 2) but check columns D, G, and J in addition to M. Confirm every row matches the DripJobs data.

---

## TOOLS/MATERIALS

- Google Chrome (signed into dylan@finishingtouchpaintingaz.com)
- Outlook (for Coating Launch email search)
- MBP 2026 Google Sheet (link above)
- Chrome DevTools console (for CSV export verification)

---

## DO NOT EDIT

- **Column N** (Var %) contains an ARRAYFORMULA. Never overwrite.
- **Columns A and B** use data validation dropdowns. Do not type freeform text.
- **Do not insert rows.** The sheet is protected by BT Academy.
- **Do not edit rows 3-24** (summary section). These auto-calculate from detail rows.

---

## KNOWN ROW GAPS (as of April 2026)

The following lead source rows are **missing** from the sheet and cannot be added due to BT Academy protection:

| Month | Missing Row | Impact |
|-------|------------|--------|
| January | FTP Google PPC | $700 mgmt fee has no row |
| February | FTP Google PPC | $700 mgmt fee has no row |
| March | PEC Google PPC | $700+ mgmt/ad fee has no row |
| March | FTP Google PPC | $700 mgmt fee has no row |

Note: "FTP Google PPC" may not exist in the column B dropdown validator. The subtotals section uses "FTP Google Ads" which may be the correct dropdown label. Needs testing.

**Action required:** Dylan needs to request these rows from BT Academy support, or use the blank rows between month blocks (R57-59) to add them using the dropdown selectors. Do NOT attempt to type freeform values into columns A or B.

---

## COMMON MISTAKES

1. **Entering PEC Meta as a fixed $3,000.** It is NOT fixed. You must calculate it from Coating Launch weekly emails each month. The actual amounts vary significantly (Jan: $2,200, Feb: $1,775, Mar: $1,721 in Q1 2026).

2. **Pressing Enter instead of Tab after entering a value.** Enter moves the cursor down to the next row, which can accidentally overwrite data in the row below. Always use Tab to confirm, which moves right (safe direction).

3. **Not verifying after entry.** Cell navigation in Google Sheets via Name Box can misfire. Always run the CSV export verification after completing all entries to catch any values that landed in wrong cells.

---

## REVISION HISTORY

| Date | Author | Change |
|------|--------|--------|
| 2026-04-07 | Cowork VA | v1.0 -- SOP created. Documented recurring costs, row structure, and known gaps. |
| 2026-04-07 | Cowork VA | v2.0 -- Major revision. Fixed PEC Meta from flat $3,000 to variable (calculated from Coating Launch emails). Fixed SEO split amounts. Added Outlook email pull procedure. Updated Known Row Gaps (Jan FTP Website exists). Added Common Mistakes section. Added Angi and zero-spend source entries. |
| 2026-04-07 | Cowork VA | v2.1 -- Added DripJobs leads/booked/sales data entry procedure (Steps 5-8, columns D/G/J). Expanded PURPOSE and ASSETS sections. Added lead source mapping reference. |

---

Source: Marketing Manager | Generated 2026-04-07
