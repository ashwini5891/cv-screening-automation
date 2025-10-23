# CV Screening Automation with Make.com & Claude AI

Automatically screen job applications using AI-powered analysis. This system reduces manual CV review time by 90% while maintaining consistent evaluation criteria.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Platform](https://img.shields.io/badge/platform-Make.com-purple.svg)
![AI](https://img.shields.io/badge/AI-Claude-orange.svg)

## 🎯 What This Does

This automation system:
- ✅ Monitors a Google Drive folder for new CVs
- ✅ Extracts text from PDF and DOCX files
- ✅ Uses Claude AI to analyze candidates against your criteria
- ✅ Records results in Google Sheets with evidence quotes
- ✅ Automatically organizes files into Shortlisted/Review folders

**No coding required** - just follow the setup guide!

## 📊 Results

- **Time saved:** ~90% reduction in screening time
- **Consistency:** Every CV assessed against the same criteria
- **Accuracy:** AI provides evidence quotes from CVs
- **Tracking:** Complete audit trail in spreadsheet

## 💰 Cost

- **Make.com:** FREE (1,000 operations/month ≈ 140 CVs)
- **Claude API:** ~$0.01 per CV ($5 free credit included)
- **Google Workspace:** FREE (Drive + Sheets)

**Total: Essentially free for most small businesses**

## ⚡ Quick Start

### Prerequisites
- Google Account (Gmail)
- Make.com account (free tier)
- Claude API key (~$5 free credit)
- 30-45 minutes for setup

### Setup Steps

1. **Clone or download this repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/cv-screening-automation.git
   ```

2. **Follow the complete setup guide**
   - Start with: [`docs/make-com-complete-setup-guide.md`](docs/make-com-complete-setup-guide.md)
   - Estimated time: 30-45 minutes

3. **Set up your Google Sheets**
   - Use: [`docs/google-sheets-template-guide.md`](docs/google-sheets-template-guide.md)

4. **Import the Make.com template**
   - Template: [`templates/make-com-cv-screening-blueprint.json`](templates/make-com-cv-screening-blueprint.json)

## 📁 Repository Structure

```
cv-screening-automation/
├── README.md                          # You are here
├── docs/
│   ├── make-com-complete-setup-guide.md   # Main setup instructions
│   └── google-sheets-template-guide.md    # Spreadsheet configuration
├── templates/
│   └── make-com-cv-screening-blueprint.json  # Make.com scenario template
└── examples/
    └── (coming soon - sample CVs and results)
```

## 🎓 Documentation

### For Beginners
Start with the **[Complete Setup Guide](docs/make-com-complete-setup-guide.md)** - written for non-technical users with step-by-step instructions.

### For Technical Users
Review the **[Scenario Blueprint](templates/make-com-cv-screening-blueprint.json)** to understand the workflow structure.

## 🔧 How It Works

### Workflow Overview

```
New CV Uploaded → Extract Text → AI Analysis → Update Sheet → Move File
     (Drive)         (Parse)       (Claude)      (Sheets)     (Organize)
```

### Screening Criteria (Customizable)

1. **Role Experience:** Has the candidate done this role before?
2. **Organization Size:** Have they worked in similar-sized companies?
3. **Sector Experience:** Have they worked in the same industry?

Each criterion receives:
- **Score:** YES / NO / UNCLEAR
- **Evidence:** Direct quote from CV
- **Confidence:** HIGH / MEDIUM / LOW

## 📈 Features

### Core Features
- ✅ Automated CV text extraction (PDF & DOCX)
- ✅ AI-powered candidate assessment
- ✅ Structured data output (Google Sheets)
- ✅ Automatic file organization
- ✅ Evidence-based scoring

### Advanced Features
- 🎨 Customizable screening criteria
- 📊 Conditional formatting in spreadsheet
- 🔄 Configurable check frequency
- 📁 Smart folder organization
- 🔍 Full audit trail

### Optional Enhancements
- 📧 Email notifications for top candidates
- 📅 Interview scheduling integration
- 🔗 ATS integration
- 📊 Reporting dashboards
- 🌍 Multi-language support

## 🚀 Use Cases

Perfect for:
- **Small Businesses:** Streamline hiring without dedicated HR
- **Startups:** Scale recruitment efficiently
- **Non-Profits:** Maximize limited resources
- **Consultants:** Offer as a service
- **HR Teams:** Focus on interviews, not admin

## 🛠️ Customization

### Change Screening Criteria
Edit the AI prompt in Module 4 of the Make.com scenario. Examples:
- Technical skills assessment
- Years of experience requirements
- Education qualifications
- Language proficiency

### Adjust Scoring Logic
Modify Module 7 to change how files are organized:
- Require 3/3 YES for shortlist
- Require 2/3 YES and HIGH confidence
- Create additional folders (e.g., "Maybe", "Strong Maybe")

See the [Setup Guide](docs/make-com-complete-setup-guide.md) for detailed customization instructions.

## 🔒 Privacy & Security

- ✅ All data stored in your Google account
- ✅ Claude API doesn't retain CV data
- ✅ Encrypted connections (HTTPS)
- ✅ GDPR considerations included in guide

**Important:** Always inform candidates if using AI screening.

## 📞 Support & Community

### Getting Help
- **Issues:** Open a GitHub issue
- **Questions:** Check the [Setup Guide](docs/make-com-complete-setup-guide.md) troubleshooting section
- **Discussions:** Use GitHub Discussions

### Contributing
Contributions welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Submit a pull request

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Make.com** - Workflow automation platform
- **Anthropic** - Claude AI API
- **Google Workspace** - Drive & Sheets integration

## ⭐ Star This Repo

If this project helped you, please give it a star! It helps others discover it.

## 📮 Contact

Questions or suggestions? Open an issue or discussion on GitHub.

---

**Made with ❤️ for efficient hiring**

*Last updated: October 2024*
