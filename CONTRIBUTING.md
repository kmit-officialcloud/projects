# Contributing to KMIT Projects Repository

Welcome to the official KMIT projects repository! This guide will help you submit your academic projects following our contribution workflow and best practices.

## Repository Purpose

This repository serves as the central hub for student project submissions across KMIT's Software Development curriculum. It facilitates organized collaboration, code review, and knowledge sharing among students, faculty, and maintainers.

**Courses included:**
- **SDC-I** — Skill Development Course I
- **RTRP** — Real Time Research Projects
- **SDC-II** — Skill Development Course II

---

## Before You Start

- Ensure you have a GitHub account
- Install Git on your machine
- Familiarize yourself with Git and GitHub basics
- Read through this entire guide before submitting

---

## Contribution Workflow

### Step 1: Fork the Repository

Click the **Fork** button on the repository page. This creates your own copy of the repository under your GitHub account.

```bash
# After forking, you'll have:
# https://github.com/YOUR_USERNAME/projects
```

### Step 2: Clone Your Fork Locally

Clone your forked repository to your computer:

```bash
git clone https://github.com/YOUR_USERNAME/projects.git
cd projects
```

### Step 3: Create Your Project Folder

Navigate to the appropriate course directory and create a folder for your project:

```bash
cd SDC-I
# or: cd RTRP
# or: cd SDC-II

mkdir your-project-folder-name
cd your-project-folder-name
```

### Step 4: Proper Project Naming

Follow these naming conventions:

| Format | Example | Notes |
|--------|---------|-------|
| **Recommended** | `FirstName-LastName-ProjectTitle` | Clear and descriptive |
| **Alternative** | `ProjectTitle-Year-Semester` | If team project |
| **Avoid** | `MyProject`, `Project123`, `test` | Too generic |

**Guidelines:**
- Use hyphens to separate words (not underscores or spaces)
- Use lowercase letters
- Keep names under 50 characters
- Be descriptive of the project purpose

**Example:**
```
john-doe-expense-tracker
```

### Step 5: Folder Structure

Organize your project folder as follows:

```
your-project-folder-name/
│
├── README.md                 # Project documentation (required)
├── src/                      # Source code directory
│   ├── main.py              # Main application file
│   ├── utils/               # Utility modules
│   └── ...
├── docs/                     # Additional documentation (optional)
│   ├── API.md               # API documentation
│   ├── SETUP.md             # Setup instructions
│   └── ...
├── tests/                    # Test files (optional but recommended)
│   ├── test_main.py
│   └── ...
├── screenshots/             # Project screenshots (optional)
│   ├── home.png
│   ├── dashboard.png
│   └── ...
├── .gitignore              # Git ignore file (required)
├── requirements.txt        # Dependencies (if Python)
├── package.json            # Dependencies (if Node.js)
└── LICENSE                 # License file (optional)
```

### Step 6: README Requirements

Every project **must include** a comprehensive `README.md` file. Use this template:

```markdown
# Project Title

## 📋 Overview
Brief description of your project (2-3 sentences).

## ✨ Features
- Feature one
- Feature two
- Feature three

## 🛠️ Technology Stack
- **Language:** Python 3.9
- **Framework:** Flask
- **Database:** SQLite
- **Libraries:** pandas, requests

## 📦 Installation

### Prerequisites
- Python 3.8 or higher
- Git

### Setup
1. Clone this repository
2. Create virtual environment: `python -m venv venv`
3. Activate: `source venv/bin/activate` (Linux/Mac) or `venv\Scripts\activate` (Windows)
4. Install dependencies: `pip install -r requirements.txt`

## 🚀 Usage
```bash
python src/main.py
```

Detailed usage instructions here.

## 📸 Screenshots
[Add project screenshots if applicable]

## 📚 Documentation
- [Setup Guide](SETUP.md)
- [API Documentation](API.md)

## 👨‍💻 Author
- **Student Name:** John Doe
- **Roll Number:** 21K-1234
- **Year:** Second Year
- **Faculty Guide:** Prof. Jane Smith

## 📝 License
This project is licensed under the MIT License - see [LICENSE](LICENSE) file.

## 🙏 Acknowledgments
- Keshav Memorial Institute of Technology
- Course Instructors
- Peers and Mentors
```

### Step 7: Commit Message Conventions

Write clear, descriptive commit messages:

```bash
# Good examples
git commit -m "Add user authentication module"
git commit -m "Fix login validation error"
git commit -m "Update project documentation"
git commit -m "Add database schema for products"

# Avoid
git commit -m "fixed stuff"
git commit -m "updates"
git commit -m "asdf"
```

**Commit message format:**
- Start with an action verb (Add, Fix, Update, Remove, Refactor)
- Keep it under 50 characters
- Use present tense
- Be specific

### Step 8: .gitignore File

Include a `.gitignore` file in your project folder to exclude unnecessary files:

```
# Python
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
venv/
env/
.env

# Node.js
node_modules/
npm-debug.log
.env

# IDE
.vscode/
.idea/
*.sublime-project

# Database
*.db
*.sqlite
*.sqlite3

# Secrets
*.pem
*.key
.env.local
secrets.json

# OS
.DS_Store
Thumbs.db
```

### Step 9: Commit Your Changes

Add your project files and commit:

```bash
git add .
git commit -m "Add project: [Your Project Name]"
```

### Step 10: Push to Your Fork

Push your changes to your forked repository:

```bash
git push origin main
# or: git push origin master
```

### Step 11: Create a Pull Request

1. Go to your forked repository on GitHub
2. Click the **"Compare & pull request"** button
3. Ensure the base repository is `kmit-officialcloud/projects`
4. Fill out the Pull Request template completely (see below)
5. Click **"Create Pull Request"**

