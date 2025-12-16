# Application Knowledge Base

## Application Overview

**Application Name:** Acme CRM

**Description:** Web-based client relationship management system that helps the company maintain healthy relationships with clients, colleagues, and company alumni.  

**Business Purpose:** Maintains all contact and relationship details for company contacts, manages relationship strenth scores, and helps maintain relevant marketing email lists.  

**Environment:** Production

**Criticality Level:** App is critical for normal business operations

**Owner/Team:** Application Engineering Team

**Primary Contact:** AppEngineeringTeam@company.com

---

## Technical Information

### Version Information
- **Current Version:** v3.8.12
- **Last Updated:** 20251208

### Dependencies
- **External APIs:**
  - Stripe Payment API (v2023-10-16)
  - ShipStation API for shipping labels
  - SendGrid for email notifications
- **Internal Services:**
  - ShopHub Auth Service (SSO)
  - Inventory Service API
  - Customer Data Platform
- **Third-Party Libraries:**
  - Django REST Framework 3.14
  - Celery 5.3 for async tasks
  - Redis 7.2 for caching and queue

---

## Networking Information

### IP Addresses
- **Public IP:** 203.0.113.45
- **Private IP:** 10.20.5.11 (dc1-crm-app-1), 10.20.5.12 (app-server-2)
- **Additional IPs:** 10.20.5.100 (Celery worker server)

### Ports & Protocols
- **HTTP:** Port 80 (redirects to HTTPS)
- **HTTPS:** Port 443
- **Application Ports:** 8000 (Gunicorn)
- **Database Port:** 5432 (PostgreSQL)
- **Other Ports:** 6379 (Redis), 5672 (RabbitMQ for Celery)

### Load Balancer Information
- **Load Balancer Type:** F5
- **LB IP/Hostname:** orders-prod-alb-1234567890.us-east-1.elb.amazonaws.com / 203.0.113.45
- **LB Algorithm:** Round Robin with sticky sessions
- **Health Check URL:** /api/health
- **Health Check Interval:** Every 30 seconds, timeout 5s, 2 consecutive failures marks unhealthy
- **Backend Servers:** app-server-1 (10.20.5.11), app-server-2 (10.20.5.12)

### DNS & Hostnames
- **Hostname:** crm.company.com

### Firewall Rules
- **Inbound Rules:**
  - Port 443 from internet (0.0.0.0/0)
- **Outbound Rules:**
  - HTTPS (443) to external APIs (Stripe, ShipStation, SendGrid)
  - PostgreSQL (5432) to RDS instance
  - Redis (6379) to ElastiCache cluster
  - HTTP/HTTPS to internal services on 10.20.0.0/16
- **Allowed Source IPs:** ThirdPartyVendorIntegration (198.51.100.0/24)

---

## Infrastructure Details

### Production Server Information
- **Web Server:** DC1-CRM-WEB-1.company.com
- **Application Server:** DC1-CRM-APP-1.company.com

### Develpoment Server Information
- **Web Server:** DC1-CRM-WEBDEV-1.company.com
- **Application Server:** DC1-CRM-APPDEV-1.company.com

### Database Information
- **Database Type:** SQL Server  
- **Database Version:** n/a
- **Database Server:** appsDB.company.com
- **Database Name:** CRMDB

### Storage Locations
- **Application Files:** /opt/shophub/orders
- **Log Files:** /var/log/shophub/orders
- **Configuration Files:** /etc/shophub/orders/settings.py
- **Data/Upload Directory:** /opt/shophub/orders/media (invoices, packing slips)
- **Temporary Files:** /tmp/shophub-orders

### Backup Information
- **Backup Schedule:**
  - Database: Automated RDS snapshots daily at 3:00 AM EST
  - Application files: Daily at 2:00 AM EST
- **Backup Location:**
  - RDS automated backups retained in AWS
  - Application backups to S3: s3://shophub-backups/orders-app/
- **Retention Policy:**
  - Database: 30 days automated snapshots, 1 year for monthly snapshots
  - Application files: 30 days
