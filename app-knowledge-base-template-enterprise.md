<!-- AI CONTEXT
This is a FACT SHEET for an IT system. When responding:
- Use only this document. If the answer isn't here, say so. Do not consult external sources or supplement with general knowledge.
- Lead with a clear, jargon-light answer. Follow with technical details only if needed to complete the task.
- Match the user's language. If they ask in plain terms, respond in plain terms. If they use technical terminology, you can mirror it.
- For support issues, prioritize the Support Procedures section.
- Assume the reader is competent but may be outside their specialty. Clarity trumps precision.
-->
# Application Knowledge Base - Enterprise Edition

## Application Overview

**Application Name:** [Enter application name]

**Description:** [Brief description of what this application does]

**Business Purpose:** [Why this application exists and what business function it serves]

**Environment:** [Production / Staging / Development / QA]

**Criticality Level:** [Critical / High / Medium / Low]

**Owner/Team:** [Team or individual responsible]

**Primary Contact:** [Name, email, phone]

**Secondary Contact:** [Name, email, phone]

**Business Unit:** [Which business unit owns this application]

**Cost Center:** [Cost center or budget code]

---

## Service Level Agreements (SLA)

**Availability Target:** [e.g., 99.9% uptime]

**Maximum Downtime Per Month:** [e.g., 43 minutes]

**Response Time SLA:** [e.g., 95% of requests under 2 seconds]

**Support Response Times:**
- **Critical (P1):** [e.g., 15 minutes]
- **High (P2):** [e.g., 1 hour]
- **Medium (P3):** [e.g., 4 hours]
- **Low (P4):** [e.g., 24 hours]

**Planned Maintenance Windows:** [e.g., Second Saturday monthly, 2-6 AM EST]

---

## Technical Information

### Technology Stack
- **Language/Framework:** [e.g., Java Spring Boot, Python Django, .NET Core]
- **Runtime Version:** [e.g., Java 17, Python 3.11, .NET 8]
- **Web Server:** [e.g., Tomcat, Nginx, IIS]
- **Application Server:** [if applicable]
- **Container Runtime:** [e.g., Docker, containerd]
- **Orchestration:** [e.g., Kubernetes, Docker Swarm, ECS]

### Version Information
- **Current Version:** [e.g., v2.3.1]
- **Last Updated:** [Date]
- **Release Schedule:** [e.g., Monthly, Quarterly, As needed]
- **Next Planned Release:** [Date and version]

### Dependencies
- **External APIs:** [List any external services this app depends on]
- **Internal Services:** [List internal dependencies]
- **Third-Party Libraries:** [Key libraries or packages]
- **Upstream Dependencies:** [Services this app depends on]
- **Downstream Consumers:** [Services that depend on this app]

---

## Networking Information

### IP Addresses
- **Public IP:** [e.g., 203.0.113.10]
- **Private IP:** [e.g., 10.0.1.50]
- **Additional IPs:** [List any additional IPs]
- **VIP (Virtual IP):** [if applicable]
- **Floating IP:** [if applicable]

### Ports & Protocols
- **HTTP:** [e.g., Port 80]
- **HTTPS:** [e.g., Port 443]
- **Application Ports:** [e.g., 8080, 8443, custom ports]
- **Database Port:** [e.g., 5432, 3306, 1433]
- **Management Ports:** [e.g., JMX, admin interfaces]
- **Other Ports:** [List any other relevant ports]

### Load Balancer Information
- **Load Balancer Type:** [e.g., AWS ALB, F5, HAProxy, Nginx]
- **LB IP/Hostname:** [e.g., lb-prod-app.example.com / 203.0.113.5]
- **LB Algorithm:** [e.g., Round Robin, Least Connections]
- **Health Check URL:** [e.g., /health or /api/status]
- **Health Check Interval:** [e.g., Every 30 seconds]
- **Health Check Timeout:** [e.g., 5 seconds]
- **Healthy Threshold:** [e.g., 2 consecutive successes]
- **Unhealthy Threshold:** [e.g., 3 consecutive failures]
- **Backend Servers:** [List IPs/hostnames of servers behind LB]
- **Session Persistence:** [Yes/No - method if yes]
- **SSL Termination:** [At LB / End-to-end encryption]

### DNS & Hostnames
- **Primary Hostname:** [e.g., app.company.com]
- **Alternative Hostnames:** [e.g., www.app.company.com]
- **Internal Hostname:** [e.g., app.internal.company.com]
- **CDN Hostname:** [if applicable]
- **DNS Provider:** [e.g., Route53, Cloudflare, internal]
- **TTL Settings:** [DNS record TTL values]

