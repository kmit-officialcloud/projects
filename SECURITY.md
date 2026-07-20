# Security Policy

## Overview

This repository contains educational software projects created by KMIT students. While this is an academic repository, security best practices are essential to protect both the repository and its contributors.

**This document outlines security guidelines for all contributors.**

---

## What Should NOT Be Committed

### 🔴 Critical: Never Commit Secrets

The following should **NEVER** be committed to this repository:

#### Passwords
- Database passwords
- Application account passwords
- SSH passphrases
- Any login credentials

```python
# ❌ WRONG - Never do this!
database_password = "MySecurePassword123!"
admin_user = "admin"
admin_pass = "admin123"

# ✅ RIGHT - Use environment variables
import os
database_password = os.getenv('DB_PASSWORD')
```

#### API Keys and Tokens
- Third-party API keys (Google, AWS, GitHub, etc.)
- Authentication tokens
- OAuth tokens
- Webhook secrets
- Bearer tokens
- JWT secrets

```python
# ❌ WRONG
api_key = "sk_live_51234567890abcdefghijk"
google_maps_key = "AIzaSyD1234567890abcdefghijk"

# ✅ RIGHT - Use environment variables
api_key = os.getenv('API_KEY')
google_maps_key = os.getenv('GOOGLE_MAPS_KEY')
```

#### Application Passwords
- Microsoft App Passwords
- GitHub Personal Access Tokens (PAT)
- Docker credentials
- Cloud platform credentials

```bash
# ❌ WRONG
docker login -u myusername -p mypassword

# ✅ RIGHT - Use credentials from environment or secure storage
docker login -u myusername
# Enter password when prompted
```

#### Environment Variables (.env files)
- Never commit `.env`, `.env.local`, `.env.production` files
- Never commit configuration files with secrets

```
# ❌ WRONG - These should be in .gitignore
.env
.env.local
.env.staging
.env.production
config.local.js
secrets.json
```

### 🔴 High Priority: Never Commit Sensitive Data

#### Database Exports
- Database dumps containing user data
- Database backups
- SQL scripts with sample data including credentials
- Any database exports

```sql
-- ❌ WRONG - Never commit database dumps with real data
INSERT INTO users VALUES (1, 'user@example.com', 'password123');
INSERT INTO users VALUES (2, 'admin@example.com', 'admin_pass');
```

#### Personally Identifiable Information (PII)
- Real user data
- Email addresses
- Phone numbers
- Home addresses
- Social security numbers
- Student IDs (actual numbers with personally identifying data)
- Banking information
- Medical information

```json
// ❌ WRONG
{
  "users": [
    {"id": 1, "name": "John Doe", "email": "john@example.com", "phone": "555-1234"},
    {"id": 2, "name": "Jane Smith", "ssn": "123-45-6789"}
  ]
}

// ✅ RIGHT - Use anonymized test data
{
  "users": [
    {"id": 1, "name": "User1", "email": "test1@example.com"},
    {"id": 2, "name": "User2", "email": "test2@example.com"}
  ]
}
```

#### Private Keys and Certificates
- SSL/TLS certificates with private keys
- SSH private keys (`.pem`, `.key`, `.ppk` files)
- PGP keys
- AWS key pairs
- Any cryptographic private keys

```
# ❌ WRONG - Never commit private keys
id_rsa
server.pem
private_key.key
mycert.p8
```

#### Configuration Files with Secrets
- `config.js` or `config.py` with API keys
- `settings.json` with credentials
- `.AWS` configuration
- Cloud platform configuration files

### 🟡 Medium Priority: Large Files and Binaries

While not security issues, avoid committing:
- Large video or image files (use alternatives like LFS)
- Compiled binaries or executables
- Archive files (.zip, .tar, .rar)
- IDE workspace settings containing paths

---

## Setting Up .gitignore

Create a `.gitignore` file in your project root to exclude sensitive files:

### Python Projects