### Step 12: Pull Request Template

Your PR will be pre-filled with our template. Complete all sections:

```markdown
# Project Information

**Project Name:** Your Project Title

**Course:** 
- [ ] SDC-I
- [ ] RTRP
- [ ] SDC-II

**Student Name:** Your Name
**Roll Number:** 21K-1234
**Department:** CSE/ECE/Mech
**Year:** First/Second/Third

---

# Project Description

Brief overview of what your project does.

---

# Features

- [ ] Feature 1
- [ ] Feature 2
- [ ] Feature 3

---

# Technology Stack

- **Language:** Python
- **Framework:** Flask
- **Database:** SQLite

---

# Checklist

- [ ] My project builds successfully
- [ ] README.md is included and complete
- [ ] Documentation is clear and comprehensive
- [ ] Screenshots/demos are included (if applicable)
- [ ] Source code is included
- [ ] No secrets or API keys committed
- [ ] No plagiarism - all code is my own work
- [ ] Project placed in correct course folder
- [ ] Project tested and working
- [ ] Follows naming conventions

---

# Additional Notes

Any additional information for reviewers.
```

### Step 13: Code Review Process

1. **Faculty Review:** Your course instructor or a faculty member will review your submission
2. **Feedback:** Comments may be requested for improvements
3. **Revisions:** Make requested changes and push to the same branch
4. **Approval:** Once approved, your PR will be merged
5. **Completion:** Your project is now part of the official repository

**Review timeline:** Usually 3-7 business days

---

## What NOT to Do

❌ **DO NOT** push directly to the main branch
- Always submit through Pull Requests
- Direct pushes will be rejected

❌ **DO NOT** commit sensitive information
- Never commit passwords or API keys
- Never commit database backups
- See [SECURITY.md](SECURITY.md) for details

❌ **DO NOT** commit plagiarized code
- All code must be your own original work
- Cite external resources properly
- See [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)

❌ **DO NOT** modify other students' projects
- Respect others' work and intellectual property
- Only submit your own projects

❌ **DO NOT** commit large binary files
- Use `.gitignore` to exclude them
- Keep repository size reasonable

❌ **DO NOT** submit incomplete projects
- Ensure your project is fully functional
- Include all necessary documentation

---

## Best Practices

### Code Quality
- Write clean, readable code
- Add comments for complex logic
- Follow language-specific style guides
  - Python: PEP 8
  - JavaScript: Airbnb Style Guide
  - Java: Google Java Style Guide

### Documentation
- Always include a comprehensive README
- Document setup and installation steps
- Explain how to use your project
- Include API documentation if applicable

### Testing
- Test your project before submission
- Include unit tests if possible
- Document test procedures

### Version Control
- Commit frequently with meaningful messages
- Keep commits logical and focused
- Avoid giant single commits

### Project Organization
- Keep folder structure clean and logical
- Don't clutter root directory
- Organize code into modules

### README Screenshots
- Add 2-3 screenshots of your working project
- Show the main features in action
- Include screenshots in `screenshots/` folder

---

## Frequently Asked Questions

### Q: I made a mistake in my commit. How do I fix it?

**A:** Use interactive rebase:
```bash
git rebase -i HEAD~1
```

Or amend your last commit:
```bash
git commit --amend
git push origin branch-name --force-with-lease
```

### Q: How do I sync my fork with the main repository?

**A:**
```bash
git remote add upstream https://github.com/kmit-officialcloud/projects.git
git fetch upstream
git rebase upstream/main
git push origin main
```

### Q: Can I work on multiple projects?

**A:** Yes! Create separate folders for each project within the appropriate course directory. Each project will have its own separate Pull Request.

### Q: How long does review take?

**A:** Typically 3-7 business days. Faculty reviewers evaluate each submission carefully.

### Q: Can I edit my project after it's merged?

**A:** Yes, but create a new Pull Request for updates. Reference the original PR in your new PR.

### Q: What if my Pull Request gets rejected?

**A:** Don't worry! Review the feedback, make requested changes, push to your branch, and resubmit. The Pull Request will automatically update.

### Q: Can I delete files from the repository?

**A:** No. All Pull Requests are merge-only. Contact repository maintainers if there's an issue.

### Q: What language should I use for my project?

**A:** Any language is acceptable. Ensure proper documentation and installation instructions.

### Q: Is there a project size limit?

**A:** Keep repositories under 100 MB. Exclude large datasets, binaries, and dependencies from version control.

### Q: Can I use external libraries and frameworks?

**A:** Yes! Document all dependencies clearly in `requirements.txt`, `package.json`, or equivalent.

---

## Getting Help

Stuck? Here's where to find help:

1. **Read the README** — Most answers are there
2. **Check Existing Issues** — Your question may be answered already
3. **Open a GitHub Issue** — Describe your problem clearly with:
   - What you're trying to do
   - What error you're seeing
   - Steps to reproduce
   - Your environment (OS, language version, etc.)
4. **Contact Your Instructor** — For course-specific questions
5. **Email Repository Maintainers** — For repository setup issues

For more information, see [SUPPORT.md](SUPPORT.md).

---

## Code of Conduct

All contributors must follow our [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md). We are committed to providing a respectful, inclusive, and professional environment for all.

---

## Additional Resources

- [GitHub Guides](https://guides.github.com/)
- [Git Documentation](https://git-scm.com/doc)
- [GitHub Issues](https://guides.github.com/features/issues/)
- [KMIT Official Website](https://kmit.in/)

---

Thank you for contributing to KMIT Projects! We look forward to reviewing your work.

**Happy coding!** 🚀

---

*Last updated: 2026*
*Maintained by: KMIT Repository Team*
