# SOP Bypass Projects Report

**Date:** 2026-04-19
**Scope:** Identify projects and workflows that are generating operational docs outside the SOP Hub — the places where repeatable work is happening without being captured as an SOP.

---

## Headline

Eight distinct project streams are running operational work outside the SOP Hub. Four are active and recurring (job costing close-out, hiring, sales engine debugging, dashboard build). Four are one-off artifacts that belong somewhere else, not in the SOP flow. The inbox itself is the biggest symptom: every file that lands there is a bypass until it gets filed or destroyed.

---

## Active bypass streams (these should produce SOPs)

### 1. Monthly Job Costing Close-Out (JCC)
**Location:** `09 - Inbox/PEC-JCC-March-*.docx` (4 files), `04 - Finance/Job Costing/Protiv_CloseOut_Report_2026-03-30.md`
**Evidence:** Four separate March JCC artifacts in the inbox:
- PEC-JCC-March-LaborBudget-vs-Actuals
- PEC-JCC-March-LaborVsMaterials-Bonus
- PEC-JCC-March-LaborVsMaterials-Bonus-CORRECTED
- PEC-JCC-March-Material-Verification

Plus PEC-Job-Costing-Bonus-Summary-2026-04-12.md in inbox and Protiv_CloseOut_Report in Job Costing folder.

**Why this is a bypass:** JCC is a monthly recurring close-out involving Andrew (job costing accuracy), bonus calculations, material verification, and labor-vs-budget analysis. This is a textbook SOP, and it is being executed by generating fresh docs every month with no playbook.

**SOP needed:** `SHARED-FIN-002 Monthly Job Costing Close-Out` — covers the full monthly cycle: Andrew's job cost entry, material verification, labor-vs-budget comparison, bonus calculation, the "CORRECTED" step that shows something went wrong the first time. PEC-FIN-001 exists for "Monthly Job Costing Materials Entry" but only covers the data entry step, not the close-out and reconciliation.

### 2. Hiring Flow (PEC Sales Consultant + Installers)
**Location:** `09 - Inbox/PEC-Indeed-Candidate-Call-List-2026-04-15.md`, `03 - People & HR/PEC Sales Consultant/`, `03 - People & HR/Docs/`, `03 - People & HR/Handbook Acknowledgment - *.docx` (Justin, Kyle, Silas), plus the 4 Sales Consultant HR docs misfiled in Drive PEC/ADMIN
**Evidence:** Indeed candidate call list from April 15. Hiring agreements, job descriptions, KPI framework, competency model for the Sales Consultant role all sitting loose in HR folder. Three installer handbook acknowledgments for Justin, Kyle, Silas from the April hires.

**Why this is a bypass:** Hiring is a recurring workflow (active Sales Consultant search now, installers hired in April, marketing person in Year 1, office staff in Year 3 per the 3-Year Hiring Plan). The exact same sequence runs every time: job post, Indeed screening, phone screen, interview, agreements, onboarding, handbook. This is not documented as an SOP.

**SOPs needed:**
- `SHARED-HR-001 Candidate Screening and Phone Interview` (Dusty runs phone screens)
- `SHARED-HR-002 Employment Agreement and Handbook Acknowledgment Process`
- `PEC-HR-001 New Installer Onboarding` (a New-Installer-Guide doc already exists in HR — extract and number it)

### 3. PEC Sales Engine (Lead Funnel Debugging)
**Location:** `09 - Inbox/PEC-SalesEngine-FailureLog-2026-04-15.md`, `01 - Prescott Epoxy/Lead Qualification Automation.md`
**Evidence:** Sales Engine Failure Log from April 15 sitting in inbox. Lead Qualification Automation doc in PEC folder.

**Why this is a bypass:** You are running lead-routing automations (Dusty discovery calls, estimator assignment, DripJobs handoff) with no SOP for how the flow is supposed to work or how to diagnose when it breaks. The failure log is evidence that the process is breaking and nobody has a reference doc to check against.

**SOP needed:** `PEC-SALES-003 Lead Intake and Qualification Flow` — covers the chain from lead arrival through Dusty's discovery call through Dylan's estimate booking. Cross-references the Zapier/DripJobs setup.

### 4. Dashboard Build (HQ Command Center)
**Location:** `09 - Inbox/HQ-Dashboard-Restructure-Mockup.html`, `09 - Inbox/index.html`, `06 - Automations & Tech/`, Netlify `hq-prescott.netlify.app`, GitHub `Dnordby50/hq-dashboard`
**Evidence:** Dashboard mockup and index HTML in inbox. Active automations and tool integrations in 06.

