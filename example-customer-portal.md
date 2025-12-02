# Application Knowledge Base

## Application Overview

**Application Name:** Customer Portal

**Description:** Self-service web portal allowing customers to view orders, track shipments, update account information, and submit support tickets.

**Business Purpose:** Reduces call center volume by 40% and provides 24/7 customer access to account information and order status.

**Environment:** Production

**Criticality Level:** High

**Owner/Team:** Digital Experience Team

**Primary Contact:** Sarah Johnson, sarah.johnson@company.com, ext. 5521

**Secondary Contact:** Mike Chen, mike.chen@company.com, ext. 5522

---

## Technical Information

### Technology Stack
- **Language/Framework:** Node.js with Express.js
- **Runtime Version:** Node.js 18.17.1
- **Web Server:** Nginx (reverse proxy)
- **Application Server:** PM2 process manager

### Version Information
- **Current Version:** v3.2.1
- **Last Updated:** 2025-11-15
- **Release Schedule:** Bi-weekly on Thursdays

### Dependencies
- **External APIs:** Shippo API (shipping tracking), Stripe API (payment processing)
- **Internal Services:** Order Management System API, Customer Database API, Email Service
- **Third-Party Libraries:** React 18.2.0, Express 4.18.2, PostgreSQL client, Redis client

---

## Networking Information

### IP Addresses
- **Public IP:** 203.0.113.45
- **Private IP:** 10.10.5.20
- **Additional IPs:** 10.10.5.21 (secondary app server)

### Ports & Protocols
- **HTTP:** Port 80 (redirects to HTTPS)
- **HTTPS:** Port 443
- **Application Ports:** 3000 (internal, behind nginx)
- **Database Port:** 5432
- **Redis Port:** 6379

### Load Balancer Information
- **Load Balancer Type:** AWS Application Load Balancer (ALB)
- **LB IP/Hostname:** customer-portal-lb-1234567890.us-east-1.elb.amazonaws.com
- **LB Algorithm:** Least Outstanding Requests
- **Health Check URL:** /api/health
- **Health Check Interval:** Every 30 seconds
- **Backend Servers:** 10.10.5.20:3000, 10.10.5.21:3000

### DNS & Hostnames
- **Primary Hostname:** portal.company.com
- **Alternative Hostnames:** customerportal.company.com
- **Internal Hostname:** portal.internal.company.local

### Firewall Rules
- **Inbound Rules:** HTTPS (443) from anywhere, SSH (22) from jump server only
- **Outbound Rules:** HTTPS (443) to external APIs, PostgreSQL (5432) to database server, Redis (6379) to cache server
- **Allowed Source IPs:** Public access on 443, internal network 10.10.0.0/16 for management

---

## Infrastructure Details

### Server Information
| Server Name | Role | OS | CPU | RAM | Disk |
|-------------|------|-----|-----|-----|------|
| portal-app-01 | App Server | Ubuntu 22.04 LTS | 4 cores | 16GB | 100GB |
| portal-app-02 | App Server | Ubuntu 22.04 LTS | 4 cores | 16GB | 100GB |
| portal-db-01 | DB Server | Ubuntu 22.04 LTS | 8 cores | 32GB | 500GB SSD |
| portal-cache-01 | Redis Cache | Ubuntu 22.04 LTS | 2 cores | 8GB | 50GB |

### Database Information
- **Database Type:** PostgreSQL
- **Database Version:** PostgreSQL 15.3
- **Database Server:** portal-db-01.internal.company.local (10.10.5.10)
- **Database Name:** customer_portal_prod
- **Connection String Format:** postgresql://portal_user:PASSWORD@10.10.5.10:5432/customer_portal_prod
- **Connection Pool Size:** 20 connections per app server

### Storage Locations
- **Application Files:** /var/www/customer-portal
- **Log Files:** /var/log/customer-portal
- **Configuration Files:** /etc/customer-portal/config.json
- **Data/Upload Directory:** /var/www/customer-portal/uploads (user profile pictures)
- **Temporary Files:** /tmp/customer-portal

### Backup Information
- **Backup Schedule:** Database: Daily at 2 AM ET; Application: Weekly on Sundays
- **Backup Location:** AWS S3 bucket s3://company-backups/customer-portal/
- **Retention Policy:** Daily backups: 30 days, Weekly backups: 90 days
- **Backup Type:** Database: Full daily backup with WAL archiving; Application: Incremental
- **Recovery Time Objective (RTO):** 4 hours
- **Recovery Point Objective (RPO):** 24 hours (daily backups)

---

## Access & Authentication

