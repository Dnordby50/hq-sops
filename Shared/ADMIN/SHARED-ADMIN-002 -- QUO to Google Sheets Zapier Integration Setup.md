# SOP -- QUO to Google Sheets Zapier Integration Setup

---

## SOP Title: QUO to Google Sheets Zapier Integration Setup

**SOP ID:** SHARED-ADMIN-002
**Company:** Shared (PEC and FTP)
**Owner:** Dylan
**Approved by:** Dylan
**Last updated:** 2026-04-08
**Version:** 1.0

---

## Purpose

Set up Zapier zaps that route QUO (formerly OpenPhone) call transcripts and SMS messages into the Customer Communications Google Sheet. Each zap captures one combination of company (PEC or FTP) and data type (call transcript or SMS), filters by phone number, and writes a row to the correct tab.

---

## Scope

**Who this applies to:** Dylan or Cowork assistant
**When to use this SOP:** Any time a new QUO-to-Sheets zap needs to be built, such as adding a new phone line, a new data type (e.g., outgoing SMS), or rebuilding a broken zap.

---

## Prerequisites

Before starting, confirm:
- [ ] Zapier account access (login via Google as dylan@finishingtouchpaintingaz.com)
- [ ] QUO Zapier integration is connected in Zapier (app name: "OpenPhone" in Zapier's app list)
- [ ] Google Sheets integration is connected in Zapier under dylan@finishingtouchpaintingaz.com
- [ ] The target Google Sheet exists with the correct tab and column headers already in place

---

## Reference Data

### Customer Communications Google Sheet
- **Sheet ID:** 1o_tOFB9pNCCwu0aFo3Lob8GCvYau9ZOpjpHnz3DCGxI
- **Tab: PEC Call Log** (worksheet ID: 337493357)
- **Tab: FTP Call Log** (worksheet ID: 1902780514)
- **Tab: PEC SMS Log** (worksheet ID: 1784496727)
- **Tab: FTP SMS Log** (worksheet ID: 1787603418)
- **Tab: Email Log** (worksheet ID: 1551439282)

### QUO Phone Number IDs (used in Zapier filters)
- **PEC:** PNY8vPVPEZ (Prescott Epoxy - 928-800-8154)
- **FTP:** PNbl4NYbrM (Finishing Touch - 928-356-1243)

### QUO Trigger Types in Zapier
- **Call Transcript Completed** -- fires when a call ends and QUO generates the transcript
- **Incoming Message Received** -- fires on inbound SMS only
- **Outgoing Message Delivered** -- fires on outbound SMS only (not used in initial build)

### Google Account Rule
- ALWAYS use dylan@finishingtouchpaintingaz.com for the Google Sheets connection. Never Dusty's account.

---

## Steps

### 1. Create the Zap

1. Go to zapier.com and click "Create" > "New Zap"
2. Name the zap using this convention: `[Company] [Data Type] > Google Sheets`
   - Examples: "PEC Call Transcripts > Google Sheets", "FTP SMS Incoming > Google Sheets"

### 2. Set Up the Trigger (QUO / OpenPhone)

1. Search for "OpenPhone" as the trigger app
2. Select the appropriate trigger event:
   - For call transcripts: "Call Transcript Completed"
   - For incoming SMS: "Incoming Message Received"
   - For outgoing SMS: "Outgoing Message Delivered"
3. Connect to the QUO account (should already be connected)
4. In trigger configuration, if it asks for Phone Number ID, select the correct one:
   - PEC: "Prescott Epoxy - 928-800-8154"
   - FTP: "Finishing Touch - 928-356-1243"
5. Test the trigger to pull sample data. If no recent data exists, you may need to generate a test call or SMS first.

### 3. Add a Filter (if trigger does not filter by phone number)

If the trigger fires for all phone numbers and does not have a built-in phone number filter:
1. Add a Filter step between the trigger and the action
2. Set the filter to: `Phone Number ID` > `(Text) Exactly matches` > the QUO Phone Number ID for the target company
3. This ensures only the correct company's data flows through

### 4. Set Up the Action (Google Sheets)

1. Search for "Google Sheets" as the action app
2. Select "Create Spreadsheet Row" as the action event
3. Connect using dylan@finishingtouchpaintingaz.com (verify this before proceeding)
4. Configure the action:
   - **Drive:** My Google Drive
   - **Spreadsheet:** Customer Communications (Sheet ID above)
   - **Worksheet:** Select the correct tab for the company and data type

### 5. Map Fields

Map the QUO trigger fields to the Google Sheet columns. The exact mapping depends on the data type:

**For Call Transcript Zaps:**

| Sheet Column | QUO Field |
|---|---|
| Date/Time | Created At |
| Customer Name | (leave blank -- QUO does not provide names) |
| Phone Number | From (or To, depending on direction) |
| Direction | (not available in Call Transcript trigger) |
| Duration | Duration |
| Transcript | Transcript |
| AI Summary | (not available in basic trigger -- would need "Call Summary Completed" trigger) |
| QUO Conversation ID | Conversation ID |

**For SMS Zaps:**

| Sheet Column | QUO Field |
|---|---|
| Date/Time | Created At |
| Customer Name | (leave blank -- QUO does not provide names) |
| From | From |
| To | To |
| Direction | Direction |
| Message Body | Body |
| QUO Conversation ID | Conversation ID |

### 6. Test the Action

1. Click "Test step" to write a sample row to the sheet
2. Open the Google Sheet and verify:
   - Row landed in the correct tab
   - All mapped fields populated correctly
   - Date format is readable
   - No data landed in wrong columns

### 7. Publish the Zap

1. Click "Publish" to make the zap live
2. Verify the zap toggle is ON
3. Note the Zapier zap ID for records

---

## Known Limitations

1. **Customer Name is always blank.** QUO triggers do not include contact names. Name lookup would require a second Zapier step querying QUO contacts by phone number (adds task cost).
2. **SMS zaps are one-direction per zap.** "Incoming Message Received" only captures inbound. A separate zap with "Outgoing Message Delivered" is needed for outbound.
3. **Call direction is not in the Call Transcript trigger.** The transcript trigger does not include whether the call was inbound or outbound.
4. **AI Summary requires a different trigger.** The "Call Transcript Completed" trigger does not include the AI-generated summary. The "Call Summary Completed" trigger (if available) would be needed for that field.

---

## Current Live Zaps (as of 2026-04-08)

| Zap Name | Zapier ID | Trigger | Target Tab | Status |
|---|---|---|---|---|
| PEC Call Transcripts > Google Sheets | 358476455 | Call Transcript Completed | PEC Call Log | Live, v1 |
| FTP Call Transcripts > Google Sheets | 358476455 | Call Transcript Completed | FTP Call Log | Live, v1 |
| PEC SMS Incoming > Google Sheets | 358477961 | Incoming Message Received | PEC SMS Log | Live, v1 |
| FTP SMS Incoming > Google Sheets | 358478868 | Incoming Message Received | FTP SMS Log | Live, v1 |

---

## Troubleshooting

| Issue | Fix |
|---|---|
| Zap fires but no row appears | Check the filter step -- phone number ID may not match. Also check that the Google Sheets connection is under dylan@finishingtouchpaintingaz.com. |
| Row appears in wrong tab | The worksheet selection in the action step is wrong. Edit the zap and re-select the correct tab. |
| Date/Time shows as a number | The Created At field from QUO may need a Formatter step to convert to a readable date. |
| "Authentication failed" on Google Sheets | Re-authenticate the Google connection. Make sure it is dylan@finishingtouchpaintingaz.com, not Dusty's account. |
| Zap turns itself off | Zapier auto-disables zaps after repeated errors. Check the zap history for the error, fix the root cause, then re-enable. |

---

## Escalation

Escalate to Dylan when:
- QUO changes their Zapier integration or deprecates a trigger type
- A zap has been erroring for 24+ hours
- A new phone line is added and needs its own set of zaps

---

## Revision History

| Version | Date | Change |
|---|---|---|
| 1.0 | 2026-04-08 | Initial version. Documents the 4-zap build (PEC/FTP call transcripts + PEC/FTP incoming SMS). |

---

Source: PEC Sales Engine | Generated 2026-04-08