**Why this is a bypass:** Dashboard development and deployment are recurring. Every change requires a Netlify deploy cycle. The SOP Hub audit just flagged that the dashboard's SOPS tab may or may not be wired to GitHub. There is no deployment SOP, no "what to do when the build fails" runbook.

**SOP needed:** `SHARED-ADMIN-003 HQ Dashboard Deploy and Rollback` — documents the GitHub → Netlify pipeline, how to verify a successful deploy, what to do when a build fails, how to trigger a fresh sync.

---

## One-off artifacts (NOT SOPs, but misfiled)

### 5. PPR Notice of Entry (Single Job)
`09 - Inbox/PPR-Notice-of-Entry-3240Bumblebee-2026-04-15.md` — address-specific, one-time document. Should live with the Freddy's / client-specific job artifacts or be deleted after the job closes. Not an SOP.

### 6. NotebookLM Generation Log
`SOP-Hub/_LOGS/NotebookLM-Training-Generation-Log-2026-04-14.md` — this is the log from the one-time NotebookLM training video attempt. It is in the rogue hyphenated `SOP-Hub/` folder, not the real `SOP Hub/`.

**Action:** Move the log into `SOP Hub/_LOGS/`, delete the empty hyphenated `SOP-Hub/` folder.

### 7. BTA Presentation and GSR Template
`07 - Coaching & MBP/Shared-BTA-Presentation-Outline-2026-04-16.docx` and `Shared-GSR-Template-Dusty-Wilson-2026-04-12.docx`

These are coaching artifacts. GSR prep for Dusty has its own skill (`gsr-meeting-prep`), which IS effectively an SOP in executable form. No action needed for the SOP Hub.

### 8. Vault Root Garbage
`DOPE-Campaign-Strategy.md`, `contacts_merged.csv`, `contacts_merged_clean.csv`, `contacts_removed.csv` at vault root.

**Action:** Move to `05 - Marketing/` (DOPE) and `03 - People & HR/Contacts/` (CSVs), or archive if stale. Vault root should not have these files per Cowork Output Standards.

---

## Orphan SOPs (work that WAS treated like an SOP but never filed correctly)

### 9. Operations/SOPs folder in PEC
`01 - Prescott Epoxy/Operations/SOPs/Andrew SOP -- Job Sheets.md` and `Crew Bonus Structure.md`

**Why this is a bypass:** These are explicitly named SOPs but they are not in the SOP Hub and not numbered. "Andrew SOP - Job Sheets" likely overlaps with PEC-OPS-001. "Crew Bonus Structure" is critical revenue/comp doc that has no SOP number.

**Action:**
- Compare "Andrew SOP - Job Sheets" content against PEC-OPS-001. If overlap, retire the orphan. If unique content, merge.
- Number "Crew Bonus Structure" as `PEC-FIN-003 Crew Bonus Structure` (or PEC-HR-001 if you prefer the HR department) and move to SOP Hub. Memory flagged this has "unfilled fields" — needs completion before filing.

### 10. Protiv Legacy Docs
`04 - Finance/Job Costing/Protiv -- Job Costing Setup.md` and `Protiv_CloseOut_Report_2026-03-30.md`

Protiv is being replaced by the new Job Costing Workflow (now `SHARED-FIN-001 Job Costing Workflow (Protiv Replacement).md` in Shared/FIN after today's rename). These two files are historical. Archive into `08 - Templates/Archive/` or delete.

---

## Priority ranking for the bypass fixes

1. **Write `SHARED-FIN-002 Monthly JCC Close-Out`** (highest impact — recurring monthly, already failing once as evidenced by the "CORRECTED" file)
2. **Write `PEC-SALES-003 Lead Intake and Qualification Flow`** (revenue-critical — there is a failure log already)
3. **Write `SHARED-HR-001/002 + PEC-HR-001`** (hiring is active right now with the Sales Consultant search)
4. **Number the Crew Bonus Structure** (money-sensitive — unfilled fields means this has bitten you)
5. **Write `SHARED-ADMIN-003 Dashboard Deploy and Rollback`** (the dashboard is your single source of truth — cannot be brittle)
6. **Clean vault root and inbox** (hygiene — not an SOP gap but violates Cowork Output Standards)

---

## The bigger pattern

Everything in `09 - Inbox/` that is operational and dated is a bypass candidate. The inbox should hold work in transit, not work at rest. Six of the ten items in the inbox are operational (JCC files, hiring, sales engine, dashboard mockup) — that ratio tells you the SOP filing discipline is downstream of a filing triage habit that has not formed yet.

A repeating weekly audit on `09 - Inbox/` with a rule like "anything dated >7 days old must be filed, SOP'd, or deleted" would catch this before it stacks up. Your project instructions already require this (weekly self-audit), it just is not being enforced.

Source: SOP Hub | Generated 2026-04-19