### Application Access
- **Public URL:** https://portal.company.com
- **Internal URL:** https://portal.internal.company.local
- **Admin Portal:** https://portal.company.com/admin
- **VPN Required:** No for public portal; Yes for admin portal and SSH access

### Authentication Methods
- **Authentication Type:** OAuth 2.0 with email/password
- **SSO Provider:** Auth0
- **MFA Enabled:** Yes (optional for customers, required for admin users)
- **Service Accounts:** portal_api_user (for internal API calls), portal_backup_user (for backups)

### Access Levels
- **Admin Access:** Digital Experience Team members via Auth0 admin role
- **User Access:** Self-registration available; email verification required
- **API Access:** API keys issued through admin portal; contact Digital Experience Team

### Credentials & Secrets
- **Credential Storage:** AWS Secrets Manager
- **Required Credentials:** Database password, Redis password, Auth0 client secret, Stripe API key, Shippo API key

---

## End-User Support Scenarios

### Common Issues & Resolutions

#### Issue 1: Cannot Login / Forgot Password
- **Symptoms:** User reports "Invalid credentials" or cannot remember password
- **Cause:** Incorrect password, account locked after failed attempts, or email not verified
- **Resolution Steps:**
  1. Verify user email is correct and account exists in Auth0
  2. Check if account is locked (Auth0 logs show "account locked" event)
  3. Send password reset email via "Forgot Password" link
  4. If email not verified, resend verification email from Auth0 dashboard
  5. Unlock account in Auth0 if locked due to failed attempts
- **Escalation:** If password reset email not received after 10 minutes, escalate to Digital Experience Team

#### Issue 2: Order Status Not Updating
- **Symptoms:** Customer sees old order status or "Loading..." indefinitely
- **Cause:** Shippo API timeout, cache not invalidated, or Order Management System delayed sync
- **Resolution Steps:**
  1. Check Shippo API status at status.goshippo.com
  2. Clear Redis cache for specific order: `redis-cli DEL order:{order_id}`
  3. Verify Order Management System API is responding: `curl https://oms.internal.company.local/api/health`
  4. Check application logs for API timeout errors: `grep "Shippo timeout" /var/log/customer-portal/app.log`
  5. Ask customer to hard refresh browser (Ctrl+Shift+R or Cmd+Shift+R)
- **Escalation:** If Shippo API is down >15 minutes, notify Digital Experience Team and create P2 incident

#### Issue 3: Payment Method Won't Update
- **Symptoms:** Error message when trying to update credit card, or changes don't save
- **Cause:** Stripe API issue, expired Stripe API key, or PCI compliance validation failure
- **Resolution Steps:**
  1. Check Stripe dashboard for failed payment method updates
  2. Verify Stripe API key is valid in AWS Secrets Manager
  3. Check application logs: `tail -f /var/log/customer-portal/payment.log`
  4. Ensure customer is using supported card types (Visa, MC, Amex, Discover)
  5. Try test card update in staging environment to isolate issue
- **Escalation:** All payment issues should be escalated to Digital Experience Team immediately (P1)

### Troubleshooting Steps
1. **Check Application Status:** `systemctl status customer-portal` or check PM2: `pm2 status`
2. **Check Logs:** `tail -f /var/log/customer-portal/app.log` and check CloudWatch Logs
3. **Check Database Connectivity:** `pg_isready -h 10.10.5.10 -p 5432`
4. **Check Network Connectivity:** `curl https://portal.company.com/api/health`
5. **Check Resource Usage:** `top`, `df -h`, `free -h`

### Known Limitations
- Profile picture uploads limited to 5MB (workaround: ask users to resize images)
- Order history only shows last 12 months (older orders available through customer service)
- Safari 14 and older has session timeout issues (workaround: upgrade to Safari 15+)

### Frequently Asked Questions
**Q:** How do customers reset their passwords?
**A:** Click "Forgot Password" on login page, enter email, and follow link in email (valid for 1 hour).

**Q:** Why do some customers see a blank page after login?
**A:** Usually a browser cache issue. Ask them to clear cache or try incognito/private mode.

**Q:** How long does it take for order updates to appear?
**A:** Order updates sync every 15 minutes. Manual refresh available via "Refresh Status" button.

---

## Maintenance & Operations

### Restart Procedures

#### Application Restart
```bash
# Restart all app instances via PM2
pm2 restart customer-portal

# Or restart systemd service
sudo systemctl restart customer-portal

# Graceful reload without downtime
pm2 reload customer-portal
```

**Impact:** Standard restart: 10-15 seconds downtime per server; Graceful reload: Zero downtime
**When to Restart:** After config changes, memory leaks (RSS >4GB), or deployment

