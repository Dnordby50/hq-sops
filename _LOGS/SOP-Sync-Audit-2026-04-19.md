# SOP Sync Audit — Drive vs Obsidian vs GitHub

**Date:** 2026-04-19
**Scope:** Verify every SOP is synced across the three sources of truth and identify why OPS SOPs in Drive are missing from the dashboard.

---

## Headline

Drive has 48 files across all SOP folders. Local Obsidian (= GitHub hq-sops, which the dashboard reads from) has 24 distinct SOPs plus 4 legitimate .md/.docx pairs. The 24 that are properly numbered and filed sync cleanly. The 18+ files that are missing from the dashboard are NOT sync failures. They are Drive files that were never cleaned up, numbered, or extracted into proper SOPs in the first place. The sync is working. The problem is Drive has never been fully deduplicated or migrated.

**Obsidian Git plugin status:** Local and origin/main are in sync. Last commit was 2026-04-14 09:54. Nothing new has been committed in the last 5 days. If you have been editing SOPs in Obsidian since then, the plugin may have stopped auto-pushing. Verify it is still running.

**Drive Bridge status:** The `folderTree` action works. The `list` action throws a DriveApp error on any subfolder. Audit performed via direct browser navigation instead. The bridge needs to be fixed before it can reliably process inbox SOPs.

---

## The OPS gap you're seeing

Drive PEC/OPS has 19 files. Local (and therefore the dashboard) has 12. The 7 that do not appear on the dashboard:

| File in Drive PEC/OPS | Type | Why it is missing |
|---|---|---|
| Concrete_Prep_Playbook.mp4 | Video | Training video, not an SOP. Belongs in TRAINING/PEC/ |
| PEC_Concrete_Patching.mp4 | Video | Training video, not an SOP. Belongs in TRAINING/PEC/ |
| Epoxy System Training | Google Doc | This is the SOURCE doc you extracted PEC-OPS-003 through 012 from. Not a live SOP. Archive it. |
| Job Walk SOP | Google Doc | Legacy "Field Job Walk SOP - Landen." Landen is no longer in sales. Needs rewrite or retire. |
| PEC SOP for BusyBusy | Google Doc | Legacy unnumbered. Should be extracted and numbered (PEC-OPS-013). |
| PRESCOTT EPOXY – CHANGE ORDER SOP | Google Doc | Legacy unnumbered, Dec 2025. Should be extracted and numbered (probably PEC-ADMIN-003). |
| PEC-OPS-002 -- Daily Crew Schedule Briefing.md | Markdown | Duplicate of the .docx version. Violates your Drive-is-.docx-only rule. Delete. |

The first four are legitimately not SOPs. The last three are real gaps that need action.

---

## Full diff by folder

### PEC/OPS — Drive 19, Synced 12
Legacy / unfiled: Concrete_Prep_Playbook.mp4, PEC_Concrete_Patching.mp4, Epoxy System Training, Job Walk SOP, PEC SOP for BusyBusy, PRESCOTT EPOXY – CHANGE ORDER SOP, PEC-OPS-002 .md duplicate.

### PEC/ADMIN — Drive 7, Synced 2
Synced: PEC-ADMIN-001, PEC-ADMIN-002.
Misfiled here (these are HR docs, not admin SOPs): PEC-Sales-Consultant-Competency-Model.docx, PEC-Sales-Consultant-Employment-Agreement.docx, PEC-Sales-Consultant-Job-Description.docx, PEC-Sales-Consultant-KPI-Framework.docx. These belong in 03 - People & HR/PEC Sales Consultant/.
Legacy: Social Media SOP (Google Doc, unnumbered). Extract and number.

### PEC/FIN — Drive 3, Synced 2
Synced: PEC-FIN-001, PEC-FIN-002.
Legacy: "PEC Receipt SOP" (unnumbered stub). Memory flagged this as a gap. Finish it, number it PEC-FIN-003.

### PEC/SALES — Drive 2, Synced 2 (partial)
Synced: PEC-SALES-002 (as Google Doc in Drive, .md in local).
Legacy: "PEC Sales SOP" (unnumbered). Extract, number, or retire.
**Missing from Drive:** PEC-SALES-001 -- MBP Marketing Plan Monthly Update.docx exists locally but is NOT in Drive. Needs to be uploaded.

### PEC/SAFETY — Drive 1, Synced 1
Clean. PEC-SAFETY-001 matches.

### Shared/ADMIN — Drive 10, Synced 1
Only SHARED-ADMIN-002 exists in both. 9 files in Drive are unfiled or duplicate:
- Andrew-Weekly-Cadence-and-Schedule.docx (likely superseded by PEC-OPS-001 — verify and delete)
- Dusty-Desk-Card.docx (unnumbered)
- FTP-Org-Chart.html (not an SOP, org chart)
- Lead-Follow-Up-Script.docx (unnumbered, was updated Apr 16)
- Office-Assistant-Duties (Google Doc, unnumbered)
- PEC-ADMIN-001_--_Price_List_Organization.docx (DUPLICATE of the one in PEC/ADMIN)
- PEC-Org-Chart.html (not an SOP)
- Quo_Phone_SOP.docx (unnumbered)
- Shop-Cleaning-Procedure (Google Doc, unnumbered)
- Brand Guidelines (subfolder, not counted in the 10)

