# SHARED-FIN-001 Job Costing Workflow (Protiv Replacement)

<!-- Renamed from SH-FIN-001 to SHARED-FIN-001 on 2026-04-19 to match naming convention; file moved from Shared/ADMIN to Shared/FIN. -->


**SOP Version:** 1.0
**Last Updated:** 2026-04-12
**Owner:** Dylan / Cowork VA
**Function:** Finance (Shared — PEC + FTP)
**Replaces:** Protiv job costing system (cut 2026-04-10)

---

## Purpose

This SOP documents the complete end-to-end workflow for job costing across both Prescott Epoxy (PEC) and FTP, using the Job Costing Master Google Sheet. It replaces all Protiv-based costing and covers every step from job booking through final margin review and bonus calculation.

---

## System Overview

### Data Flow

```
DripJobs (job booked)
    ↓
Booked Jobs Tracker (Zapier auto-populates)
    ↓
Job Costing Master — JCC Pipeline tab (job row created)
    ↓                         ↓
Material costs entered    Crew hours entered
(from PEC Order Sheet     (from Busy Busy CSV export)
 + Epoxy Price List)
    ↓                         ↓
    └──────────┬──────────────┘
               ↓
    GP% auto-calculates per job
               ↓
    Crew Hours & Bonus tab (per-person split + bonus calc)
               ↓
    Watchdog monitoring flags issues
               ↓
    Dylan reviews flagged jobs
```

### Key Systems

| System | Purpose | Sheet ID |
|---|---|---|
| Job Costing Master | Central job costing database | `1cb2QZLgK-wWQOX1bzB8SBv3RN6e-FXTEbI7AFfAr1HQ` |
| PEC Order Sheet | Materials ordered per PEC job | `16vfUHggITTuz53RRWFepQWNtInJmN1JsZ7qt3MeRGcI` |
| Epoxy Price List | Unit pricing for PEC materials | `1S0EeQKa_mPZ0IFujGrRBdS3T2UYQFVAV7Kk9eL3i92I` |
| Booked Jobs Tracker | Auto-populated job list from DripJobs | `1oNMMiuPmtrmu-x9Vxcy4kz0xxzQV00WNCGvk35rGLr4` |
| FTP Daily Progress Tracker | Doug's daily job walk notes | `1mbYOKJCSny_dcsIyy3dsImg5YuIDu3GVPuBLR-7OPYg` |
| MBP 2026 | Master business plan (52+ tabs) | `1vlumbi2mh_mjtmO1ZiTxMy0BTXbtNCNV-FOM-LVZ_s0` |

### Job Costing Master — Tab Guide

| Tab | Purpose | Data State (2026-04-12) |
|---|---|---|
| JCC Pipeline | Per-job cost tracking. Columns: Month, Job ID, Sales Team, Job Type, Crew, Revenue Stream, Revenue, Hours, Est. Hours, Materials, Wages, GP%. ~1,000+ job rows from MBP history. | Populated with historical data. Row 66 = headers. Row 69+ = job data. |
| Job Type Rates | Labor budget % lookup per job type. Used to calculate labor budget allocation. | Fully populated — 12 job types confirmed by Dylan. |
| Crew Hours & Bonus | Per-person crew hour split with bonus eligibility calculation. | Headers only — awaiting Busy Busy CSV integration. |

---

## Roles & Responsibilities

| Step | Who | What |
|---|---|---|
| Job booking | Zapier (auto) | Writes to Booked Jobs Tracker when DripJobs status changes |
| Job row in JCC Pipeline | Cowork VA or Dylan | Ensure new completed jobs appear in JCC Pipeline |
| Material cost sourcing | Cowork VA | Pull from PEC Order Sheet + Epoxy Price List |
| Material cost entry | Cowork VA (with Dylan approval) | Enter into JCC Pipeline column S |
| Crew hours entry | Andrew → Cowork VA (pending Busy Busy integration) | Enter actual labor hours from Busy Busy time tracking |
| Bonus calculation | Cowork VA | Calculate in Crew Hours & Bonus tab per bonus rules |
| Margin review | Dylan | Review flagged jobs from Watchdog alerts |
| Monthly reconciliation | Cowork VA + Dylan | Ensure all jobs for the month are costed |

---

## Workflow Steps

### Phase 1: Job Completion → Data Capture

**Trigger:** A job reaches "completed" status in DripJobs.

#### Step 1.1: Verify Job Row Exists in JCC Pipeline

