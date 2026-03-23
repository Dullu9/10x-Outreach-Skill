---
name: sheet-reader
description: |
  Read recipient data from Google Sheets for email campaigns.
  Supports column mapping, data validation, and batch processing.
  Use this skill when the user wants to import contacts from a Google Sheet.
allowed-tools:
  - Bash
  - Read
  - Write
---

# Sheet Reader Skill

Reads recipient data from Google Sheets for use in email campaigns and outreach workflows.

## When to Use This Skill

Use this skill when the user:
- Wants to import contacts from a Google Sheet
- Needs to read campaign recipient lists
- References a Google Sheet URL or ID

## Script

```bash
python .claude/scripts/sheets_reader.py --sheet-id <SHEET_ID> --range "Sheet1!A1:Z1000"
```

## Required Environment

- `GOOGLE_CLIENT_ID` — for Google Sheets API access
- `GOOGLE_CLIENT_SECRET` — for OAuth authentication
- `GOOGLE_SHEET_ID` — default sheet ID (optional, can be passed per-call)

## Output

Saves parsed contacts to `output/discovery/` as JSON for use by outreach-manager.
