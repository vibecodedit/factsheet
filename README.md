# FACT SHEET

**The standard instruction manual for the software powering your business.**

FACT SHEET is a lightweight, AI-friendly documentation system for IT professionals who manage multiple applications and systems. Instead of scattered documentation across wikis, tickets, and tribal knowledge, FACT SHEET provides a single Markdown template that captures everything you need to know about an application—from IP addresses and deployment procedures to common support scenarios and troubleshooting steps.

## Why FACT SHEET?

- **Single Source of Truth**: All critical application information in one clean Markdown file
- **AI-Ready**: Feed your completed FACT SHEET to any AI chat application for instant, context-aware assistance
- **Simple**: No complex tooling, databases, or dependencies—just Markdown
- **Comprehensive**: Covers technical details, networking, operations, and end-user support scenarios
- **Portable**: Easy to version control, share, and maintain

## What's Inside the Template?

Each FACT SHEET template includes sections for:

- **Application Overview**: Name, purpose, ownership, criticality level
- **Technical Information**: Stack, versions, dependencies
- **Networking Information**: IPs, ports, load balancers, DNS, firewall rules
- **Infrastructure Details**: Servers, databases, storage, backups
- **Access & Authentication**: URLs, auth methods, credentials management
- **End-User Support Scenarios**: Common issues with step-by-step resolutions
- **Maintenance & Operations**: Restart procedures, deployment, monitoring
- **Documentation & Resources**: Links, diagrams, runbooks

## How to Use FACT SHEET

### Step 1: Fork the Repository
Fork this repository to your own GitHub account or organization.

```bash
# Or clone it directly
git clone https://github.com/yourusername/factsheet.git
cd factsheet
```

### Step 2: Copy the Template
Copy `app-knowledge-base-template.md` for each application you manage.

```bash
# Example: Create a knowledge base for your payment API
cp app-knowledge-base-template.md payment-api-factsheet.md
```

### Step 3: Fill In the Template
Open your new file and fill in all relevant sections with your application's information. See `example-customer-portal.md` for a complete example.

**Tips for filling out your FACT SHEET:**
- Be specific with IP addresses, ports, and hostnames
- Include actual commands and procedures (not just "restart the app")
- Document common issues you've actually encountered
- Add links to monitoring dashboards, wikis, and runbooks
- Keep it updated when changes occur

### Step 4: Feed to AI Chat
When you need help with your application, feed the entire FACT SHEET to your preferred AI chat application (Claude, ChatGPT, etc.) to give it full context about your system.

**Example prompt:**
```
I'm providing you with the complete knowledge base for my Customer Portal application.
Please read this entire document to understand the system.

[Paste your FACT SHEET here]

Now that you understand the system, help me troubleshoot why customers are reporting
slow page loads during peak hours.
```

### Step 5: Prompt for Assistance
Ask your AI assistant specific questions about:
- Troubleshooting issues
- Understanding error messages
- Planning maintenance procedures
- Generating runbook steps
- Explaining system architecture to team members
- Creating incident response plans

The AI will have full context about your application and can provide targeted, relevant assistance.

## Example

See [`example-customer-portal.md`](example-customer-portal.md) for a fully completed FACT SHEET example.

## Best Practices

- **One file per application**: Keep each application's knowledge base separate
- **Version control**: Commit your FACT SHEETs to git to track changes over time
- **Regular updates**: Update your FACT SHEET whenever infrastructure or procedures change
- **Team collaboration**: Have team members review and contribute to accuracy
- **Incident learnings**: Add new troubleshooting scenarios after resolving incidents
- **Test with AI**: Periodically test your FACT SHEET with AI to ensure it provides useful context

## Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on:
- Suggesting template improvements
- Adding new sections
- Reporting issues
- Submitting pull requests

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Who Is This For?

FACT SHEET is ideal for:
- System administrators managing multiple applications
- DevOps engineers documenting infrastructure
- IT support teams needing quick reference materials
- Platform engineers building internal documentation
- Anyone who wants AI-assisted help with their systems

## Get Started

1. [Download the template](app-knowledge-base-template.md)
2. [See a complete example](example-customer-portal.md)
3. Start documenting your applications
4. Use AI to supercharge your system knowledge

---

**Questions or feedback?** Open an issue or submit a pull request. We'd love to hear how you're using FACT SHEET!
