<!-- AI CONTEXT
This is a FACT SHEET for an IT system. When responding:
- Use only this document. If the answer isn't here, say so. Do not
- Lead with a clear, jargon-light answer. Follow with technical details only if needed to complete the task.
- Match the user's language. If they ask in plain terms, respond in plain terms. If they use technical terminology, you can mirror it.
- For support issues, prioritize the Support Procedures section.
- Assume the reader is competent but may be outside their specialty. Clarity trumps precision.
-->
# Application Knowledge Base - Small Business Edition

## Application Overview

**Application Name:** [Enter application name]

**Description:** [Brief description of what this application does]

**Business Purpose:** [Why this application exists and what business function it serves]

**Environment:** [Production / Staging / Development]

**Criticality Level:** [Critical / High / Medium / Low]

**Owner/Team:** [Team or individual responsible]

**Primary Contact:** [Name, email, phone]

**Secondary Contact:** [Name, email, phone]

---

## Technical Information

### Technology Stack
- **Language/Framework:** [e.g., Java Spring Boot, Python Django, .NET Core, PHP Laravel]
- **Runtime Version:** [e.g., Java 17, Python 3.11, PHP 8.2]
- **Web Server:** [e.g., Nginx, Apache, IIS]

### Version Information
- **Current Version:** [e.g., v2.3.1]
- **Last Updated:** [Date]
- **Release Schedule:** [e.g., Monthly, Quarterly, As needed]

### Dependencies
- **External APIs:** [List any external services this app depends on]
- **Internal Services:** [List internal dependencies]
- **Key Libraries:** [Main third-party packages]

---

## Hosting & Access

### Hosting Information
- **Hosting Provider:** [e.g., AWS, DigitalOcean, Linode, Heroku, Vercel]
- **Hosting Plan:** [e.g., Business plan, $50/month tier]
- **Server Location:** [e.g., US East, EU West]
- **Account Owner:** [Who owns the hosting account]

