# PEC-FIN-001 -- Monthly Job Costing Materials Entry

**SOP Version:** 1.0  
**Last Updated:** 2026-04-10  
**Owner:** Dylan (Prescott Epoxy)  
**Function:** Finance  
**Process:** Monthly job costing reconciliation and materials cost entry

---

## Purpose
This SOP documents the monthly process for entering material costs into the MBP 2026 Job Costing Pipeline for Prescott Epoxy jobs. The workflow ensures all completed jobs have accurate material costs recorded, enabling accurate margin analysis and financial reporting.

---

## Prerequisites & Access
- Access to MBP 2026 Google Sheet (ID: `1vlumbi2mh_mjtmO1ZiTxMy0BTXbtNCNV-FOM-LVZ_s0`)
- Access to PEC Order Sheet (ID: `16vfUHggITTuz53RRWFepQWNtInJmN1JsZ7qt3MeRGcI`)
- Access to Epoxy Price List (ID: `1S0EeQKa_mPZ0IFujGrRBdS3T2UYQFVAV7Kk9eL3i92I`)
- Write permissions on MBP 2026 and ability to create/edit documents
- Microsoft Word for creating verification documents
- Current month's completed job data from PEC operations

---

## Workflow Steps

### Step 1: Identify Target Jobs
1. Open **MBP 2026 Google Sheet** (ID: `1vlumbi2mh_mjtmO1ZiTxMy0BTXbtNCNV-FOM-LVZ_s0`)
2. Navigate to the **JCC Pipeline tab** (GID: `1816501272`)
3. Filter column A (Month) for the target month (e.g., March 2026)
4. Identify all rows where column B (Company) = **PEC**
5. Note the complete list of PEC jobs for the month before proceeding

### Step 2: Find Jobs Missing Material Costs
1. In the filtered view, examine **column S (MATERIALS VAR)**
2. Identify all jobs with empty or missing material cost values
3. Create a list of job names/IDs that need material cost entry
4. *Note: Column T (Material %) will auto-calculate once column S is populated*

### Step 3: Source Material Data from Order Sheet
1. Open **PEC Order Sheet** (ID: `16vfUHggITTuz53RRWFepQWNtInJmN1JsZ7qt3MeRGcI`)
2. **Check BOTH tabs:**
   - "NEW ORDER SHEET" (current/in-progress jobs)
   - "COMPLETED JOBS" (completed jobs archive)
3. For each job identified in Step 2, match by customer last name across both tabs
4. List all materials used for that job, including:
   - Product name (exact as listed on PEC Order Sheet)
   - Quantity ordered/used

**⚠️ Common Issue:** Some jobs may appear in BOTH tabs. Confirm with Dylan which version to use before proceeding.

### Step 4: Retrieve Current Unit Prices
1. Open **Epoxy Price List** (ID: `1S0EeQKa_mPZ0IFujGrRBdS3T2UYQFVAV7Kk9eL3i92I`)
2. Look up the current unit price for each material identified in Step 3
3. Record both the product name and unit price for verification

**Standard Material Pricing Reference (as of 2026-04-10):**
- 1100SL Prepigmented (Light Gray, Sandstone, Taupe, Haze Gray): $144.27/kit
- 1100SL Clear (Clear Gloss): $139.03/kit
- MVB Clear kit: $214.04/kit
- Polyaspartic 2-gal standard: $153.02/kit
- High Wear Urethane: $199.36/kit
- Flake standard 40lb: $87.44/box
- Flake special/Torginol: $136.62/box
- Metallic Epoxy: $157.10/kit
- Metallic Pigment: $63.70/pack
- U-Tint: $16.37/pack
- Self Leveler: $32.72/bag
- Anti Skid/50 Tex: $11.05/unit
- Ameripolish Densifier: $71.86/gal
- Ameripolish Classic Stain: $75.27/gal