1. Open Job Costing Master > JCC Pipeline tab
2. Filter column A (Month) for the current month
3. Confirm the completed job appears with:
   - Month (column A)
   - Job Address/ID (column B)
   - Sales Team (column E)
   - Job Type (column F)
   - Crew/Sub Name (column G)
   - Revenue Stream — PEC or FTP (column H)
   - Revenue (column I)
   - Hours and Est. Hours (columns K, L)

4. **If the job is missing:** Add it manually. Source data from Booked Jobs Tracker and DripJobs.

#### Step 1.2: Capture Crew Hours (Busy Busy → Sheet)

**Current process (manual, until Busy Busy CSV automation is built):**

1. Export crew hours from Busy Busy for the job
2. Record total hours by crew member
3. Enter total actual hours into JCC Pipeline column K (HOURS)
4. Cross-check against column L (Est. Hours) — flag if variance > 30%

**Future process (automated):**
- Busy Busy CSV export automation will wire crew hours directly into the Crew Hours & Bonus tab
- JCC Pipeline HOURS column will auto-pull from Crew Hours & Bonus totals

---

### Phase 2: Material Cost Entry (PEC Jobs)

**Applies to:** PEC jobs only. FTP jobs do not use the PEC Order Sheet.

#### Step 2.1: Source Materials from Order Sheet

1. Open PEC Order Sheet (`16vfUHggITTuz53RRWFepQWNtInJmN1JsZ7qt3MeRGcI`)
2. Check **both** tabs:
   - "NEW ORDER SHEET" (current/in-progress)
   - "COMPLETED JOBS" (archived)
3. Match by customer last name
4. List all materials and quantities

**Edge case:** Job appears in both tabs → confirm with Dylan which to use.

#### Step 2.2: Look Up Unit Prices

1. Open Epoxy Price List (`1S0EeQKa_mPZ0IFujGrRBdS3T2UYQFVAV7Kk9eL3i92I`)
2. Find current unit price for each material
3. Standard pricing reference (as of 2026-04-10):

| Material | Unit Price |
|---|---|
| 1100SL Prepigmented (Light Gray, Sandstone, Taupe, Haze Gray) | $144.27/kit |
| 1100SL Clear (Clear Gloss) | $139.03/kit |
| MVB Clear kit | $214.04/kit |
| Polyaspartic 2-gal standard | $153.02/kit |
| High Wear Urethane | $199.36/kit |
| Flake standard 40lb | $87.44/box |
| Flake special/Torginol | $136.62/box |
| Metallic Epoxy | $157.10/kit |
| Metallic Pigment | $63.70/pack |
| U-Tint | $16.37/pack |
| Self Leveler | $32.72/bag |
| Anti Skid/50 Tex | $11.05/unit |
| Ameripolish Densifier | $71.86/gal |
| Ameripolish Classic Stain | $75.27/gal |

**If a material is missing from the price list:** Stop and ask Dylan. Never estimate.

#### Step 2.3: Calculate Total Material Cost

For each job:
```
Total Material Cost = Σ (Quantity × Unit Price) for all materials
```
Round to nearest cent.

#### Step 2.4: Create Verification Document

1. Create a Word doc: `PEC-JCC-[MONTH]-Materials Verification-[DATE].docx`
2. For each job, list:
   - Job name/customer
   - Each material: product name, quantity, unit price, extended cost
   - **Total Material Cost** (bold)
3. Header: `Source: Back End Office | Generated [DATE]`
4. Save to 09 - Inbox/ in Google Drive

#### Step 2.5: Get Dylan's Approval

1. Share verification doc with Dylan via Slack
2. **Wait for explicit approval before entering any data**
3. Make corrections if requested
4. Do not proceed to Step 2.6 without a "yes" from Dylan

#### Step 2.6: Enter Material Costs into JCC Pipeline

1. Navigate to JCC Pipeline > column S (MATERIALS VAR)
2. Enter Total Material Cost for each approved job
3. **Critical rules:**
   - Wait 10+ seconds between cell edits (MBP-derived sheet recalculates slowly)
   - Verify column T (Material %) auto-populates after entry
   - **Never touch column U (Wages)** — read-only for this step
   - Use the Name Box (top-left) for navigation, not scrolling

---

### Phase 3: Labor Cost Entry (Both PEC + FTP)

#### Step 3.1: Determine Labor Budget

1. Open Job Type Rates tab in Job Costing Master
2. Find the job type and its Labor Budget %:

| Job Type | Labor Budget % | Notes |
|---|---|---|
| Flake Garage | 20% | PEC — Dylan confirmed |
| Flake Patio | 20% | PEC — Dylan confirmed |
| Grind and Seal | 25% | PEC — Dylan confirmed |
| Grind Only | 25% | PEC — same as Grind and Seal |
| Polishing | 40% | PEC — Dylan confirmed |
| Quartz Patio | 30% | PEC — Dylan confirmed |
| Specialty Epoxy | varies | PEC — ASK DYLAN per job |
| Specialty | 32.5% | FTP — 50% GP target |
| Commercial Interior | 32.5% | FTP — 50% GP target |
| Commercial Exterior | 32.5% | FTP — 50% GP target |
| Residential Interior | 32.5% | FTP — 50% GP target |
| Residential Exterior | 32.5% | FTP — 50% GP target |

3. Calculate: `Labor Budget $ = Revenue × Labor Budget %`

#### Step 3.2: Enter Actual Labor Cost

1. Source actual labor cost from:
   - Busy Busy time tracking exports (hours × crew pay rate)
   - Or payroll records if Busy Busy isn't available
2. Enter into JCC Pipeline column U (Wages)
3. The sheet calculates: `Remaining Budget = Labor Budget $ - Actual Labor Cost`

---

### Phase 4: Crew Hours & Bonus Calculation

**Prerequisite:** Material costs AND labor costs must both be entered in JCC Pipeline before proceeding.

#### Step 4.1: Enter Job into Crew Hours & Bonus Tab

For each completed and costed job, add a row to the Crew Hours & Bonus tab:

| Column | Data Source |
|---|---|
| A: Job Address/ID | JCC Pipeline column B |
| B: Job Type | JCC Pipeline column F |
| C: Revenue | JCC Pipeline column I |
| D: Labor Budget % | Job Type Rates tab lookup |
| E: Labor Budget $ | C × D (auto-calc) |
| F: Actual Labor Cost | JCC Pipeline column U |
| G: Remaining Budget | E - F (auto-calc) |
| H: GP % | From JCC Pipeline (auto-calc) |
| I: Callback? | Yes/No — check with ops |
| J: Bonus Eligible? | Auto: GP ≥ 50% AND no callback |
| K: Bonus Pool (75%) | G × 0.75 (if eligible) |
| L: Total Crew Hours | Sum of individual crew hours |
| M+: Crew Name / Hours | Per-person hour split from Busy Busy |

#### Step 4.2: Bonus Eligibility Rules

A job qualifies for crew bonus when ALL of these are true:

1. **GP ≥ 50%** — Gross profit percentage meets threshold
2. **No callbacks** — Job completed without requiring a return visit
3. **Remaining labor budget > $0** — Job came in under labor budget

**Bonus amount:** 75% of remaining labor budget, split proportionally by crew hours.

```
Crew Member Bonus = (Bonus Pool) × (Their Hours / Total Crew Hours)
```

#### Step 4.3: Report Bonus Summary

After completing bonus calculations for a batch of jobs:
1. Summarize total bonus pool and per-person amounts
2. Send to Dylan via Slack for payroll processing
3. Include: job name, bonus pool, each crew member's share

---

### Phase 5: Margin Review & Watchdog Monitoring

#### Step 5.1: Automated Watchdog Checks (Daily)

The Job Costing Watchdog (Apps Script) runs daily at 7 AM and flags:

| Alert Type | Threshold | Action |
|---|---|---|
| GP below floor | PEC < 40%, FTP < 35% | CRITICAL — Dylan must investigate |
| GP below target | PEC < 51.6%, FTP < 47.7% | WARNING — review for patterns |
| Missing materials | Revenue > 0, col S empty | Enter material costs |
| Stale jobs | 14+ days past month-end, no costs | Prioritize costing |
| Hours overrun | Actual > 30% over estimate | Review estimating accuracy |
| Hourly rate below min | PEC < $120/hr, FTP < $75/hr | Flag for pricing review |
| Missing crew hours | Costed but no Crew H&B entry | Complete bonus calc |
| Data errors | #REF!, #VALUE! in cells | Fix formula issues |

#### Step 5.2: Monthly Reconciliation

At month-end (or within first week of following month):

1. Filter JCC Pipeline for the closing month
2. Verify **every** job has:
   - Revenue (column I) ✓
   - Material costs (column S) ✓ — PEC only
   - Wages (column U) ✓
   - GP% calculating correctly (column BZ) ✓
