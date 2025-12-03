# FACT SHEET

> The instruction manual standard that solves fragmented information.

## The Problem with Documentation

When you need to understand or troubleshoot an application, the information you need is **scattered everywhere**: wikis, email threads, Slack messages, configuration files, someone's head, tribal knowledge, separate documentation systems.

**You waste precious time hunting** for answers across multiple sources, especially during incidents when every second counts. You're never sure if you found everything, or if there's a critical detail buried in some other system. You end up asking three different people to piece together information that should be in one place.

This **fragmentation problem** means responders can't act quickly, new team members take forever to get up to speed, and everyone wastes time context-switching between systems just to find basic information.

## The FACT SHEET Solution

FACT SHEET solves the fragmentation problem with a single insight: **put everything about an application in one place.** It's literally one file with every answer.

A FACT SHEET is:

- **Single file**: One Markdown file per application that consolidates ALL your application knowledge—no more jumping between systems
- **Structured enough for AI**: Organized sections that AI assistants can parse and reason over effectively
- **Simple enough for humans**: Plain Markdown that anyone can edit in any text editor, no special tools required
- **Living documentation**: Lives in the repo alongside the code, making it the natural place to record information as you work

Because it's just a Markdown file in your repository, it becomes your **single source of truth**. No context switching, no separate systems to log into, no hunting across multiple places. Everything you need is in one spot.

## How to Use FACT SHEET

1. **Fork** this repository or copy the template to your own project
2. **Copy** `app-knowledge-base-template.md` to your application repository
3. **Fill In** the template with your application's details (see `example-filled-factsheet.md` for reference)
4. **Feed** the FACT SHEET to your AI chat assistant when you need help
5. **Prompt** the AI: "Using this FACT SHEET, help me troubleshoot why the application won't start" or "Based on this FACT SHEET, generate a deployment checklist"

## What Makes a Good FACT SHEET

- Keep information **factual and current**—dates, versions, IP addresses, contact names
- Update it **when you make changes**, not as a separate task later
- Include **operational details** that help during incidents: log locations, restart commands, common issues
- Focus on **what responders need to know**: how to check if it's running, how to restart it, who to contact

## Choosing the Right Template

FACT SHEET comes in multiple variations designed for different organizational sizes. Choose the one that best matches your needs:

### Enterprise Template (`app-knowledge-base-template-enterprise.md`)
**Best for: Medium to large companies (50+ employees)**

The most comprehensive template with sections for:
- SLA tracking and compliance requirements
- Disaster recovery and business continuity
- On-call rotations and escalation paths
- Complex networking (load balancers, CDN, multiple environments)
- Change management and audit trails
- Security controls and compliance documentation

Use this if you have dedicated IT teams, complex infrastructure, multiple environments, and formal operational processes.

### Small Business Template (`app-knowledge-base-template-small-business.md`)
**Best for: Small to mid-size companies (10-50 employees)**

A streamlined template focused on practical operations:
- Simplified hosting and access information
- Essential troubleshooting procedures
- Basic backup and deployment processes
- Vendor and support contacts

Use this if you're running on managed cloud services, have a smaller team, and need straightforward documentation without enterprise overhead.

### Micro Business Template (`business-factsheet-template-micro.md`)
**Best for: Solopreneurs and very small businesses (1-10 employees)**

A single unified document covering ALL your business systems:
- Websites and applications
- SaaS tools and services
- Domain, email, and payment processing
- Vendor contacts and renewal tracking
- Emergency procedures

Use this if you're a one-person operation or small team managing multiple tools and services. Instead of creating separate fact sheets for each system, this template lets you document everything in one place.

### Template Flexibility

**You're not locked into any specific template.** These variations exist to save you time by providing a starting point that matches your complexity level. You can:

- Start with the enterprise template and remove sections you don't need
- Use the small business template and add enterprise sections as you grow
- Customize any template to match your specific requirements
- Mix and match sections from different templates

The goal is to help you create documentation faster, not to force you into a specific structure.

## Benefits

- **Reduced MTTR**: During incidents, responders have immediate access to ALL critical information in one place
- **Stop hunting**: No more searching across wikis, Slack, email, and tribal knowledge to find answers
- **Better AI assistance**: AI can provide context-aware help using your specific infrastructure details from a single source
- **Knowledge preservation**: New team members find everything they need in one document instead of asking around
- **Version controlled**: Track changes over time, see what changed and when

## What's Included

### Templates
- `app-knowledge-base-template.md` - The original standard template
- `app-knowledge-base-template-enterprise.md` - Comprehensive template for larger organizations
- `app-knowledge-base-template-small-business.md` - Streamlined template for small businesses
- `business-factsheet-template-micro.md` - Unified business fact sheet for micro-businesses

### Examples
- `example-filled-factsheet.md` - A complete example showing how a filled FACT SHEET looks

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on how to suggest improvements to the template.

## License

This project is released under the MIT License. See [LICENSE](LICENSE) for details.

---