```
# Environment variables
.env
.env.local
.env.*.local

# Virtual environment
venv/
env/
ENV/
env.bak/
venv.bak/

# Secrets
secrets.json
config.local.py

# IDE
.vscode/
.idea/
*.sublime-project
.DS_Store

# Python
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
dist/
build/
```

### Node.js Projects

```
# Environment variables
.env
.env.local
.env.*.local

# Dependencies
node_modules/
npm-debug.log
yarn-error.log

# Secrets
.env.development.local
.env.test.local
.env.production.local

# IDE
.vscode/
.idea/
*.sublime-project

# OS
.DS_Store
Thumbs.db
```

### Java Projects

```
# Environment variables
.env
.env.local

# Build
target/
*.class
*.jar
*.war

# IDE
.idea/
.vscode/
*.iml
.DS_Store

# Secrets
application-local.properties
application-dev.properties
```

### General Template

```
# Environment files
.env
.env.local
.env.*.local
.env.production
config.local.*

# Secrets and credentials
secrets.json
credentials.json
*.pem
*.key
*.p8
id_rsa
id_rsa.pub

# Database files and exports
*.db
*.sqlite
*.sqlite3
database_export.sql

# IDE and Editor
.vscode/
.idea/
*.sublime-project
.DS_Store
Thumbs.db

# Dependencies
node_modules/
venv/
env/
ENV/

# Build outputs
dist/
build/
*.pyc

# Logs
npm-debug.log
yarn-error.log
```

---

## Before You Submit: Security Checklist

Before creating your Pull Request, verify that:

- [ ] **No passwords** are in my code
- [ ] **No API keys** are in my code
- [ ] **No .env files** are committed
- [ ] **No database dumps** with real data are included
- [ ] **No personal information** (emails, phone numbers, IDs) is committed
- [ ] **No private keys** are included
- [ ] **No sensitive credentials** of any kind are present
- [ ] **`.gitignore` file is created** and includes sensitive file types
- [ ] **All configuration files** contain placeholder values only
- [ ] **No credentials** appear in commit messages or comments

---

## If You Accidentally Committed Secrets

If you realize you've committed sensitive information, **act immediately:**

### Step 1: Stop Immediately
- Don't push to the repository
- Notify your instructor immediately
- Contact repository maintainers

### Step 2: Amend Your Commit

If not yet pushed, amend your last commit:

```bash
# Remove the file from staging
git reset HEAD filename

# Update the file to remove secrets
# Edit the file and remove sensitive data

# Add the updated file
git add filename

# Amend the commit
git commit --amend

# Force push ONLY to your fork (never to main repository)
git push origin branch-name --force-with-lease
```

### Step 3: Rebase to Remove from History

If commit history contains secrets:

```bash
# Interactive rebase to last N commits
git rebase -i HEAD~5

# Mark the commit with 'edit'
# When stopped at that commit:
git reset HEAD~1
# Edit file to remove secrets
git add .
git commit -m "Remove sensitive data"
git rebase --continue

# Force push to your fork only
git push origin branch-name --force-with-lease
```

### Step 4: Report the Incident
- If already pushed, email contact@kmit.in
- Describe what was exposed and when
- Explain steps taken to remediate

### Step 5: Invalidate Credentials
- If real API keys were exposed, invalidate them immediately
- Create new credentials
- Update your local `.env` files

---

## Best Practices for Managing Secrets

### Use Environment Variables

Python example:
```python
import os
from dotenv import load_dotenv

load_dotenv()  # Load from .env file (in development only)

API_KEY = os.getenv('API_KEY')
DB_PASSWORD = os.getenv('DB_PASSWORD')
```

Node.js example:
```javascript
require('dotenv').config();

const apiKey = process.env.API_KEY;
const dbPassword = process.env.DB_PASSWORD;
```

Java example:
```java
public class Config {
    public static final String API_KEY = System.getenv("API_KEY");
    public static final String DB_PASSWORD = System.getenv("DB_PASSWORD");
}
```