**Missing from Drive:** SHARED-ADMIN-001 -- MBP Monthly Marketing Spend Update.docx exists locally, not uploaded to Drive.

### Shared/FIN — Drive 1, Synced 0
- Payroll-SOP (Google Doc, unnumbered). Extract, number SHARED-FIN-001, fix filename. Local has `SH-FIN-001 -- Job Costing Workflow (Protiv Replacement).md` which uses a non-standard prefix (SH instead of SHARED) — rename to match convention.

### Shared/OPS — Drive 2, Synced 0
- Customer Journey Map.html (exists locally in _LOGS, misplaced in Drive)
- Project Manager.docx (unnumbered legacy)

### Shared/SALES — Drive 2, Synced 0 (partial)
Legacy: "SOP- Sales Process" (Google Doc, has the accidental star mentioned in memory), "Total Sales Training" (Google Doc).
**Missing from Drive:** SHARED-SALES-001 -- On Site Referral Pipeline.docx exists locally, not uploaded.

### FTP — Drive 1 (in SALES only), Synced 0
- FTP/SALES: "Interior Paint Estimate SOP" (Google Doc, unnumbered). Should become FTP-SALES-001.
- FTP/OPS, FTP/ADMIN, FTP/FIN, FTP/SAFETY are all empty.
- Local FTP folder is also empty.
- **FTP still has zero numbered SOPs anywhere.** This remains the #1 gap per prior memory notes.

---

## Numbering and duplication issues

- **PEC-FIN-001 conflict:** Local has "Monthly Job Costing Materials Entry" filed as PEC-FIN-001. _REVIEW/ has "RETIRED-PEC-FIN-001 -- Protiv ProPay Close-Out SOP.md" (already retired, good).
- **SH- vs SHARED- prefix:** `SH-FIN-001 -- Job Costing Workflow (Protiv Replacement).md` uses "SH-" which breaks the naming convention. Rename to SHARED-FIN-001 (or move Job Costing Workflow to its own SOP number after extracting the Payroll-SOP Google Doc).
- **Andrew duplicate:** `Andrew-Weekly-Cadence-and-Schedule.docx` in Shared/ADMIN likely overlaps with `PEC-OPS-001 Andrew Remote VA`. Compare content, retire one.
- **Price List duplicate:** `PEC-ADMIN-001_--_Price_List_Organization.docx` exists in BOTH Shared/ADMIN and PEC/ADMIN. The Shared copy should be deleted.

---

## Dashboard wiring

Memory from 2026-04-12 says the hq-prescott.netlify.app dashboard SOPS tab was NOT yet wired to the GitHub repo and showed "SOP library not yet configured." Check whether this changed. If it is now reading from GitHub, the file list will match local exactly. The dashboard cannot show the unfiled Drive legacy content until those files are extracted, numbered, and committed.

---

## Priority action list (ranked)

1. **Unblock the dashboard** — verify hq-prescott.netlify.app is pulling from `Dnordby50/hq-sops` and the Netlify build is current. Memory says local build was ahead of production as of Apr 12.
2. **Fix Obsidian Git plugin** — no commits since Apr 14. Either nothing has changed (unlikely given the gaps above) or the plugin stopped.
3. **Fix the Drive Bridge `list` action** — currently broken, which blocks any automated inbox processing.
4. **Extract 3 real SOPs from Drive legacy docs:**
   - PEC SOP for BusyBusy → PEC-OPS-013
   - PRESCOTT EPOXY CHANGE ORDER SOP → PEC-ADMIN-003
   - Interior Paint Estimate SOP → FTP-SALES-001 (first FTP SOP)
5. **Move misfiled files:**
   - 4 Sales Consultant HR docs out of PEC/ADMIN into `03 - People & HR/PEC Sales Consultant/`
   - 2 training videos out of PEC/OPS into TRAINING/PEC/
   - Customer Journey Map out of Shared/OPS into _LOGS/
   - Org charts out of Shared/ADMIN (not SOPs)
6. **Delete duplicates and .md files from Drive:**
   - PEC-OPS-002 -- Daily Crew Schedule Briefing.md (duplicate, violates Drive .docx-only rule)
   - PEC-ADMIN-001 in Shared/ADMIN (duplicate of PEC/ADMIN version)
   - Andrew-Weekly-Cadence in Shared/ADMIN (if content matches PEC-OPS-001)
7. **Upload to Drive (3 files missing from Drive but exist locally as .docx):**
   - PEC-SALES-001 -- MBP Marketing Plan Monthly Update.docx
   - SHARED-SALES-001 -- On Site Referral Pipeline.docx
   - SHARED-ADMIN-001 -- MBP Monthly Marketing Spend Update.docx
8. **Consolidate or retire 7 legacy unnumbered Google Docs in Drive** after you decide which represent live SOPs worth keeping.
9. **Rename SH-FIN-001** locally to match SHARED- convention.

---

## What is actually working

- Local Obsidian to GitHub sync is intact (as of the last commit).
- The 12 PEC/OPS SOPs that are properly numbered and filed are consistent across all three locations.
- PEC-SAFETY-001 is clean across all three.
- Drive folder structure matches the taxonomy defined in SOP-Filing-Prompt.md.

Source: SOP Hub | Generated 2026-04-19
