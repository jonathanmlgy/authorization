# 🔐 Google Cloud Credentials Setup

This guide walks through creating the credentials needed for the n8n workflow.

---

## Step 1: Create Google Cloud Project

1. Go to [Google Cloud Console](https://console.cloud.google.com)
2. Click **New Project** (top right)
3. Name: `n8n-authorization-automation`
4. Click **Create**

---

## Step 2: Enable Required APIs

1. In your project, go to **APIs & Services → Library**
2. Search and enable these APIs:

| API | Purpose |
|-----|---------|
| **Google Drive API** | Watch folder, download PDFs |
| **Google Sheets API** | Read/write spreadsheet data |

---

## Step 3: Create Service Account

1. Go to **APIs & Services → Credentials**
2. Click **+ CREATE CREDENTIALS → Service account**
3. Fill in:

   - **Service account name**: `n8n-automation`
   - **Service account ID**: `n8n-automation` (auto-filled)
   - **Description**: `Accesses Drive and Sheets for authorization automation`

4. Click **CREATE AND CONTINUE** (skip roles for now)
5. Click **DONE**

---

## Step 4: Create OAuth Client (for n8n)

1. In **Credentials**, click **+ CREATE CREDENTIALS → OAuth client ID**
2. **Application type**: `Desktop app`
3. **Name**: `n8n Desktop Client`
4. Click **Create**
5. **Download** the JSON file (click **DOWNLOAD JSON**)
6. Rename to `google_credentials.json`

---

## Step 5: Get Service Account Email

1. Go to **APIs & Services → Credentials**
2. Click on your service account (`n8n-automation`)
3. Copy the **Email** (looks like: `n8n-automation@project-id.iam.gserviceaccount.com`)

> ⚠️ You'll need this email to share Google Drive folder and Sheets

---

## What to Save

| File | Where to Use |
|------|---------------|
| `google_credentials.json` | Upload to n8n as Google Drive OAuth2 |
| Service account email | Share Drive folder & Sheet with this email |

---

## 🔗 Connect to n8n

### Google Drive OAuth2

1. In n8n, go to **Settings → Credentials**
2. Add **Google Drive OAuth2**
3. Upload `google_credentials.json`
4. Save

### Google Sheets OAuth2

1. Add **Google Sheets OAuth2**
2. Use the **same** `google_credentials.json`
3. Save

---

## 📁 Share Resources with Service Account

### Share Google Drive Folder

1. Go to [Google Drive](https://drive.google.com)
2. Right-click your authorization folder → **Share**
3. Add the service account email
4. Set as **Editor**

### Share Google Sheet

1. Open your Google Sheet
2. Click **Share**
3. Add the service account email
4. Set as **Editor**

---

## ✅ Verify Setup

Test by running the n8n workflow:
1. Upload a PDF to the watched folder
2. Check that data appears in your Google Sheet

---

## 🔑 Anthropic Claude API Key

1. Go to [Anthropic Console](https://console.anthropic.com)
2. Go to **API Keys**
3. Create a new key
4. Copy it (you won't see it again)

In n8n, add as a **Custom Header**:
- Key: `x-api-key`
- Value: `[your-claude-api-key]`