### Firewall Rules
- **Inbound Rules:** [Describe allowed inbound traffic]
- **Outbound Rules:** [Describe required outbound access]
- **Allowed Source IPs:** [List IP ranges or specific IPs that can access this app]
- **Network Segmentation:** [VLAN or subnet information]
- **DMZ Configuration:** [if applicable]

### CDN & Edge Configuration
- **CDN Provider:** [e.g., CloudFront, Akamai, Cloudflare]
- **Cache Strategy:** [Cache rules and TTL]
- **Edge Locations:** [Geographic distribution]
- **Origin Shield:** [if configured]

---

## Infrastructure Details

### Server Information
| Server Name | Role | OS | CPU | RAM | Disk | Environment | Location |
|-------------|------|-----|-----|-----|------|-------------|----------|
| [hostname1] | [App Server] | [Ubuntu 22.04] | [4 cores] | [16GB] | [100GB] | [Prod] | [us-east-1a] |
| [hostname2] | [DB Server] | [Ubuntu 22.04] | [8 cores] | [32GB] | [500GB] | [Prod] | [us-east-1b] |

### Scaling Information
- **Auto-scaling Enabled:** [Yes/No]
- **Min Instances:** [e.g., 2]
- **Max Instances:** [e.g., 10]
- **Scaling Triggers:** [e.g., CPU > 70%, Request count > 1000/min]
- **Scale-up Cooldown:** [e.g., 5 minutes]
- **Scale-down Cooldown:** [e.g., 10 minutes]