### URLs & Access
- **Public URL:** [e.g., https://app.company.com]
- **Admin Portal:** [if separate, e.g., https://app.company.com/admin]
- **VPN Required:** [Yes/No]

### Server Details
- **Server/Instance Type:** [e.g., t3.medium, 2 vCPU / 4GB RAM]
- **Operating System:** [e.g., Ubuntu 22.04]
- **IP Address:** [if static]
- **Ports Used:** [e.g., 80 (HTTP), 443 (HTTPS)]

---

## Database

**Database Type:** [e.g., PostgreSQL, MySQL, MongoDB]

**Database Version:** [e.g., PostgreSQL 15]

**Database Hosting:** [Same server / Managed service (e.g., AWS RDS, Heroku Postgres)]

**Database Name:** [database name]

**Backup:** [Automatic via hosting provider / Manual - describe schedule]

---

## Authentication & Access

### Login Information
- **Authentication Type:** [e.g., Email/Password, Google OAuth, SSO]
- **SSO Provider:** [if applicable, e.g., Google Workspace, Microsoft 365]
- **MFA Enabled:** [Yes/No]

### Access Management
- **Admin Access:** [Who has admin rights and how to grant access]
- **User Access:** [How users get access - e.g., invite system, self-signup]
- **Password Reset:** [How users reset passwords]

### Credentials Storage
- **Where Credentials Are Stored:** [e.g., 1Password, LastPass, Bitwarden]
- **Service Accounts:** [If any service accounts exist, list them - not the passwords]

---

## Common Support Issues

### Issue 1: [e.g., Login Problems]
- **What users report:** [e.g., "Can't log in"]
- **Common causes:** [e.g., Forgot password, account not activated]
- **How to fix:**
  1. [Step 1, e.g., Send password reset link]
  2. [Step 2, e.g., Verify email address is correct]
  3. [Step 3, e.g., Check if account is active]
- **When to escalate:** [e.g., If password reset doesn't work]

### Issue 2: [e.g., Slow Performance]
- **What users report:** [e.g., "App is slow"]
- **Common causes:** [e.g., High traffic, database needs optimization]
- **How to fix:**
  1. [Step 1]
  2. [Step 2]
- **When to escalate:** [e.g., If issue persists after 30 minutes]

### Issue 3: [Add more as needed]
- **What users report:**
- **Common causes:**
- **How to fix:**
- **When to escalate:**

### Quick Troubleshooting
1. **Is the app up?** [How to check - e.g., visit URL, check hosting dashboard]
2. **Check recent errors:** [Where to look - e.g., hosting logs, application logs]
3. **Database connectivity:** [How to verify database is running]
4. **Recent changes:** [Check if anything was deployed recently]

### Known Issues
- [List any known bugs or limitations]
- [Workarounds if available]

---

## Maintenance & Operations

### Restart Procedures

**How to restart the application:**
```bash
# If using a hosting provider dashboard:
# Log in → Select app → Click "Restart"

# If using command line:
# [Include specific commands for your setup]
```

**Impact:** [e.g., 1-2 minute downtime]

**When to restart:** [e.g., After configuration changes, if app is unresponsive]

### Deployment Process
1. **Before deploying:**
   - [e.g., Test in staging, notify team]

2. **Deploy:**
   - [e.g., Push to main branch, click deploy button in hosting dashboard]

3. **After deploying:**
   - [e.g., Verify app loads, test key features]

**Preferred deployment time:** [e.g., Outside business hours, Tuesday afternoons]

**Rollback:** [How to undo a deployment if something breaks]

### Monitoring

**How to check if app is running:**
- [e.g., Visit URL, check uptime monitor]

**Uptime Monitoring:**
- [Tool name, e.g., UptimeRobot, Pingdom]
- [Alert contact: email/phone]

**Where to find logs:**
- [e.g., Hosting provider dashboard, /var/log/app]

**What to look for in logs:**
- [e.g., Error messages, 500 status codes]

### Backups

**Backup Schedule:** [e.g., Daily automatic backups via hosting provider]

**Where backups are stored:** [e.g., S3 bucket, hosting provider's backup system]

**How long backups are kept:** [e.g., 30 days]

**How to restore from backup:** [Basic steps or link to provider docs]

**Last tested restore:** [Date - or "Never tested" if applicable]

---

## Configuration & Files

**Where application files are stored:** [e.g., /var/www/app, GitHub repository]

**Configuration file location:** [e.g., .env file, config/app.yaml]

**Important settings:** [e.g., API keys, database URL, email settings]

**Environment variables:** [Where they're set - e.g., hosting dashboard, .env file]

---

## External Services & Integrations

### Connected Services
- [e.g., Stripe for payments]
- [e.g., SendGrid for email]
- [e.g., Twilio for SMS]

### API Keys & Credentials
- **Where they're stored:** [e.g., In hosting dashboard environment variables, 1Password]
- **How to rotate them:** [Brief steps or link to docs]

### Integrations
- [List any systems this app integrates with]
- [How data flows between them]

---

## Vendor & Support Contacts

### Hosting Provider
- **Provider:** [e.g., DigitalOcean]
- **Support:** [How to contact them - e.g., support ticket, phone number]
- **Account login:** [Where login is stored]

### Domain Registrar
- **Registrar:** [e.g., Namecheap, Google Domains]
- **Renewal date:** [When domain expires]
- **Account login:** [Where login is stored]

### Other Service Providers
- **Service:** [e.g., Email provider]
- **Contact:** [Support info]

### Developer/Consultant
- **Name:** [If you have a developer or agency that maintains this]
- **Contact:** [Email, phone]
- **What they handle:** [e.g., New features, bug fixes]

---

## Documentation & Resources

**Application Documentation:** [Link to any user guides or internal docs]

**Technical Documentation:** [Link to developer docs, API docs]

**Important Links:**
- [GitHub repository, if applicable]
- [Project management tool]
- [Support ticket system]

---

## Change History

| Date | What Changed | Who Changed It |
|------|--------------|----------------|
| [YYYY-MM-DD] | [Description] | [Name] |
| [YYYY-MM-DD] | [Description] | [Name] |

---

## Additional Notes

[Any other important information about this application]

---

**Last Updated:** [Date]
**Template Version:** 1.0 (Small Business Edition)
**Maintained By:** [Your name/team]
