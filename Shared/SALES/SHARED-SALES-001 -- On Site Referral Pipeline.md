# SHARED-SALES-001 -- On Site Referral Pipeline

**SOP: On Site Referral Lead Capture (FTP & PEC)**
**Last Updated:** March 30, 2026
**Owner:** Dylan Nordby

---

## PURPOSE

Capture referral leads submitted by crews on site via Google Forms, auto-populate a shared Google Sheet, and auto-create new leads in DripJobs via Zapier.

## APPLIES TO

Both Finishing Touch Painting (FTP) and Prescott Epoxy (PEC).

## SYSTEM OVERVIEW

1. Crew member fills out the company-specific Google Form on site.
2. Form response lands in the shared Google Sheet ("On Site Referrals (FTP & PEC)") on the company-specific tab.
3. Zapier triggers on new row and creates a new lead in DripJobs under the correct company.

## ASSETS & LINKS

**Google Sheet:** "On Site Referrals (FTP & PEC)"
- Sheet ID: `1AmLXD1dFJAsuHWSb1MCg3whE8bCBeeQCHqdWkXro_zY`
- FTP tab: "FTP Form Responses"
- PEC tab: "PEC Form Responses"

**Google Forms:**
- FTP Referrals (form ID: `1vAXJcbSX-1gnahggH1sRg-WMlg_65sYMPrJ_kl1gFUE`)
- PEC Referrals (form ID: `1S9pd6Sn8KRs2EjA4OFhykfFMv7PNvr3T9OHOUvz98ow`)

**Zapier Zaps:**
- FTP On Site Lead (Zap ID: 353286743) — Active, published Mar 9, 2026
- PEC On Site Lead (Zap ID: 356993220) — Published Mar 30, 2026

## FORM FIELDS (both forms identical)

- Your Name (referring crew member)
- Lead First Name
- Lead Last Name
- Lead Address
- Lead Phone Number
- Lead Email
- Description of work
- Lead Source?

## ZAPIER FIELD MAPPING (both zaps identical pattern)

**Trigger:** Google Sheets → New or Updated Spreadsheet Row
**Action:** DripJobs → Create Lead

| DripJobs Field | Google Sheet Column |
|---|---|
| Lead Source | Description of work |
| First Name | Lead First Name |
| Last Name | Lead Last Name |
| Email | Lead Email |
| Phone | Lead Phone Number |
| Job Address | Lead Address |
| Job City | (empty) |
| Job State | (empty) |
| Job Zip | (empty) |
| Notes | (empty) |
| Deal Stage | (empty) |
| Drip Sequence | (empty) |
| Assign To | (empty) |
| Deal Name | (empty) |

## DRIPJOBS CONFIGURATION REQUIREMENT

Each company must have a Zapier API Key configured in DripJobs company settings for the zap to successfully create leads. Without this key, the zap fires but DripJobs rejects the request.

## TROUBLESHOOTING

- **Leads not appearing in DripJobs:** Check DripJobs → Company Settings for Zapier API Key.
- **Form responses not appearing in sheet:** Verify the form is linked to the correct sheet tab (Form → Settings → Responses → Select response destination).
- **Zapier not triggering:** Confirm the zap is published and the trigger column is set to "Timestamp."

## ADDING A NEW COMPANY

To replicate this pipeline for a new company:

1. Create a new Google Form matching the field structure above.
2. Link form responses to a new tab in the shared Google Sheet.
3. Create a new Zapier zap: Google Sheets trigger (new row on new tab) → DripJobs Create Lead action (select the new company account).
4. Map fields identically per the mapping table above.
5. Ensure DripJobs has the Zapier API Key configured for the new company.
6. Test with a dummy submission, verify lead appears in DripJobs, then delete test data.