### Create .env.example

Commit a template file showing required environment variables:

```
# .env.example - Copy this file to .env and fill in actual values

# Database Configuration
DB_HOST=localhost
DB_PORT=5432
DB_NAME=myapp_db
DB_USER=your_username
DB_PASSWORD=your_password_here

# API Configuration
API_KEY=your_api_key_here
API_SECRET=your_api_secret_here

# Application Settings
DEBUG=false
ENVIRONMENT=production
```

### Document Required Secrets

In your README.md:

```markdown
## Environment Setup

1. Copy `.env.example` to `.env`
2. Fill in the following values:
   - `API_KEY` - Get from [API Provider](link)
   - `DB_PASSWORD` - Your database password
   - `SECRET_KEY` - Generate a secure key

Never commit your `.env` file!
```

### Use Secure Default Values

```python
# ✅ GOOD - Uses environment variable with fallback
SECRET_KEY = os.getenv('SECRET_KEY', 'dev-key-not-for-production')

# ❌ WRONG - Hardcoded production secret
SECRET_KEY = 'my-production-secret-12345'
```

---

## Reporting Security Issues

### For Repository Security Issues

If you discover a security vulnerability in **how this repository operates** (not your project code):

1. **Do NOT open a public GitHub issue**
2. **Email: contact@kmit.in**
   - Subject: "[SECURITY] Repository Vulnerability Report"
   - Description: Detailed explanation of the security issue

### For Your Project Code Issues

If your project has a security vulnerability:

1. Immediately notify your course instructor
2. Create a private discussion with maintainers (if available)
3. Do not publicly disclose details until patched

### Responsible Disclosure

We follow responsible disclosure principles:

- Report security issues privately
- Allow time for remediation before public disclosure
- Do not attempt to exploit vulnerabilities
- Act in good faith
- Keep vulnerability details confidential until fixed

---

## Third-Party Dependencies

### Dependency Security

When using external libraries:

1. **Use official sources only**
   - Python: `pip install package-name`
   - JavaScript: `npm install package-name`
   - Java: Use official Maven repositories

2. **Keep dependencies updated**
   - Regularly update to latest versions
   - Check for security patches
   - Monitor for vulnerabilities

3. **Review dependencies**
   - Understand what each library does
   - Check for known vulnerabilities
   - Use tools like:
     - `npm audit` for Node.js
     - `safety` for Python
     - GitHub Dependabot

4. **Document dependencies**
   - Maintain `requirements.txt`, `package.json`, etc.
   - Include version numbers
   - Never commit `node_modules` or similar directories

---

## Security in Documentation

### What to Include in README

✅ Include in documentation:
- How to set up environment variables
- Required API keys and where to get them
- Testing credentials for demo accounts
- Security best practices for users

❌ Never include in documentation:
- Example API keys (use placeholders)
- Production credentials
- Real passwords
- Sensitive configuration values

---

## Additional Resources

- [OWASP Top 10](https://owasp.org/www-project-top-ten/) - Common security vulnerabilities
- [GitHub Security Best Practices](https://docs.github.com/en/code-security) - Official GitHub security guide
- [Git Secrets Tool](https://github.com/awslabs/git-secrets) - Prevent secrets in Git
- [TruffleHog](https://github.com/trufflesecurity/trufflehog) - Detect secrets in repositories

---

## Questions About Security?

If you're unsure whether something should be committed:

1. **When in doubt, leave it out** — err on the side of caution
2. **Ask your instructor** — they can provide guidance
3. **Check this document** — review the security checklist
4. **Email contact@kmit.in** — with your specific question

---

## Commitment to Security

As members of the KMIT community, we all share responsibility for maintaining a secure repository. By following these guidelines, you protect:

- Your own credentials and accounts
- Other students' work and privacy
- KMIT's institutional security
- The integrity of the project repository

Thank you for prioritizing security in your contributions.

---

*Last updated: 2026*
*Maintained by: KMIT Repository Team*
