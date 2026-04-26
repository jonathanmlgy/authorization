# Student Authorization PDF → Google Sheets Automation

An n8n workflow that automatically extracts student authorization data from PDFs in Google Drive and populates a Google Sheet using Claude AI.

## 📋 Overview

- **Status:** Pre-Error Handling Phase (active)
- **Technology:** n8n + Claude API + Google Drive/Sheets
- **Processing Time:** ~15 seconds per PDF
- **Accuracy:** ~95% field extraction rate

## 🎯 What It Does

1. Monitors Google Drive folder for new authorization PDFs
2. Extracts text using n8n PDF parser
3. Parses fields with Claude AI (structured output mode)
4. Populates Google Sheet with student data
5. Logs warnings for missing or ambiguous fields

## 🚀 Quick Start

### Prerequisites
- n8n (self-hosted or n8n Cloud)
- Google Drive API credentials (OAuth2)
- Google Sheets API credentials (OAuth2)
- Anthropic Claude API key

### Setup

1. **Configure credentials**
   - Follow [credentials setup guide](docs/credentials_setup.md)
   - Create Google Cloud project
   - Enable Drive & Sheets APIs
   - Get OAuth2 credentials

2. **Create n8n workflow**
   - Import workflow JSON (link to export)
   - Or manually recreate 13 nodes from node mapping

3. **Set up Google Sheet**
   - Import [template CSV](docs/student_authorization_template.csv)
   - Or follow [detailed setup guide](docs/google_sheet_setup.md)
   - Update Sheet ID in workflow nodes

4. **Set folder & sheet IDs**
   - Update Drive folder path: `/Test Authorization`
   - Update Sheet ID: (your spreadsheet ID)

5. **Test with sample PDFs**
   - Upload test authorization PDFs
   - Verify extraction accuracy
   - Check _warnings sheet for anomalies