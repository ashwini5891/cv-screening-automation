# CV Screening Automation with Make.com and Claude AI

Automatically screen job applications using AI-powered analysis. This system reduces manual CV review time by 90% whilst maintaining consistent evaluation criteria.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Platform](https://img.shields.io/badge/platform-Make.com-purple.svg)
![AI](https://img.shields.io/badge/AI-Claude-orange.svg)

## Overview

This automation system provides:
- Monitoring of Google Drive folders for new CVs
- Text extraction from PDF and DOCX files
- Claude AI analysis of candidates against your criteria
- Recording of results in Google Sheets with evidence quotations
- Automatic organisation of files into Shortlisted/Review folders

No coding required. Simply follow the setup guide.

## Results and Benefits

**Time savings:** Approximately 90% reduction in screening time  
**Consistency:** Every CV assessed against identical criteria  
**Accuracy:** AI provides evidence quotations from CVs  
**Tracking:** Complete audit trail in spreadsheet format

## Cost Structure

**Make.com:** Free tier (1,000 operations per month, approximately 140 CVs)  
**Claude API:** Approximately £0.01 per CV (£5 free credit included)  
**Google Workspace:** Free (Drive and Sheets)

**Total cost:** Essentially free for most small businesses

## Quick Start

### Prerequisites
- Google Account (Gmail)
- Make.com account (free tier)
- Claude API key (approximately £5 free credit available)
- 30 to 45 minutes for setup

### Setup Steps

**1. Clone or download this repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/cv-screening-automation.git
   ```

**2. Follow the complete setup guide**
   - Start with: [`docs/make-com-complete-setup-guide.md`](docs/make-com-complete-setup-guide.md)
   - Estimated time: 30 to 45 minutes

**3. Set up your Google Sheets**
   - Use: [`docs/google-sheets-template-guide.md`](docs/google-sheets-template-guide.md)

**4. Import the Make.com template**
   - Template: [`templates/make-com-cv-screening-blueprint.json`](templates/make-com-cv-screening-blueprint.json)

## Repository Structure

```
cv-screening-automation/
├── README.md                                   (This document)
├── docs/
│   ├── make-com-complete-setup-guide.md       (Main setup instructions)
│   └── google-sheets-template-guide.md        (Spreadsheet configuration)
├── templates/
│   └── make-com-cv-screening-blueprint.json   (Make.com scenario template)
└── examples/
    └── sample-test-cvs.md                      (Sample CVs and test data)
```

## Documentation

### For Non-Technical Users
Begin with the **[Complete Setup Guide](docs/make-com-complete-setup-guide.md)**, which provides step-by-step instructions written for non-technical users.

### For Technical Users
Review the **[Scenario Blueprint](templates/make-com-cv-screening-blueprint.json)** to understand the workflow structure and technical implementation.

## System Architecture

### Workflow Overview

```
New CV Uploaded → Extract Text → AI Analysis → Update Sheet → Move File
     (Drive)         (Parse)       (Claude)      (Sheets)     (Organise)
```

### Screening Criteria (Customisable)

The system evaluates candidates against three criteria:

**1. Role Experience**  
Has the candidate performed this role previously, or an equivalent position?

**2. Organisation Size**  
Have they worked in similarly sized companies?

**3. Sector Experience**  
Have they worked in the same industry?

Each criterion receives:
- **Score:** YES / NO / UNCLEAR
- **Evidence:** Direct quotation from CV
- **Confidence:** HIGH / MEDIUM / LOW

## Features

### Core Functionality
- Automated CV text extraction (PDF and DOCX formats)
- AI-powered candidate assessment
- Structured data output (Google Sheets)
- Automatic file organisation
- Evidence-based scoring system

### Advanced Features
- Customisable screening criteria
- Conditional formatting in spreadsheet
- Configurable check frequency
- Smart folder organisation
- Complete audit trail

### Optional Enhancements
- Email notifications for top candidates
- Interview scheduling integration
- Applicant Tracking System (ATS) integration
- Reporting dashboards
- Multi-language support

## Use Cases

This system is particularly suitable for:

**Small Businesses**  
Streamline hiring processes without dedicated HR resources

**Startups**  
Scale recruitment efforts efficiently as the organisation grows

**Non-Profit Organisations**  
Maximise limited resources whilst maintaining quality standards

**Recruitment Consultants**  
Offer as an additional service to clients

**HR Teams**  
Focus on candidate interviews rather than administrative tasks

## Customisation

### Modifying Screening Criteria

Edit the AI prompt in Module 4 of the Make.com scenario to assess different criteria. Examples include:
- Technical skills assessment
- Years of experience requirements
- Educational qualifications
- Language proficiency

### Adjusting Scoring Logic

Modify Module 7 to change file organisation rules:
- Require 3/3 YES scores for shortlisting
- Require 2/3 YES scores with HIGH confidence
- Create additional folders (e.g., "Possible", "Strong Candidate")

Refer to the [Setup Guide](docs/make-com-complete-setup-guide.md) for detailed customisation instructions.

## Privacy and Security

**Data storage:** All data stored in your Google account  
**API retention:** Claude API does not retain CV data  
**Connections:** All connections encrypted (HTTPS)  
**Compliance:** GDPR considerations included in guide

**Important:** Candidates should be informed if AI screening is used in the recruitment process.

## Support and Community

### Obtaining Help
**Issues:** Open a GitHub issue for bug reports  
**Questions:** Consult the [Setup Guide](docs/make-com-complete-setup-guide.md) troubleshooting section  
**Discussions:** Use GitHub Discussions for general queries

### Contributing

Contributions are welcome. Please:
1. Fork the repository
2. Create a feature branch
3. Submit a pull request

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

## Licence

This project is licenced under the MIT Licence. See the [LICENSE](LICENSE) file for full details.

## Acknowledgements

**Make.com**  
Workflow automation platform

**Anthropic**  
Claude AI API provider

**Google Workspace**  
Drive and Sheets integration

## Repository Recognition

If this project proves helpful, please consider starring the repository to help others discover it.

## Contact

For questions or suggestions, please open an issue or discussion on GitHub.

---

**Developed for efficient recruitment processes**

*Last updated: October 2024*