#### Database Restart
```bash
# On portal-db-01 server
sudo systemctl restart postgresql
```

**Impact:** 30-60 seconds downtime; all app connections will reconnect automatically
**When to Restart:** After PostgreSQL config changes, rarely needed otherwise

### Deployment Process
1. **Pre-Deployment:**
   - Notify #customer-portal Slack channel 30 minutes before
   - Verify all tests pass in CI/CD pipeline
   - Backup database: `pg_dump customer_portal_prod > backup_$(date +%F).sql`
   - Tag release in GitHub

2. **Deployment Steps:**
   - Deploy to portal-app-01 first: `./deploy.sh portal-app-01`
   - Monitor health checks and error logs for 5 minutes
   - If healthy, deploy to portal-app-02: `./deploy.sh portal-app-02`
   - Run smoke tests: `npm run smoke-test:prod`

3. **Post-Deployment:**
   - Verify login flow works
   - Check order status page loads
   - Verify payment method updates work
   - Monitor error rates in DataDog for 30 minutes
   - Post completion message in #customer-portal Slack

**Deployment Window:** Thursday 8 PM - 10 PM ET (low traffic period)
**Rollback Procedure:** `./rollback.sh <previous-version>` - takes 3 minutes per server

### Monitoring & Alerts

#### Monitoring Tools
- **APM Tool:** DataDog APM
- **Log Aggregation:** AWS CloudWatch Logs
- **Uptime Monitoring:** Pingdom (checks every 1 minute from 5 locations)

#### Key Metrics to Monitor
- Response time < 500ms (p95)
- Error rate < 0.5%
- CPU usage < 70%
- Memory usage < 80%
- Database connections < 80% of pool

#### Alert Contacts
- **Critical Alerts:** PagerDuty → On-call engineer (24/7)
- **Warning Alerts:** #customer-portal-alerts Slack channel

#### Log Locations
- **Application Logs:** /var/log/customer-portal/app.log and CloudWatch: /aws/customer-portal/app
- **Access Logs:** /var/log/nginx/customer-portal-access.log
- **Error Logs:** /var/log/customer-portal/error.log and CloudWatch: /aws/customer-portal/errors
- **Audit Logs:** CloudWatch: /aws/customer-portal/audit (login attempts, admin actions)

### Scheduled Maintenance
- **Patch Schedule:** Second Saturday of each month, 2 AM - 5 AM ET
- **Maintenance Window:** Saturday 2 AM - 5 AM ET
- **Notification Process:** Email sent to all customers 7 days in advance; banner on portal 48 hours before

---

## Documentation & Resources

### Internal Documentation
- **Architecture Diagram:** https://wiki.company.com/customer-portal/architecture
- **Network Diagram:** https://wiki.company.com/customer-portal/network-topology
- **Data Flow Diagram:** https://wiki.company.com/customer-portal/data-flows
- **Runbook:** https://wiki.company.com/customer-portal/runbook
- **Standard Operating Procedures:** https://wiki.company.com/customer-portal/sops

### External Documentation
- **Auth0 Documentation:** https://auth0.com/docs
- **Stripe API Documentation:** https://stripe.com/docs/api
- **Shippo API Documentation:** https://goshippo.com/docs/
- **PostgreSQL 15 Documentation:** https://www.postgresql.org/docs/15/

### Related Systems
- Order Management System (OMS) - provides order data and status updates
- Customer Database - central customer information and preferences
- Email Service - transactional emails (order confirmations, password resets)
- Analytics Platform - customer behavior tracking

### Ticket System
- **Issue Tracker:** Jira
- **Project/Component:** PORTAL project, "Customer Portal" component
- **Recent Issues:** https://jira.company.com/projects/PORTAL/issues

### Change History
| Date | Change Description | Changed By |
|------|-------------------|------------|
| 2025-11-15 | Upgraded to Node.js 18.17.1 and React 18.2.0 | Mike Chen |
| 2025-10-22 | Added Shippo integration for real-time tracking | Sarah Johnson |
| 2025-09-30 | Implemented Redis caching for order queries | David Park |
| 2025-09-01 | Migrated from Auth0 Universal Login to embedded login | Sarah Johnson |

---

## Additional Notes

- Black Friday/Cyber Monday: Increase auto-scaling limits to handle 5x normal traffic
- Known issue: Safari 14 users may experience session timeouts after 10 minutes of inactivity (Apple browser bug, no workaround)
- Future enhancement: Mobile app planned for Q2 2026
- Compliance: PCI-DSS Level 1 compliant (annual audit in Q1)

---

**Last Updated:** 2025-12-02
**Template Version:** 1.0
**Maintained By:** Digital Experience Team
