# 📥 Google Sheet Setup Guide

## Option 1: Quick Import (Recommended)

1. Open [Google Sheets](https://sheets.google.com)
2. Create a new spreadsheet
3. Go to **File → Import**
4. Upload `student_authorization_template.csv`
5. Delete the example rows (rows 2-3)

## Option 2: Manual Creation

Create these columns in row 1:

| Column | Description | Example |
|--------|-------------|---------|
| A | UCI (Client ID) | `EXAMPLE001` |
| B | Student Name | `Jane Doe` |
| C | Guardian Name | `John Doe` |
| D | Authorization Comments | `Approved for ABA therapy` |
| E | Authorization Date | `09/01/26 - 12/31/26` |
| F | Current Auth Exp Date | `12/31/26` |
| G | Hours Per Month | `10 hours/month (09/01/26 - 12/31/26)` |
| H | Requested Schedule | `3pm-7pm M-Th virtual` |
| I | Parent Requested Mode | `virtual` |
| J | Parent Feedback | `Parent requests consistent schedule` |
| K | Start Date Track | `Track A` |

---

## 🔗 Connect to n8n Workflow

### Step 1: Get Sheet ID

From your Google Sheet URL:

```
https://docs.google.com/spreadsheets/d/[SHEET_ID]/edit
```

Copy the **SHEET_ID** (the long string between `/d/` and `/edit`).

### Step 2: Update Workflow

1. Open the n8n workflow
2. Find the **"Write to Sheet"** node(s)
3. Replace the existing Sheet ID with yours

### Step 3: Share with Service Account

1. Click **Share** in Google Sheets
2. Add the service account email from your Google Cloud project
3. Set as **Editor** (can edit)

---

## 📋 Required Credentials

| Credential | Where to Get |
|-------------|--------------|
| Google Drive OAuth2 | [Google Cloud Console](https://console.cloud.google.com) → APIs → Drive API |
| Google Sheets OAuth2 | Same project, enable Sheets API |
| Claude API Key | [Anthropic Console](https://console.anthropic.com) |

### Required OAuth Scopes

```
https://www.googleapis.com/auth/drive
https://www.googleapis.com/auth/spreadsheets
```