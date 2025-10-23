# Google Sheets Template for CV Screening

## Sheet Name: CV Screening Tracker

### Headers (Row 1)

Copy and paste this into cell A1 (it will automatically spread across columns):

```
Timestamp	Candidate Name	File Name	File Link	Done Role Before	Role Evidence	Role Confidence	Similar Size Org	Size Evidence	Size Confidence	Same Sector	Sector Evidence	Sector Confidence	YES Count	Overall Recommendation	Summary
```

### Column Details

| Column | Header | Data Type | Description |
|--------|--------|-----------|-------------|
| A | Timestamp | Date/Time | When the CV was processed |
| B | Candidate Name | Text | Extracted from CV |
| C | File Name | Text | Original filename |
| D | File Link | URL | Link to view file in Drive |
| E | Done Role Before | YES/NO/UNCLEAR | First criterion score |
| F | Role Evidence | Text | Quote/evidence from CV |
| G | Role Confidence | HIGH/MEDIUM/LOW | AI confidence level |
| H | Similar Size Org | YES/NO/UNCLEAR | Second criterion score |
| I | Size Evidence | Text | Quote/evidence from CV |
| J | Size Confidence | HIGH/MEDIUM/LOW | AI confidence level |
| K | Same Sector | YES/NO/UNCLEAR | Third criterion score |
| L | Sector Evidence | Text | Quote/evidence from CV |
| M | Sector Confidence | HIGH/MEDIUM/LOW | AI confidence level |
| N | YES Count | Number (0-3) | Total YES scores |
| O | Overall Recommendation | SHORTLIST/REVIEW/REJECT | Final decision |
| P | Summary | Text | 2-3 sentence candidate summary |

---

## Formatting Instructions

### 1. Make Headers Bold

1. Click on row number **1**
2. Press **Ctrl+B** (Windows) or **Cmd+B** (Mac)

### 2. Freeze Header Row

1. Click on cell **A2** (first cell below headers)
2. Go to **View** → **Freeze** → **1 row**

This keeps headers visible when scrolling down.

### 3. Set Column Widths

**Quick method - Auto-resize:**
1. Select all columns (click between column A and row 1)
2. Move cursor to the line between column letters
3. Double-click when you see the resize cursor ↔️

**Manual method (recommended for specific columns):**

| Column | Suggested Width | How to Resize |
|--------|----------------|---------------|
| A (Timestamp) | 150 pixels | Good for dates |
| B (Name) | 150 pixels | Fits most names |
| C (File Name) | 200 pixels | For long filenames |
| D (File Link) | 80 pixels | Just shows "Link" |
| E, H, K (Scores) | 120 pixels | YES/NO/UNCLEAR |
| F, I, L (Evidence) | 300 pixels | Room for quotes |
| G, J, M (Confidence) | 100 pixels | HIGH/MEDIUM/LOW |
| N (YES Count) | 80 pixels | Just numbers |
| O (Recommendation) | 150 pixels | SHORTLIST/REVIEW/REJECT |
| P (Summary) | 400 pixels | Longer text |

### 4. Add Conditional Formatting (Optional but Helpful!)

This makes it easy to spot good candidates at a glance.

#### Highlight Strong Candidates (3 YES)

1. Select column **N** (YES Count) from N2 downward
2. Go to **Format** → **Conditional formatting**
3. Set:
   - **Format cells if:** "Text is exactly"
   - **Value:** `3`
   - **Formatting style:** Green background
4. Click **Done**

#### Highlight Recommendations

1. Select column **O** (Overall Recommendation) from O2 downward
2. Go to **Format** → **Conditional formatting**
3. Set up three rules:

**Rule 1 - SHORTLIST (Green):**
- **Format cells if:** "Text is exactly"
- **Value:** `SHORTLIST`
- **Formatting style:** Green background, dark green text

**Rule 2 - REVIEW (Yellow):**
- **Format cells if:** "Text is exactly"
- **Value:** `REVIEW`
- **Formatting style:** Yellow background, dark yellow text

**Rule 3 - REJECT (Red):**
- **Format cells if:** "Text is exactly"
- **Value:** `REJECT`
- **Formatting style:** Red background, dark red text

### 5. Add Filter Buttons

1. Click on cell **A1**
2. Go to **Data** → **Create a filter**
3. Little dropdown arrows appear on each header

Now you can:
- Click the arrow on "YES Count" → Sort largest to smallest
- Click the arrow on "Overall Recommendation" → Show only "SHORTLIST"
- Click the arrow on "Candidate Name" → Search for specific person

### 6. Add a Summary Dashboard (Advanced - Optional)

Create a second sheet called "Dashboard" with these formulas:

**In Dashboard sheet, add:**

**A1:** `Total CVs Processed`  
**B1:** `=COUNTA('CV Screening Tracker'!B:B)-1`

**A2:** `Shortlisted`  
**B2:** `=COUNTIF('CV Screening Tracker'!O:O,"SHORTLIST")`

**A3:** `Under Review`  
**B3:** `=COUNTIF('CV Screening Tracker'!O:O,"REVIEW")`

**A4:** `Rejected`  
**B4:** `=COUNTIF('CV Screening Tracker'!O:O,"REJECT")`

**A6:** `Candidates with 3/3 YES`  
**B6:** `=COUNTIF('CV Screening Tracker'!N:N,3)`

**A7:** `Candidates with 2/3 YES`  
**B7:** `=COUNTIF('CV Screening Tracker'!N:N,2)`