- **Backup Type:** Full daily snapshots for database, incremental for application files
- **Recovery Time Objective (RTO):** 2 hours
- **Recovery Point Objective (RPO):** 24 hours (last night's backup)

---

## Access & Authentication

### Application Access
- **Internal URL:** https://crm.company.com
- **Admin Portal:** https://crm.company.com/admin

### Authentication Methods
- **Authentication Type:** SSO
- **MFA Enabled:** No
- **Service Accounts:**
  - crm_service (for service integrations and background tasks)

### Access Levels
- **Admin Access:** Platform Engineering team (5 people), managed via Active Directory group "shophub-orders-admins"
- **User Access:** Warehouse staff and customer service team (automatic access via SSO, no approval needed)
- **API Access:** API keys managed through Auth Service, request via Jira ticket to Platform Engineering

### Credentials & Secrets
- **Credential Storage:** AWS Secrets Manager
- **Required Credentials:**
  - Database password: secret/production/orders/db_password
  - Redis password: secret/production/orders/redis_password
  - Stripe API key: secret/production/orders/stripe_api_key
  - SendGrid API key: secret/production/orders/sendgrid_api_key

---

## End-User Support Scenarios

### Common Issues & Resolutions

#### Issue 1: Order stuck in "Processing" status
- **Symptoms:** Users report order has been "Processing" for more than 2 hours, inventory was deducted but no picking list generated
- **Cause:** Usually Celery worker backlog or failed connection to Inventory Service
- **Resolution Steps:**
  1. Check Celery worker status: `sudo systemctl status celery-worker`
  2. Check queue length: `redis-cli -h 10.20.5.200 llen celery` (should be < 100)
  3. Check recent errors in Celery logs: `tail -100 /var/log/shophub/celery.log | grep ERROR`
  4. If worker is down, restart: `sudo systemctl restart celery-worker`
  5. If queue is backed up (>500), alert Platform Engineering immediately
- **Escalation:** If restart doesn't resolve within 15 minutes, page Platform Engineering on-call

#### Issue 2: Cannot access admin portal
- **Symptoms:** Admin users getting "403 Forbidden" or "Authentication Failed"
- **Cause:** Usually SSO service issue or VPN not connected for internal access
- **Resolution Steps:**
  1. Verify user is on VPN: Check if they can access orders.internal.shophub.net
  2. Check SSO service status: https://status.shophub.net
  3. Verify user is in "shophub-orders-admins" AD group (ask them to log out and back in)
  4. Check application logs for auth errors: `grep "auth failed" /var/log/shophub/orders/app.log | tail -20`
  5. If SSO is down, follow SSO incident runbook
- **Escalation:** If SSO is up but specific user can't access after 10 minutes, escalate to Identity team

#### Issue 3: Slow order processing / Page load times > 5 seconds
- **Symptoms:** Users report application is slow, orders taking long time to load
- **Cause:** Database connection pool exhaustion, high query load, or cache issues
- **Resolution Steps:**
  1. Check application response time in New Relic dashboard
  2. Check database CPU: Log into RDS console, verify CPU < 80%
  3. Check Redis cache hit rate: Should be > 85%, check in New Relic
  4. Check number of database connections: Should be < 80 total across both app servers
  5. If cache hit rate is low, restart application to reset cache: `sudo systemctl restart orders-app` on both servers (one at a time)
- **Escalation:** If performance doesn't improve after cache reset, page Database team for query optimization

### Troubleshooting Steps
1. **Check Application Status:**
   - SSH to app-server-1: `ssh deploy@app-server-1.internal.shophub.net`
   - Check service: `sudo systemctl status orders-app`
   - Expected: "active (running)" with recent log lines showing request processing

2. **Check Logs:**
   - Application logs: `/var/log/shophub/orders/app.log`
   - Nginx access logs: `/var/log/nginx/orders_access.log`
   - Nginx error logs: `/var/log/nginx/orders_error.log`
   - Look for: 500 errors, connection timeouts, database errors

3. **Check Database Connectivity:**
   - From app server: `psql -h orders-db-prod.abc123.us-east-1.rds.amazonaws.com -U orders_app -d orders_production -c "SELECT 1;"`
   - Should return: "1" immediately (< 100ms)

4. **Check Network Connectivity:**
   - To database: `nc -zv orders-db-prod.abc123.us-east-1.rds.amazonaws.com 5432`
   - To Redis: `nc -zv 10.20.5.200 6379`
   - To Inventory Service: `curl -I https://inventory.internal.shophub.net/health`

5. **Check Resource Usage:**
   - CPU: `top` (should be < 80% average)
   - Memory: `free -h` (should have > 2GB free)
   - Disk: `df -h` (/ should be < 80% used)

### Known Limitations
- Cannot process more than 5000 orders per hour due to ShipStation API rate limits (workaround: orders queue automatically during high volume)
- Order search only indexes last 90 days by default (older orders require "Search Archive" button)
- Bulk order import limited to 1000 orders per CSV file

### Frequently Asked Questions
**Q:** How do I manually retry a failed order?
**A:** In admin portal, find order by ID, click "Retry Processing" button. If button is grayed out, order may need status reset - contact Platform Engineering.

**Q:** Where can I download reports of today's orders?
**A:** Reports > Daily Orders > Select date > Export CSV. Reports are generated at 1 AM daily for previous day.

**Q:** Can I cancel an order that's already in "Shipped" status?
**A:** No, the application prevents this. You must process a return/refund through customer service tools after delivery.

---

## Maintenance & Operations

### Restart Procedures

#### Application Restart
```bash
# On each application server (do one at a time to avoid downtime)
ssh deploy@app-server-1.internal.shophub.net
sudo systemctl restart orders-app
# Wait 30 seconds and verify health
curl http://localhost:8000/api/health
# If healthy, proceed to app-server-2
```

**Impact:** Zero downtime if done one server at a time with 30-60 second delay between servers
**When to Restart:**
- After configuration changes
- After code deployment
- When cache needs clearing (to reset Redis connections)
- When memory usage exceeds 90%

#### Celery Worker Restart
```bash
ssh deploy@celery-worker-1.internal.shophub.net
sudo systemctl restart celery-worker
# Check status
sudo systemctl status celery-worker
# Check it's processing jobs
tail -f /var/log/shophub/celery.log
```

**Impact:** Background job processing paused during restart (30-60 seconds), jobs will queue and process once worker is back
**When to Restart:**
- When Celery worker shows as dead/stuck
- After deploying code changes that affect background tasks
- When worker memory usage exceeds 90%

#### Database Restart
RDS database is managed by AWS - do not restart without approval from Database team and Platform Engineering lead.

**Impact:** 5-10 minute application outage
**When to Restart:** Only during approved maintenance windows or critical incidents

### Deployment Process
1. **Pre-Deployment:**
   - Verify Jira ticket approval from product team
   - Announce in #engineering-alerts Slack channel 30 minutes before
   - Verify automated test suite passed in CI/CD pipeline
   - Check that deployment window is approved (Tuesday/Thursday 9-11 PM)

2. **Deployment Steps:**
   - CI/CD automatically deploys via GitHub Actions when tag is pushed
   - Manual process if CI/CD fails:
     ```bash
     # From deployment server
     cd /opt/shophub/deployment
     ./deploy.sh orders-app v3.8.2
     ```
   - Deployment script automatically:
     - Pulls latest code to staging directory
     - Runs database migrations
     - Updates app-server-1, waits 2 minutes, then updates app-server-2
     - Restarts Celery workers
     - Runs smoke tests

3. **Post-Deployment:**
   - Verify health checks passing: Check ALB target health in AWS Console
   - Run smoke tests: `./smoke-test.sh production`
   - Check New Relic for error rate (should be < 1%)
   - Process 1 test order manually through full workflow
   - Monitor for 30 minutes before closing deployment ticket

**Deployment Window:** Tuesday/Thursday 9 PM - 11 PM EST
**Rollback Procedure:**
```bash
# If deployment fails or critical bugs found
./rollback.sh orders-app v3.8.1  # Previous version
# Script automatically rolls back code and database migrations
```

### Monitoring & Alerts

#### Monitoring Tools
- **APM Tool:** New Relic (account: shophub-prod)
- **Log Aggregation:** Splunk (search: index=production app=orders)
- **Uptime Monitoring:** Pingdom, StatusCake (checks /api/health every 60 seconds)

#### Key Metrics to Monitor
- Response time P95 < 800ms
- Error rate < 0.5%
- Order processing success rate > 99%
- Celery queue length < 100 jobs
- CPU usage < 80%
- Memory usage < 85%
- Database connection pool < 80% utilized

#### Alert Contacts
- **Critical Alerts:** PagerDuty to Platform Engineering on-call rotation
- **Warning Alerts:** #platform-alerts Slack channel

#### Log Locations
- **Application Logs:** /var/log/shophub/orders/app.log (also in Splunk)
- **Access Logs:** /var/log/nginx/orders_access.log
- **Error Logs:** /var/log/nginx/orders_error.log
- **Celery Logs:** /var/log/shophub/celery.log
- **Audit Logs:** Stored in database, accessible via admin portal under "Audit Trail"

### Scheduled Maintenance
- **Patch Schedule:** Second Saturday of each month, 6 AM - 10 AM EST
- **Maintenance Window:** OS security patches, dependency updates
- **Notification Process:**
  - 7 days before: Email to stakeholders
  - 48 hours before: Banner on application
  - 24 hours before: Reminder email and Slack announcement

---

## Documentation & Resources

### Internal Documentation
- **Architecture Diagram:** Confluence: https://wiki.shophub.example/display/ENG/Orders+Architecture
- **Network Diagram:** https://wiki.shophub.example/display/ENG/Network+Topology
- **Data Flow Diagram:** https://wiki.shophub.example/display/ENG/Orders+Data+Flow
- **Runbook:** This document (also stored in GitHub repo README)
- **Standard Operating Procedures:** https://wiki.shophub.example/display/OPS/Orders+SOPs

### External Documentation
- **Django Documentation:** https://docs.djangoproject.com/en/4.2/
- **Stripe API Documentation:** https://stripe.com/docs/api
- **ShipStation API:** https://www.shipstation.com/docs/api/
- **AWS RDS PostgreSQL:** https://docs.aws.amazon.com/rds/

### Related Systems
- ShopHub Storefront (sends orders to this system via API)
- Inventory Service (receives allocation requests)
- Warehouse Management System (receives picking lists)
- Customer Service Portal (queries order status)
- Analytics Pipeline (receives order events for reporting)

### Ticket System
- **Issue Tracker:** Jira
- **Project/Component:** ORDERS project, components: Backend, Workers, Database
- **Recent Issues:** https://jira.shophub.example/projects/ORDERS/issues

### Change History
| Date | Change Description | Changed By |
|------|-------------------|------------|
| 2025-11-15 | Upgraded to Django 4.2 and Python 3.11 | Sarah Chen |
| 2025-10-28 | Added second application server for redundancy | Marcus Rodriguez |
| 2025-09-12 | Migrated database from EC2 to RDS | Sarah Chen |
| 2025-08-05 | Implemented Redis caching layer | Marcus Rodriguez |

---

## Additional Notes

- This application is integrated with the company's disaster recovery plan. In case of full region failure, RDS has cross-region read replica in us-west-2 that can be promoted.
- Performance degrades significantly during Black Friday / Cyber Monday. Additional Celery workers are spun up automatically via Auto Scaling Group during these periods.
- The application has a feature flag system using LaunchDarkly - if new features cause issues, they can be disabled without deployment.

---

**Last Updated:** 2025-11-30
**Template Version:** 1.0
**Maintained By:** Platform Engineering Team (Sarah Chen, Marcus Rodriguez)
