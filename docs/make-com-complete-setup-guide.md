# CV Screening Automation - Make.com Setup Guide
## For Non-Technical Users

---

## 📋 What You'll Need (5 minutes to gather)

- ✅ Google Account (Gmail)
- ✅ Claude API Key (we'll get this together)
- ✅ 30 minutes of time

**Total Cost:** ~$0.01 per CV screened (1 cent)  
**Free Tier:** Make.com gives you 1,000 operations/month free (enough for ~100 CVs)

---

## 🎯 What This Will Do

1. You upload a CV (PDF or Word doc) to a Google Drive folder
2. Make.com automatically:
   - Reads the CV
   - Analyzes it against your 3 criteria
   - Adds results to a Google Sheet
   - Moves the file to "Shortlisted" or "Review" folder
3. You review the results in the spreadsheet

**No coding. No technical skills. Just clicks.**

---

## Part 1: Set Up Your Google Workspace (10 minutes)

### Step 1: Create Google Drive Folders

1. Go to [drive.google.com](https://drive.google.com)
2. Click the **"+ New"** button (top left)
3. Select **"New folder"**
4. Create these folders exactly:

```
📁 CV Screening System
   📁 1. Inbox (CVs go here)
   📁 2. Shortlisted
   📁 3. Review
```

**Visual Guide:**
```
Click "+ New" → "New folder" → Type name → Click "Create"
```

### Step 2: Create Google Sheet for Tracking

1. Go to [sheets.google.com](https://sheets.google.com)
2. Click **"Blank"** (the big + icon)
3. At the top, click "Untitled spreadsheet"
4. Rename it: **"CV Screening Tracker"**

### Step 3: Add Headers to Your Sheet

Copy this entire line and paste it into cell **A1**:

```
Timestamp	Candidate Name	File Name	File Link	Done Role Before	Role Evidence	Role Confidence	Similar Size Org	Size Evidence	Size Confidence	Same Sector	Sector Evidence	Sector Confidence	YES Count	Overall Recommendation	Summary
```

**How to paste:**
1. Click on cell **A1** (top-left cell)
2. Press **Ctrl+V** (Windows) or **Cmd+V** (Mac)
3. Headers should spread across columns A to P

**Make it pretty (optional):**
1. Click on row **1** (the number 1 on the left)
2. Click the **B** button (makes it bold)
3. Go to **View** menu → **Freeze** → **1 row**

### Step 4: Get Your IDs

You'll need 3 IDs. Don't worry - it's just copy-paste!

#### A) Spreadsheet ID

1. Look at the URL of your Google Sheet
2. It looks like: `https://docs.google.com/spreadsheets/d/ABC123xyz/edit`
3. Copy the part between `/d/` and `/edit`

**Example:**
```
https://docs.google.com/spreadsheets/d/1a2b3c4d5e6f7g8h9i0j/edit
                                      └──────┬──────┘
                                    Copy this part
```

**Write it down:**
```
My Spreadsheet ID: ___________________________
```

#### B) Folder IDs (all 3 folders)

For each folder you created:

1. Open the folder in Google Drive
2. Look at the URL: `https://drive.google.com/drive/folders/ABC123xyz`
3. Copy everything after `/folders/`

**Do this for all 3 folders:**

```
Inbox Folder ID:      ___________________________
Shortlisted Folder ID: ___________________________
Review Folder ID:      ___________________________
```

**💡 Tip:** Keep these IDs in a notepad - you'll need them soon!

---

## Part 2: Get Your Claude API Key (5 minutes)

Claude is the AI that will read and analyze the CVs.

### Step 1: Sign Up for Claude API

1. Go to [console.anthropic.com](https://console.anthropic.com)
2. Click **"Sign Up"**
3. Use your email or Google account
4. Verify your email

### Step 2: Add a Payment Method

⚠️ **Don't worry about cost!**
- New users get **$5 free credit**
- That's enough for **~500 CVs**
- After that, it's ~$0.01 per CV

1. Click **"Billing"** in the left menu
2. Click **"Add payment method"**
3. Enter your card details
4. Click **"Save"**

### Step 3: Create an API Key

1. Click **"API Keys"** in the left menu
2. Click **"+ Create Key"**
3. Name it: **"CV Screening Make.com"**
4. Click **"Create Key"**
5. **COPY THE KEY!** It starts with `sk-ant-`

⚠️ **Important:** You'll only see this once!

**Write it down securely:**
```
My Claude API Key: sk-ant-___________________________
```

---

## Part 3: Set Up Make.com (10 minutes)

### Step 1: Create Make.com Account

1. Go to [make.com](https://make.com)
2. Click **"Get started free"**
3. Sign up with Google (easiest) or email
4. Verify your email
5. You'll land on the Make.com dashboard

**Free Plan Includes:**
- 1,000 operations/month
- Unlimited scenarios (workflows)
- Perfect for this use case!

### Step 2: Create a New Scenario

1. Click **"Create a new scenario"** (big button in center)
2. You'll see a blank canvas with a **"+"** button

This is where we'll build your automation!

---

## Part 4: Build Your Automation (15 minutes)

Follow these steps carefully. We'll add 7 modules (building blocks).

### Module 1: Watch Google Drive Folder

**Purpose:** Detects when you upload a CV

1. Click the **"+"** button in the center
2. In the search box, type: **"Google Drive"**
3. Click on **"Google Drive"** app
4. Select: **"Watch Files"**
5. Click **"Create a connection"**
   - Sign in with your Google account
   - Allow Make.com access
   - Click **"Save"**
6. Configure the module:
   - **Choose a Method:** Select "By Folder"
   - **Enter a Folder ID:** Paste your **Inbox Folder ID**
   - **Limit:** Type **10**
7. Click **"OK"**

✅ **You should see:** A box labeled "Google Drive - Watch Files"

---

### Module 2: Download File

**Purpose:** Downloads the CV file

1. Click the **"+"** button to the right of Module 1
2. Search: **"Google Drive"**
3. Select: **"Download a File"**
4. Use the same connection (already set up)
5. Configure:
   - **File ID:** Click and select **"ID"** from the dropdown (it will show "1. ID")
6. Click **"OK"**

✅ **You should see:** Two boxes connected by a line

---

### Module 3: Extract Text from PDF/DOCX

**Purpose:** Reads the content of the CV

**For PDF files:**

1. Click the **"+"** button after Module 2
2. Search: **"PDF"**
3. Select: **"PDF" app** → **"Extract text"**
4. Configure:
   - **Source file:** Click and select **"Data"** from Module 2
5. Click **"OK"**

**For DOCX files (optional - add later if needed):**

Make.com also has a "Microsoft Word" module. You can add a second branch for DOCX files if you receive both formats. For now, let's continue with PDF.

---

### Module 4: Analyze CV with Claude AI

**Purpose:** Sends CV to Claude for assessment

1. Click the **"+"** button after Module 3
2. Search: **"HTTP"**
3. Select: **"HTTP" app** → **"Make a request"**
4. Configure:

**URL:**
```
https://api.anthropic.com/v1/messages
```

**Method:** Select **"POST"**

**Headers:** Click "Add item" 3 times and add these:

| Name | Value |
|------|-------|
| `x-api-key` | YOUR_API_KEY_HERE (paste your Claude key) |
| `anthropic-version` | `2023-06-01` |
| `content-type` | `application/json` |

**Body type:** Select **"Raw"**

**Request content:** Copy and paste this ENTIRE block:

```json
{
  "model": "claude-sonnet-4-20250514",
  "max_tokens": 2000,
  "messages": [
    {
      "role": "user",
      "content": "Analyze this CV/resume and assess the candidate on these 3 criteria:\n\n1. Has this person done this role before or equivalent? (e.g., General Manager, Head of Operations, Director)\n2. Have they worked in a similar size organization? (startup or small enterprise, typically <100 employees)\n3. Have they worked in the same sector? (charity or not-for-profit)\n\nFor each criterion, provide:\n- Score: YES/NO/UNCLEAR\n- Evidence: Brief quote or reference from CV (max 50 words)\n- Confidence: HIGH/MEDIUM/LOW\n\nAlso provide:\n- Candidate Name (extracted from CV)\n- Overall Recommendation: SHORTLIST / REVIEW / REJECT\n- Brief Summary (2-3 sentences about candidate)\n\nReturn ONLY valid JSON in this exact format:\n{\n  \"candidateName\": \"string\",\n  \"criteria1\": {\n    \"score\": \"YES/NO/UNCLEAR\",\n    \"evidence\": \"string\",\n    \"confidence\": \"HIGH/MEDIUM/LOW\"\n  },\n  \"criteria2\": {\n    \"score\": \"YES/NO/UNCLEAR\",\n    \"evidence\": \"string\",\n    \"confidence\": \"HIGH/MEDIUM/LOW\"\n  },\n  \"criteria3\": {\n    \"score\": \"YES/NO/UNCLEAR\",\n    \"evidence\": \"string\",\n    \"confidence\": \"HIGH/MEDIUM/LOW\"\n  },\n  \"overallRecommendation\": \"SHORTLIST/REVIEW/REJECT\",\n  \"summary\": \"string\"\n}\n\nCV TEXT:\n\n{{3.text}}"
    }
  ]
}
```

**⚠️ IMPORTANT:** In the JSON above, find this part near the bottom:
```
CV TEXT:\n\n{{3.text}}
```

You need to change `{{3.text}}` to the actual text from Module 3:
1. Click where it says `{{3.text}}`
2. Delete it
3. Click in that spot
4. A dropdown appears - select **"Text"** from Module 3

5. Click **"OK"**

---

### Module 5: Parse Claude's Response

**Purpose:** Converts Claude's response into usable data

1. Click the **"+"** button after Module 4
2. Search: **"JSON"**
3. Select: **"JSON" app** → **"Parse JSON"**
4. Configure:
   - **JSON string:** Click and navigate to Module 4 → Data → Content → [1] → Text
   - (Path: `4.data.content[0].text`)
5. Click **"OK"**

---

### Module 6: Add Row to Google Sheets

**Purpose:** Records the results

1. Click the **"+"** button after Module 5
2. Search: **"Google Sheets"**
3. Select: **"Google Sheets" app** → **"Add a Row"**
4. Use your existing Google connection
5. Configure:

**Spreadsheet:** Click "Select from list" → Choose "CV Screening Tracker"

**Sheet:** Select "Sheet1"

**Values:** Map each column (this is important - take your time!)

Click **"Add item"** 16 times and fill in:

| Column | Value (Select from dropdowns) |
|--------|-------------------------------|
| A (Timestamp) | Click → Functions → now |
| B (Candidate Name) | Module 5 → candidateName |
| C (File Name) | Module 1 → Name |
| D (File Link) | Module 1 → webViewLink |
| E (Done Role Before) | Module 5 → criteria1 → score |
| F (Role Evidence) | Module 5 → criteria1 → evidence |
| G (Role Confidence) | Module 5 → criteria1 → confidence |
| H (Similar Size Org) | Module 5 → criteria2 → score |
| I (Size Evidence) | Module 5 → criteria2 → evidence |
| J (Size Confidence) | Module 5 → criteria2 → confidence |
| K (Same Sector) | Module 5 → criteria3 → score |
| L (Sector Evidence) | Module 5 → criteria3 → evidence |
| M (Sector Confidence) | Module 5 → criteria3 → confidence |
| N (YES Count) | Type this formula: `{{if(5.criteria1.score = "YES"; 1; 0) + if(5.criteria2.score = "YES"; 1; 0) + if(5.criteria3.score = "YES"; 1; 0)}}` |
| O (Overall Recommendation) | Module 5 → overallRecommendation |
| P (Summary) | Module 5 → summary |

6. Click **"OK"**

---

### Module 7: Move File to Appropriate Folder

**Purpose:** Organizes CVs automatically

1. Click the **"+"** button after Module 6
2. Search: **"Google Drive"**
3. Select: **"Move a File/Folder"**
4. Configure:
   - **File ID:** Module 1 → ID
   - **New Location:** We need to use a formula here

**Click the toggle next to "New Location"** to switch to formula mode, then paste:

```
{{if(5.overallRecommendation = "SHORTLIST"; "YOUR_SHORTLIST_FOLDER_ID"; "YOUR_REVIEW_FOLDER_ID")}}
```

**Replace the folder IDs:**
- Replace `YOUR_SHORTLIST_FOLDER_ID` with your actual Shortlisted folder ID
- Replace `YOUR_REVIEW_FOLDER_ID` with your actual Review folder ID

**Example:**
```
{{if(5.overallRecommendation = "SHORTLIST"; "1a2b3c4d5e6f7g8h"; "2b3c4d5e6f7g8h9i")}}
```

5. Click **"OK"**

---

## Part 5: Test Your Automation (5 minutes)

### Step 1: Save Your Scenario

1. Click the floppy disk icon (💾) at the bottom left
2. Name it: **"CV Screening Automation"**
3. Click **"Save"**

### Step 2: Create a Test CV

Create a simple test file. Copy this text into a Word document or PDF:

```
JOHN SMITH
General Manager

EXPERIENCE

General Manager - Hope Community Foundation (2020-2023)
• Led team of 20 in a small charity focused on education
• Managed all operations for growing non-profit
• Grew organization from 5 to 20 employees over 3 years

Operations Director - Social Impact Tech (2018-2020)
• Directed operations for social enterprise startup
• Team of 12 people
• Built charitable giving platform from scratch

EDUCATION
MBA - Business Management, 2017
BA - Social Work, 2015
```

Save this as: **Test_Candidate.pdf** or **Test_Candidate.docx**

### Step 3: Run the Test

1. In Make.com, click **"Run once"** (bottom left, play button ▶️)
2. Upload your test CV to the **"1. Inbox"** folder in Google Drive
3. Wait 1-2 minutes
4. Watch the scenario run in Make.com

**You should see:**
- Each module lights up in sequence
- Green checkmarks ✅ when successful
- The file appears in your Google Sheet
- The file moves to "Shortlisted" folder

### Step 4: Check Results

**In Google Sheets:**
1. Open "CV Screening Tracker"
2. You should see a new row with John Smith's details
3. All three criteria should say "YES"
4. Recommendation should be "SHORTLIST"

**In Google Drive:**
1. Check your "2. Shortlisted" folder
2. The test file should be there

**If it worked:** 🎉 Congratulations! Your automation is ready!

**If it didn't work:** See troubleshooting below

---

## Part 6: Activate & Use

### Activate Your Scenario

1. In Make.com, toggle the switch at the bottom from **"OFF"** to **"ON"**
2. The scenario will now run automatically every 15 minutes

**Change checking frequency (optional):**
1. Click on Module 1 (Watch Files)
2. Click "Show advanced settings"
3. Change "Interval" (e.g., every 5 minutes, every hour)

### How to Use Daily

1. **Receive a CV** → Save it with the candidate's name (e.g., "Jane_Doe_CV.pdf")
2. **Upload to Google Drive** → Drag into "1. Inbox" folder
3. **Wait 1-15 minutes** → Make.com processes it automatically
4. **Check results** → Open your Google Sheet
5. **Review candidates** → Look in "Shortlisted" or "Review" folders

That's it! No clicking, no manual work.

---

## 🔧 Troubleshooting

### Nothing Happens When I Upload a File

**Check these:**
1. Is the scenario **ON**? (Check toggle switch in Make.com)
2. Did you upload to the correct folder? (Should be "1. Inbox")
3. Wait 15 minutes (default check interval)
4. Click "Run once" manually to test immediately

### "Error: Invalid API Key"

**Fix:**
1. Go to Module 4 (HTTP Request)
2. Check the `x-api-key` header
3. Make sure:
   - No extra spaces
   - Key starts with `sk-ant-`
   - You copied the full key
4. If still broken, generate a new API key

### "Error: File format not supported"

**Fix:**
- Make sure the file is PDF (not scanned image)
- Or use DOCX format
- If you have image-based PDFs, you'll need OCR first

### Text Extraction Returns Gibberish

**Common causes:**
- File is a scanned image (not text-based PDF)
- File is corrupted

**Solutions:**
1. Right-click the PDF in Google Drive
2. "Open with" → "Google Docs"
3. Google Docs will OCR it
4. Download as PDF again

### Claude Returns Wrong Format

**Fix:**
1. Go to Module 4 (HTTP)
2. Check that the prompt copied correctly
3. Make sure the `{{3.text}}` part connects to Module 3's text output

### Scenario Stops Running

**Check:**
1. Make.com free tier limits: 1,000 operations/month
2. Check usage: Settings → Organization → Usage
3. If exceeded, either upgrade ($9/month) or wait until next month

---

## 💰 Cost Breakdown

### Make.com
- **Free tier:** 1,000 operations/month
- **This scenario uses:** ~7 operations per CV
- **You can process:** ~140 CVs/month free
- **Paid plan:** $9/month for 10,000 operations (if needed)

### Claude API
- **Free credit:** $5 (enough for ~500 CVs)
- **After that:** ~$0.01 per CV
- **Cost per month:**
  - 10 CVs = $0.10
  - 50 CVs = $0.50
  - 100 CVs = $1.00

### Total Cost
- **First 500 CVs:** Free (using $5 credit)
- **After that:** $0.01-0.02 per CV
- **For 100 CVs/month:** ~$1-2/month

---

## 📊 Understanding Your Results

### Scoring System

**YES** = Candidate clearly meets this criterion  
**NO** = Candidate does not meet this criterion  
**UNCLEAR** = Not enough information in CV

### Recommendation Logic

- **SHORTLIST** = Strong candidate (usually 2-3 YES scores)
- **REVIEW** = Borderline candidate (usually 1-2 YES scores)
- **REJECT** = Does not meet criteria (usually 0-1 YES scores)

### YES Count

Quick filter for strongest candidates:
- **3 YES** = Perfect match
- **2 YES** = Good match
- **1 YES** = Partial match
- **0 YES** = Poor match

---

## 🎨 Customizing for Your Needs

### Change the Screening Criteria

1. Go to Module 4 (HTTP - Claude API)
2. Find this section in the prompt:
```
1. Has this person done this role before...
2. Have they worked in a similar size organization...
3. Have they worked in the same sector...
```
3. Edit to match your requirements
4. Example changes:
```
1. Has this person managed a team of 10+ people?
2. Do they have 5+ years of experience?
3. Do they have relevant certifications or qualifications?
```

### Change File Organization Logic

Want different folder rules?

1. Go to Module 7 (Move File)
2. Edit the formula:

**Examples:**

Move only if 3/3 YES:
```
{{if(5.criteria1.score = "YES" and 5.criteria2.score = "YES" and 5.criteria3.score = "YES"; "SHORTLIST_ID"; "REVIEW_ID")}}
```

Move if 2+ YES:
```
{{if((if(5.criteria1.score = "YES"; 1; 0) + if(5.criteria2.score = "YES"; 1; 0) + if(5.criteria3.score = "YES"; 1; 0)) >= 2; "SHORTLIST_ID"; "REVIEW_ID")}}
```

### Add Email Notifications

Want to be notified of strong candidates?

1. After Module 5, click the **"+"**
2. Add a **"Router"** module (creates two paths)
3. **Path 1:** Only when SHORTLIST
   - Add filter: `overallRecommendation = SHORTLIST`
   - Add "Gmail" → "Send an Email"
   - Configure with candidate details
4. **Path 2:** All other cases
   - Continue to existing modules

---

## 🔒 Security & Privacy

### Data Protection

**Your data stays secure:**
- Google Drive: Only you have access
- Make.com: Encrypted connections
- Claude API: Doesn't store your CV data

**Best practices:**
1. Don't share your API key
2. Use a dedicated Google account if handling sensitive data
3. Regularly review Make.com connections

### GDPR Compliance

If in EU/UK:
- CVs contain personal data
- Inform candidates their CVs will be processed by AI
- Add to your privacy policy
- Delete old CVs regularly

---

## 📈 Next Steps & Enhancements

### Once You're Comfortable

1. **Add email trigger**
   - Candidates email CVs directly
   - Make.com processes from Gmail

2. **Add interview scheduling**
   - Auto-send Calendar invite to shortlisted candidates
   - Integration with Calendly

3. **Multi-stage tracking**
   - Add columns for Interview 1, Interview 2, Offer
   - Update spreadsheet as candidates progress

4. **Reporting dashboard**
   - Connect Google Sheets to Google Data Studio
   - Visualize your hiring funnel

---

## 🆘 Getting Help

### Make.com Support
- Help Center: [make.com/en/help](https://www.make.com/en/help)
- Community: [community.make.com](https://community.make.com)
- Live chat (paid plans)

### Claude API Support
- Documentation: [docs.anthropic.com](https://docs.anthropic.com)
- Support: support@anthropic.com

### Video Tutorials
Search YouTube for:
- "Make.com tutorial for beginners"
- "Make.com Google Drive automation"
- "Make.com HTTP request tutorial"

---

## ✅ Quick Reference Checklist

Use this when setting up:

**Before Starting:**
- [ ] Google account ready
- [ ] Claude API key obtained ($5 credit)
- [ ] Make.com account created (free)

**Google Setup:**
- [ ] 3 folders created in Drive (Inbox, Shortlisted, Review)
- [ ] Folder IDs copied and saved
- [ ] Google Sheet created with headers
- [ ] Spreadsheet ID copied and saved

**Make.com Setup:**
- [ ] Module 1: Watch Files (Inbox folder)
- [ ] Module 2: Download File
- [ ] Module 3: Extract Text (PDF)
- [ ] Module 4: HTTP Request (Claude API with key)
- [ ] Module 5: Parse JSON
- [ ] Module 6: Add Row (Google Sheets mapped)
- [ ] Module 7: Move File (folder IDs set)
- [ ] Scenario saved and tested
- [ ] Scenario activated (ON)

**Testing:**
- [ ] Test CV created
- [ ] Test CV uploaded
- [ ] Results in Google Sheet
- [ ] File moved to correct folder

**Ready to Use!** 🎉

---

## 📝 Notes Section

Use this space to write down your IDs and notes:

```
My Spreadsheet ID: _________________________________

Inbox Folder ID: _________________________________

Shortlisted Folder ID: _________________________________

Review Folder ID: _________________________________

Claude API Key: sk-ant-_________________________________

Date Activated: _________________________________

Notes:
_________________________________
_________________________________
_________________________________
```

---

**You're all set! Happy recruiting! 🚀**