### Step 5: Calculate Total Material Cost Per Job
For each job:
1. Multiply quantity × unit price for each material used
2. Sum all material costs to get **Total Material Cost** for the job
3. Round to nearest cent (currency standard)

**Formula Example:**
```
Total Material Cost = (Qty_Material1 × Price_Material1) + (Qty_Material2 × Price_Material2) + ...
```

### Step 6: Create Verification Document
1. Open **Microsoft Word**
2. Create a new document titled: `PEC-JCC-[MONTH]-Materials Verification-[DATE].docx`
   - Example: `PEC-JCC-March-Materials Verification-2026-04-10.docx`
3. List each job with:
   - Job name/customer
   - Materials used (product name + quantity)
   - Unit price per material
   - Extended cost per material (qty × unit price)
   - **Total Material Cost** (bold/highlighted)
4. Include header: `Source: Back End Office | Generated [DATE]`
5. Save to: **09 - Inbox/** folder in Google Drive

### Step 7: Review & Approval from Dylan
1. Share the verification document with Dylan via Slack
2. Wait for Dylan's review and approval before entering data
3. Make any corrections Dylan requests
4. Obtain explicit approval before proceeding to Step 8

**⚠️ Rule:** Never enter material costs without Dylan's explicit approval of the verification document.

### Step 8: Enter Material Costs into MBP
1. Return to **MBP 2026 > JCC Pipeline tab**
2. Use the **Name Box** (top-left cell reference input) to navigate to column S of the first target job
3. Enter the **Total Material Cost** (from Step 5) into **column S (MATERIALS VAR)** for each job
4. After each entry:
   - Wait **10+ seconds** before editing the next cell (MBP recalculates slowly)
   - Verify that **column T (Material %)** auto-populates with a reasonable percentage
   - Verify that **column U (Wages)** is NOT overwritten (read-only for this process)

**⚠️ Critical:** The MBP sheet has 52+ tabs and is computationally heavy. Do NOT edit rapidly; allow recalculation time between entries.

### Step 9: Generate Labor vs. Materials Breakdown with Bonus Calculations
1. After all material costs are entered, create a labor vs. materials breakdown document
2. For each job, calculate labor budget allocation based on system type:
   - **Flake systems and metallics:** 20% of labor budget
   - **Grind & seal systems:** 30% of labor budget
3. Document bonus calculations (if applicable per company policy)
4. Create summary showing material costs, labor allocation, and margin impact
5. Save to **09 - Inbox/** with naming: `PEC-JCC-[MONTH]-Labor Breakdown-[DATE].docx`

### Step 10: Verify Margin Thresholds
1. After entry is complete, review all jobs in the JCC Pipeline
2. Identify any jobs with Gross Profit margin **below 40%** (PEC threshold)
3. **Flag these jobs** in a note or separate document for Dylan's review
4. Include notes on why margin is below threshold (material cost overages, pricing issues, etc.)

**⚠️ Margin Rule:** PEC minimum threshold is 40% GP. Any job below this requires investigation.

### Step 11: Report to Dylan via Slack
1. Send **one message** to Dylan reporting completion with:
   - Number of jobs processed
   - Date range (month)
   - Any flagged jobs (below margin threshold)
   - Link to verification document location
   - Any edge cases or data discrepancies discovered
2. Format: Clear, concise bullet points
3. Example message structure:
   ```
   PEC Monthly Job Costing - March 2026 Complete
   • 12 jobs processed
   • 2 jobs flagged below 40% margin threshold
   • Verification doc: [link]
   • Edge case: Customer XYZ job in both Order Sheet tabs - used COMPLETED JOBS version per your call
   ```

---

## Important Rules & Pitfalls

### Data Entry Safety
- **Never overwrite column U (Wages)** — this column is read-only for material entry
- **Only edit column S (MATERIALS VAR)** — this is the correct target column
- Do not manually edit column T (Material %) — it auto-calculates after column S is populated

### Common Data Issues
- Some jobs appear in **BOTH Order Sheet tabs** (NEW and COMPLETED) — confirm with Dylan which to use
- Jobs with **no Order Sheet entry** need Dylan's input — never guess or estimate material costs
- **Missing price data** on Epoxy Price List — escalate to Dylan before proceeding
- MBP sheet **recalculates slowly** with 52+ tabs — wait 10+ seconds between cell edits to allow proper calculation

### Navigation Tips
- Use the **Name Box** (top-left cell reference input) to jump directly to cells (faster than scrolling)
- Filter column A by month to isolate target jobs, reduces accidental edits to other months
- Keep the Epoxy Price List open in a separate window during data entry for quick reference

### Verification Standards
- All material costs must be **pre-approved by Dylan** via verification document
- Verification documents must include all component costs (product name, qty, unit price, extended cost)
- Document naming must follow: `PEC-JCC-[MONTH]-[Description]-[DATE].docx`
- Save all verification docs to **09 - Inbox/** before archiving

---

## Glossary

| Term | Definition |
|------|-----------|
| **JCC Pipeline** | Job Costing Pipeline tab in MBP 2026; tracks all jobs with cost and revenue data |
| **MATERIALS VAR** | Column S in JCC Pipeline; total material cost for each job |
| **Material %** | Column T in JCC Pipeline; percentage of revenue consumed by material costs (auto-calculated) |
| **Wages** | Column U in JCC Pipeline; labor cost allocation (read-only for material entry) |
| **Order Sheet** | PEC internal document tracking materials ordered/used per job across two tabs |
| **Epoxy Price List** | Master pricing document for all PEC materials with current unit costs |
| **Verification Document** | Word doc prepared before MBP entry showing all material costs pre-approved by Dylan |
| **Margin Threshold** | PEC minimum 40% Gross Profit; jobs below flagged for investigation |

---

## Escalation & Edge Cases

### When to Ask Dylan
- A job appears in **both Order Sheet tabs** (NEW and COMPLETED)
- A material on the Order Sheet is **missing from the Epoxy Price List**
- A job has **no Order Sheet entry** (no materials documented)
- A job's calculated material cost results in **margin below 40%** (PEC threshold)
- Material quantities seem **unusually high or low** compared to similar jobs
- **Conflicting data** between Order Sheet and MBP (job cost already entered vs. new materials list)

### When to Stop & Escalate
- If more than 2-3 jobs have missing Order Sheet entries
- If the Epoxy Price List is significantly out of date (check last update date)
- If material costs would drive more than 20% of jobs below margin threshold
- If Dylan's approval of verification doc includes requested edits — create revised version and re-submit

---

## Tools & Resources

| Resource | ID/Link | Purpose |
|----------|---------|---------|
| MBP 2026 Google Sheet | `1vlumbi2mh_mjtmO1ZiTxMy0BTXbtNCNV-FOM-LVZ_s0` | Job costing database & KPI dashboard |
| JCC Pipeline Tab | GID: `1816501272` | Monthly job cost tracking |
| PEC Order Sheet | `16vfUHggITTuz53RRWFepQWNtInJmN1JsZ7qt3MeRGcI` | Materials list per job |
| Epoxy Price List | `1S0EeQKa_mPZ0IFujGrRBdS3T2UYQFVAV7Kk9eL3i92I` | Current unit pricing |
| Verification Document Template | Microsoft Word | Pre-entry approval document |
| Output Location | 09 - Inbox/ (Google Drive) | Where to save all final documents |

---

## Related SOPs
- (To be linked as additional finance SOPs are created)

---

## Changelog

| Date | Change | Author |
|------|--------|--------|
| 2026-04-10 | Initial version created after completing March 2026 PEC job costing | Dylan (Cowork VA) |

---

**Next Review Date:** 2026-05-10  
**Review Frequency:** Monthly (after each month's job costing completion)