3. Flag any jobs still missing data → escalate to Dylan
4. Run Watchdog and resolve all alerts for the month
5. Report completion to Dylan via Slack:
   ```
   [Month] Job Costing Reconciliation Complete
   • X jobs processed (PEC: Y, FTP: Z)
   • Blended GP: XX.X% (PEC: XX.X%, FTP: XX.X%)
   • Jobs below GP floor: X
   • Total bonus pool: $X,XXX
   • Outstanding items: [list any]
   ```

---

## Margin Thresholds Reference

| Business | GP Floor (alert) | GP Target (MBP) | Labor Budget % | Min $/Hr |
|---|---|---|---|---|
| PEC | 40% | 51.6% | 20-40% by job type | $120 |
| FTP | 35% | 47.7% | 32.5% all types | $75 |

---

## Escalation Rules

### When to Stop and Ask Dylan

- A material has no entry on the Epoxy Price List
- A job appears in both Order Sheet tabs (NEW and COMPLETED)
- A job has no Order Sheet entry at all
- Calculated material cost would push GP below 40% (PEC) or 35% (FTP)
- Material quantities look unusually high or low vs. similar jobs
- More than 3 jobs in a month are missing data from source systems
- Specialty Epoxy job type — labor budget varies per job, always ask

### When to Flag but Continue

- GP between floor and target — log the alert, continue costing
- Hours variance between 20-30% — note it, not a blocker
- Crew Hours & Bonus tab backlog — costing comes first, bonus calc can follow

---

## Data Entry Safety Rules

1. **Never overwrite column U (Wages) during material entry** — it's a separate process
2. **Never manually edit auto-calculated columns** (T: Material %, GP columns)
3. **Wait 10+ seconds between cell edits** — the sheet has 52+ tabs worth of formulas inherited from MBP
4. **Use the Name Box** to navigate — faster and safer than scrolling through 1000+ rows
5. **Filter by month first** — reduces risk of editing wrong rows
6. **Always create a verification document before entering PEC material costs**
7. **Never enter costs without Dylan's approval** on the verification doc

---

## Tools & Access

| Resource | ID/Link | Access Level |
|---|---|---|
| Job Costing Master | `1cb2QZLgK-wWQOX1bzB8SBv3RN6e-FXTEbI7AFfAr1HQ` | Read-write (CFO + PM) |
| PEC Order Sheet | `16vfUHggITTuz53RRWFepQWNtInJmN1JsZ7qt3MeRGcI` | Read-write |
| Epoxy Price List | `1S0EeQKa_mPZ0IFujGrRBdS3T2UYQFVAV7Kk9eL3i92I` | Read-only |
| Booked Jobs Tracker | `1oNMMiuPmtrmu-x9Vxcy4kz0xxzQV00WNCGvk35rGLr4` | Read-only (Zapier-fed) |
| FTP Daily Progress Tracker | `1mbYOKJCSny_dcsIyy3dsImg5YuIDu3GVPuBLR-7OPYg` | Read-write |
| MBP 2026 | `1vlumbi2mh_mjtmO1ZiTxMy0BTXbtNCNV-FOM-LVZ_s0` | Read-write with caution |
| Dashboard Data | `1445T0CPavFCWEj2soegc599nCZrbWLgDsCnjQGChI74` | Append-only (CFO tab) |
| Watchdog Script | See deployment SOP | Read-only (web app) |

---

## Related SOPs

- **PEC-FIN-001** — Monthly Job Costing Materials Entry (legacy, specific to MBP JCC Pipeline tab — this SOP supersedes it for jobs entered into Job Costing Master)
- **Watchdog Deployment SOP** — `06 - Automations & Tech/Active Automations/Shared-CFO-JobCostingWatchdog-SOP-2026-04-12.md`

---

## Changelog

| Date | Change | Author |
|---|---|---|
| 2026-04-12 | Initial version — full Protiv replacement workflow | Cowork VA |

---

## What Changed from Protiv

| Before (Protiv) | After (Job Costing Master) |
|---|---|
| Protiv app for job costing | Google Sheets (Job Costing Master) |
| Costs entered in Protiv interface | Costs entered directly in JCC Pipeline columns S and U |
| Bonus calculated manually | Crew Hours & Bonus tab with formula-driven eligibility |
| No automated monitoring | Watchdog script runs daily, flags issues automatically |
| No cross-reference with hours | Hours variance tracked and flagged at 30% threshold |
| Manual reconciliation | Monthly reconciliation checklist with completion report |
| Siloed from MBP | JCC Pipeline mirrors MBP structure — same column layout |

---

**Next Review Date:** 2026-05-12
**Review Frequency:** Monthly (after each month's reconciliation)
