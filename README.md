# FACT SHEET

> The single, portable, clean Markdown file that solves documentation rot.

## The Problem with Documentation

Traditional documentation becomes a **separate chore** from the actual work required to maintain it. This disconnect inevitably leads to **documentation rot** where documentation falls out of sync with reality, becomes outdated, and eventually gets ignored.

When documentation lives in wikis, email threads, your team's heads, or separate systems, IT staff must remember to update it after making changes. This extra step is often forgotten during incidents, quick fixes, or busy periods. The result? Documentation that can't be trusted.

## The FACT SHEET Solution

FACT SHEET erases the documentation rot problem with a single insight: **make documentation so simple that IT staff maintain it without even noticing.** It's literally one file with every answer.

A FACT SHEET is:

- **Single file**: One Markdown file per application—portable, version-controlled, easy to find
- **Structured enough for AI**: Organized sections that AI assistants can parse and reason over effectively
- **Simple enough for humans**: Plain Markdown that anyone can edit in any text editor, no special tools required
- **Living documentation**: Lives in the repo alongside the code, gets updated naturally as part of normal work

Because it's just a Markdown file in your repository, updating your FACT SHEET becomes as natural as updating a README. No context switching, no separate systems to log into, no extra steps to remember.

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

## Benefits

- **Reduced MTTR**: During incidents, responders have immediate access to critical information
- **Better AI assistance**: AI can provide context-aware help using your specific infrastructure details
- **No documentation rot**: Updates happen naturally as part of normal work
- **Knowledge preservation**: New team members can quickly understand the application
- **Version controlled**: Track changes over time, see what changed and when

## What's Included

- `app-knowledge-base-template.md` - The blank template ready to fill out
- `example-filled-factsheet.md` - A complete example showing how a filled FACT SHEET looks

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on how to suggest improvements to the template.

## License

This project is released under the MIT License. See [LICENSE](LICENSE) for details.

---

**FACT SHEET**: Fact Sheet, the standard instruction manual for the software powering your business.