### Database Information
- **Database Type:** [e.g., PostgreSQL, MySQL, SQL Server, MongoDB]
- **Database Version:** [e.g., PostgreSQL 15.3]
- **Database Server:** [hostname/IP]
- **Database Name:** [database name]
- **Connection String Format:** [e.g., jdbc:postgresql://dbserver:5432/appdb]
- **Connection Pool Size:** [if applicable]
- **Read Replicas:** [List read replica endpoints]
- **Failover Configuration:** [Primary/standby setup]
- **Replication Lag Tolerance:** [e.g., < 5 seconds]

### Storage Locations
- **Application Files:** [e.g., /opt/app or C:\inetpub\app]
- **Log Files:** [e.g., /var/log/app or C:\logs\app]
- **Configuration Files:** [e.g., /etc/app/config.yaml]
- **Data/Upload Directory:** [if applicable]
- **Temporary Files:** [if applicable]
- **Shared Storage:** [e.g., NFS mount points, EFS]

### Backup Information
- **Backup Schedule:** [e.g., Daily at 2 AM]
- **Backup Location:** [e.g., S3 bucket, network share]
- **Retention Policy:** [e.g., 30 days]
- **Backup Type:** [Full / Incremental / Differential]
- **Recovery Time Objective (RTO):** [e.g., 4 hours]
- **Recovery Point Objective (RPO):** [e.g., 24 hours]
- **Backup Validation:** [How backups are tested]
- **Last Successful Restore Test:** [Date]

---

## Disaster Recovery & Business Continuity

### DR Strategy
- **DR Site Location:** [Geographic location of DR site]
- **DR Configuration:** [Hot standby / Warm standby / Cold standby]
- **Failover Method:** [Manual / Automatic]
- **Failover Time:** [Expected time to failover]

### Recovery Procedures
- **DR Runbook Location:** [Link to detailed DR procedures]
- **Failover Trigger Criteria:** [When to initiate DR]
- **Failback Procedures:** [How to return to primary site]
- **Last DR Test Date:** [Date of last DR drill]
- **Next Scheduled DR Test:** [Date]

### Data Replication
- **Replication Method:** [Async / Sync / Semi-sync]
- **Replication Lag Monitoring:** [How lag is monitored]
- **Geographic Distribution:** [Data center locations]

---

## Access & Authentication

### Application Access
- **Public URL:** [e.g., https://app.company.com]
- **Internal URL:** [e.g., https://app.internal.company.com]
- **Admin Portal:** [if separate]
- **VPN Required:** [Yes/No - details if yes]

### Authentication Methods
- **Authentication Type:** [e.g., LDAP, Active Directory, OAuth, SAML, Local]
- **SSO Provider:** [if applicable]
- **MFA Enabled:** [Yes/No]
- **Service Accounts:** [List service accounts used]
- **Certificate-based Auth:** [if applicable]
- **API Key Management:** [How API keys are issued and rotated]

### Access Levels
- **Admin Access:** [Who has admin rights]
- **User Access:** [How users get access]
- **API Access:** [How to get API credentials]
- **Privileged Access Management:** [PAM solution if used]

### Credentials & Secrets
- **Credential Storage:** [e.g., AWS Secrets Manager, Azure Key Vault, HashiCorp Vault]
- **Required Credentials:** [List types of credentials needed - avoid storing actual passwords]
- **Secret Rotation Schedule:** [How often secrets are rotated]
- **Break-glass Procedures:** [Emergency access procedures]

---

## Compliance & Security

### Compliance Requirements
- **Regulatory Frameworks:** [e.g., SOC 2, PCI-DSS, HIPAA, GDPR]
- **Data Classification:** [e.g., Public, Internal, Confidential, Restricted]
- **Compliance Audit Schedule:** [When audits occur]
- **Last Audit Date:** [Date]
- **Compliance Contacts:** [Who manages compliance]

### Security Controls
- **Encryption at Rest:** [Yes/No - method]
- **Encryption in Transit:** [TLS version and cipher suites]
- **Web Application Firewall:** [WAF provider and rules]
- **DDoS Protection:** [Protection mechanisms]
- **Intrusion Detection/Prevention:** [IDS/IPS details]
- **Vulnerability Scanning:** [Tool and frequency]
- **Penetration Testing:** [Frequency and last test date]

### Data Handling
- **PII/PHI Data:** [Yes/No - what types]
- **Data Retention Policy:** [How long data is kept]
- **Data Deletion Procedures:** [How data is purged]
- **Geographic Restrictions:** [Data residency requirements]
- **GDPR/Privacy Controls:** [Data subject rights procedures]

### Security Contacts
- **Security Team Contact:** [Name, email]
- **Incident Response Team:** [Contact information]
- **Security Champion:** [Team member responsible for security]

---

## End-User Support Scenarios

### Common Issues & Resolutions

#### Issue 1: [e.g., Login Failures]
- **Symptoms:** [What users report]
- **Cause:** [Common causes]
- **Resolution Steps:**
  1. [Step 1]
  2. [Step 2]
  3. [Step 3]
- **Escalation:** [When to escalate and to whom]

#### Issue 2: [e.g., Performance Slowness]
- **Symptoms:** [What users report]
- **Cause:** [Common causes]
- **Resolution Steps:**
  1. [Step 1]
  2. [Step 2]
  3. [Step 3]
- **Escalation:** [When to escalate and to whom]

#### Issue 3: [Add more as needed]
- **Symptoms:**
- **Cause:**
- **Resolution Steps:**
- **Escalation:**

### Troubleshooting Steps
1. **Check Application Status:** [How to verify if app is running]
2. **Check Logs:** [Where to look and what to look for]
3. **Check Database Connectivity:** [How to verify DB connection]
4. **Check Network Connectivity:** [How to verify network]
5. **Check Resource Usage:** [CPU, memory, disk checks]
6. **Check Dependencies:** [Verify upstream services are healthy]

### Known Limitations
- [List any known limitations or bugs]
- [Workarounds if available]

### Frequently Asked Questions
**Q:** [Question]
**A:** [Answer]

**Q:** [Question]
**A:** [Answer]

---

## Maintenance & Operations

### On-Call & Escalation

#### On-Call Rotation
- **On-Call Schedule:** [Link to PagerDuty/OpsGenie schedule]
- **Primary On-Call:** [Current person or rotation]
- **Secondary On-Call:** [Backup person]
- **Escalation Path:** [L1 → L2 → L3 → Manager]

#### Escalation Contacts
| Level | Name | Role | Contact Method | Response Time |
|-------|------|------|----------------|---------------|
| L1 | [Name] | [Role] | [Phone/Email] | [15 min] |
| L2 | [Name] | [Role] | [Phone/Email] | [30 min] |
| L3 | [Name] | [Role] | [Phone/Email] | [1 hour] |

### Restart Procedures

#### Application Restart
```bash
# Commands to restart the application
# Example:
# sudo systemctl restart app-service
```

**Impact:** [e.g., 2-3 minute downtime]
**When to Restart:** [Scenarios requiring restart]
**Approval Required:** [Yes/No - from whom]

#### Database Restart
```bash
# Commands to restart database if needed
```

**Impact:** [Expected downtime]
**When to Restart:** [Scenarios requiring restart]
**Approval Required:** [Yes - requires manager approval]

### Deployment Process

#### Change Management
- **Change Control Board:** [Yes/No - meeting schedule]
- **Change Approval Required For:** [Production, All environments]
- **Standard Change Window:** [e.g., Tuesday/Thursday 9 PM - 11 PM]
- **Emergency Change Process:** [How to get emergency approval]

#### Deployment Steps
1. **Pre-Deployment:**
   - [Checklist items]
   - [Stakeholder notifications]
   - [Change ticket approval]

2. **Deployment Steps:**
   - [Step-by-step deployment instructions]
   - [Validation at each stage]

3. **Post-Deployment:**
   - [Verification steps]
   - [Smoke tests]
   - [Performance validation]
   - [Stakeholder notification]

**Deployment Window:** [e.g., Tuesday/Thursday 9 PM - 11 PM]
**Rollback Procedure:** [How to rollback if deployment fails]
**Rollback Time:** [Expected time to rollback]

### Monitoring & Alerts

#### Monitoring Tools
- **APM Tool:** [e.g., New Relic, DataDog, AppDynamics]
- **Log Aggregation:** [e.g., Splunk, ELK, CloudWatch]
- **Uptime Monitoring:** [e.g., Pingdom, UptimeRobot]
- **Infrastructure Monitoring:** [e.g., Prometheus, Nagios, Zabbix]
- **Synthetic Monitoring:** [e.g., Synthetic transactions]
- **Real User Monitoring:** [RUM tool if used]

#### Key Metrics to Monitor
- [e.g., Response time < 2s]
- [e.g., Error rate < 1%]
- [e.g., CPU usage < 80%]
- [e.g., Memory usage < 85%]
- [e.g., Disk I/O < threshold]
- [e.g., Database connection pool usage]
- [e.g., Queue depth < threshold]

#### Alert Contacts
- **Critical Alerts:** [Contact method and people]
- **Warning Alerts:** [Contact method and people]
- **Info Alerts:** [Contact method and people]

#### Alert Escalation Policy
- **Initial Alert:** [Who gets notified first]
- **Escalation After:** [Time before escalating]
- **Final Escalation:** [Ultimate escalation point]

#### Log Locations
- **Application Logs:** [Path or URL]
- **Access Logs:** [Path or URL]
- **Error Logs:** [Path or URL]
- **Audit Logs:** [Path or URL]
- **Security Logs:** [Path or URL]
- **Log Retention:** [How long logs are kept]

### Scheduled Maintenance
- **Patch Schedule:** [e.g., First Saturday of month]
- **Maintenance Window:** [Time and day]
- **Notification Process:** [How users are notified]
- **Notification Lead Time:** [e.g., 5 business days]

### Capacity Planning
- **Current Capacity:** [e.g., 10,000 concurrent users]
- **Peak Usage:** [Historical peak]
- **Capacity Threshold:** [When to add resources]
- **Growth Projections:** [Expected growth rate]
- **Next Capacity Review:** [Date]

---

## Documentation & Resources

### Internal Documentation
- **Architecture Diagram:** [Link or location]
- **Network Diagram:** [Link or location]
- **Data Flow Diagram:** [Link or location]
- **Runbook:** [Link or location]
- **Standard Operating Procedures:** [Link or location]
- **Disaster Recovery Plan:** [Link or location]
- **Security Documentation:** [Link or location]
- **Compliance Documentation:** [Link or location]

### External Documentation
- **Vendor Documentation:** [Links]
- **API Documentation:** [Links]
- **User Guides:** [Links]
- **Training Materials:** [Links]

### Related Systems
- [List systems this app integrates with]
- [Dependencies and relationships]
- [Integration architecture]

### Ticket System
- **Issue Tracker:** [e.g., Jira, ServiceNow]
- **Project/Component:** [Project key or component name]
- **Recent Issues:** [Link to recent tickets]
- **Major Incident History:** [Link to P1/P2 incident log]

### Knowledge Base
- **Internal Wiki:** [Link to team wiki]
- **Troubleshooting Guides:** [Links]
- **Best Practices:** [Links]

### Change History
| Date | Change Description | Changed By | Ticket/CR # |
|------|-------------------|------------|-------------|
| [YYYY-MM-DD] | [Description] | [Name] | [CHG0001] |
| [YYYY-MM-DD] | [Description] | [Name] | [CHG0002] |

---

## Additional Notes

[Any additional information that doesn't fit in the above categories]

---

**Last Updated:** [Date]
**Template Version:** 1.0 (Enterprise Edition)
**Maintained By:** [Your name/team]
