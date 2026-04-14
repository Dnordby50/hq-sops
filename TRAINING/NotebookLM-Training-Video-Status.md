# NotebookLM Training Video Project -- Status and Continuation Brief

**Date:** 2026-04-14
**Project:** PEC Installer Training Program -- NotebookLM Video/Audio Generation
**Source:** SOP Hub | Generated 2026-04-14

---

## What Was Done

11 SOPs were broken out from two source documents ("Epoxy Product Training" and "Epoxy System Training") and turned into individual .docx files filed in Google Drive and locally under `SOP Hub/PEC/OPS/` and `SOP Hub/PEC/ADMIN/`.

A NotebookLM notebook was created for each SOP with the full SOP text loaded as a "Copied text" source. Each notebook is named using the convention: `[SOP-ID] [Title] -- Training`

The goal is to generate a **Video Overview** (Explainer format) and an **Audio Overview** (podcast-style) for each notebook so crews can watch or listen to training content.

---

## NotebookLM Generation Settings

For every Video Overview, use these settings:
- **Format:** Explainer
- **Visual style:** Auto-select
- **Steering prompt:** "This is a training video for field crews and office staff at a home services company in Prescott, Arizona. Focus on the step-by-step procedures, common mistakes to avoid, and key compliance requirements. Keep language simple and direct. These are tradespeople, not corporate employees."

For Audio Overview, just generate with defaults (no special settings needed).

---

## Current Status (as of 2026-04-14)

| # | SOP ID | Title | Notebook Created | Video | Audio |
|---|--------|-------|:---:|:---:|:---:|
| 1 | PEC-OPS-003 | Metallic Additive Product Training | Yes | DONE | DONE |
| 2 | PEC-OPS-004 | High Wear Urethane Product Training | Yes | DONE | DONE |
| 3 | PEC-OPS-005 | Polyaspartic HS Product Training | Yes | DONE | DONE |
| 4 | PEC-OPS-006 | Simiron 1100 SL Product Training | Yes | DONE | DONE |
| 5 | PEC-OPS-007 | Job Site Operations | Yes | GENERATING (triggered 4/14) | NEEDS GENERATION |
| 6 | PEC-OPS-008 | Concrete Patching and Repair | Yes | NEEDS GENERATION | NEEDS GENERATION |
| 7 | PEC-OPS-009 | Concrete Grinding and Surface Prep | Yes | NEEDS GENERATION | NEEDS GENERATION |
| 8 | PEC-OPS-010 | Flake System Installation | Yes | NEEDS GENERATION | NEEDS GENERATION |
| 9 | PEC-OPS-011 | Metallic System Installation | Yes | NEEDS GENERATION | NEEDS GENERATION |
| 10 | PEC-OPS-012 | Off-Site Procedures and Truck Inventory | Yes | NEEDS GENERATION | NEEDS GENERATION |
| 11 | PEC-ADMIN-002 | Contract Terms and Conditions | Yes | NEEDS GENERATION | NEEDS GENERATION |

**Summary:** 4 complete, 1 video generating, 6 need both video and audio, 1 needs audio only.

---

## What Needs to Happen Next

1. **Check OPS-007** -- open the notebook and confirm the video finished generating. If done, also generate Audio Overview for it.

2. **Generate Video + Audio for OPS-008 through OPS-012 and ADMIN-002** -- NotebookLM has a daily generation cap. You can typically get 4-5 video+audio pairs per day. Open each notebook, click Video Overview, set to Explainer format, paste the steering prompt above, and click Generate. Then do the same for Audio Overview.

3. **Estimated timeline:** At ~5 per day, you need 2 more days to finish all remaining generations.

4. **After all videos/audio are generated:** Download each video and audio file from NotebookLM and save to:
   - Local: `SOP Hub/TRAINING/PEC/[SOP-ID] Training Video.[ext]` and `[SOP-ID] Training Audio.[ext]`
   - Google Drive: Copy to the matching training folder

---

## NotebookLM Access

All notebooks are under Dylan's Google account (dylan@finishingtouchpaintingaz.com) at notebooklm.google.com. They appear on the home page sorted by most recent. All 11 are dated Apr 13, 2026 and each has 1 source.

---

## SOP File Locations

**Local:** `/Users/dylannordby/Desktop/HQ/SOP Hub/PEC/OPS/` and `.../PEC/ADMIN/`
**Google Drive:** SOPs > PEC > OPS and SOPs > PEC > ADMIN (Drive root folder ID: 1P8eAxJzIpQEb1mAXpGm7RSEuk9ASLCao)