---

## Example Data (for testing formatting)

After setting up, you can paste this sample data to test your formatting:

```
2024-10-22 14:30	John Smith	john_smith_cv.pdf	https://drive.google.com/...	YES	"General Manager at Small Charity Foundation (2020-2023)"	HIGH	YES	"Led team of 25 in startup charity"	HIGH	YES	"3 years in non-profit sector"	HIGH	3	SHORTLIST	Strong candidate with extensive non-profit experience as General Manager. Led operations for small charity with team of 25.

2024-10-22 14:45	Sarah Johnson	sarah_johnson_cv.pdf	https://drive.google.com/...	YES	"Operations Director at Tech Startup"	HIGH	YES	"Managed 15-person team in small enterprise"	MEDIUM	NO	"No charity sector experience mentioned"	HIGH	2	REVIEW	Good operations experience in small organization but lacks non-profit sector background. May need training on charity-specific practices.

2024-10-22 15:00	Mike Chen	mike_chen_cv.pdf	https://drive.google.com/...	NO	"Senior Developer role only"	HIGH	NO	"Worked at Fortune 500 companies"	HIGH	NO	"Tech and finance sectors only"	HIGH	0	REJECT	Technical background without management experience. Has only worked in large corporate environments in tech/finance sectors.
```

---

## Using Your Sheet

### Daily Use

1. **Check new entries:** Look at the newest rows (bottom of sheet)
2. **Click File Link:** Opens the CV in Google Drive
3. **Review Evidence:** Read what the AI found
4. **Make decision:** Based on AI recommendation + your judgment

### Filtering for Top Candidates

**Method 1 - Simple Sort:**
1. Click the filter arrow on "YES Count" (Column N)
2. Select "Sort Z → A" (highest to lowest)
3. Top candidates appear at the top

**Method 2 - Filter View:**
1. Click filter arrow on "Overall Recommendation" (Column O)
2. Uncheck "REVIEW" and "REJECT"
3. Only "SHORTLIST" candidates show

**Method 3 - Advanced:**
1. Use multiple filters together:
   - YES Count ≥ 2
   - AND Role Confidence = HIGH
   - AND Recommendation = SHORTLIST

### Exporting Results

**To share with your team:**

1. **Option A - Share the Sheet:**
   - Click "Share" button (top right)
   - Add team member emails
   - Set permissions (Viewer/Editor)

2. **Option B - Export to Excel:**
   - File → Download → Microsoft Excel (.xlsx)

3. **Option C - Export specific candidates:**
   - Filter for SHORTLIST only
   - Select visible rows
   - Copy and paste into new sheet

---

## Maintenance

### Weekly

- **Review borderline candidates** (REVIEW status)
- **Archive old entries** (move to separate sheet)
- **Check for errors** (look for empty cells)

### Monthly

- **Create archive sheet:** "October 2024 Archive"
- **Move processed data** there
- **Keep main sheet** for current month only
- **Update dashboard** (if you created one)

### Cleaning Up

**Remove test data:**
1. Select rows with test data
2. Right-click → "Delete rows"

**Archive old months:**
1. Create new sheet: "Archive - October 2024"
2. Copy old data there
3. Delete from main sheet
4. Keep last 100 entries in main sheet for reference

---

## Advanced Features

### Add Comments

Click any cell → Right-click → "Insert comment"

Useful for:
- Adding interview notes
- Flagging candidates for follow-up
- Team collaboration

### Add Checkboxes

1. Select a new column (e.g., Column Q)
2. Insert → Checkbox
3. Use for: "Contacted", "Interviewed", "Offered Role"

### Link to Other Tools

**Connect to Google Calendar:**
- Add column for "Interview Date"
- Link to Calendar events

**Connect to Gmail:**
- Add column for "Email Sent"
- Use Apps Script to auto-send emails

---

## Troubleshooting

### Data Not Appearing

**Check:**
1. Is Make.com scenario running? (should be ON)
2. Have you uploaded CVs to the Inbox folder?
3. Wait 15 minutes for processing

### Formatting Breaks

**Fix:**
1. Make sure row 1 has headers
2. Don't insert rows above row 1
3. Don't delete columns (add to the end instead)

### Links Don't Work

**Common issue:**
- Column D should contain actual URLs
- If showing "https://..." but not clickable
- Solution: Make.com is configured correctly, Google Sheets just displays as text (it's fine!)

---

## Tips & Tricks

### Quick Keyboard Shortcuts

| Action | Windows | Mac |
|--------|---------|-----|
| Bold | Ctrl+B | Cmd+B |
| Find | Ctrl+F | Cmd+F |
| Filter | Ctrl+Shift+L | Cmd+Shift+L |
| Insert row | Ctrl+Alt+= | Cmd+Option+= |
| Delete row | Ctrl+Alt+- | Cmd+Option+- |

### Best Practices

1. **Don't edit columns A-P** - Let automation fill these
2. **Add custom columns after P** - For your own notes
3. **Use filters, don't delete** - Keep historical data
4. **Regular backups** - File → Make a copy (monthly)
5. **Share as "Viewer"** - Only you should edit

---

## Ready-to-Use Template

**Quick Setup:**
1. Create new Google Sheet
2. Paste headers from top of this document
3. Apply formatting from sections above
4. You're ready!

**Or use this shareable template:**
[Link to template would go here if you create one]

---

That's it! Your tracking sheet is ready to receive data from Make.com! 📊
