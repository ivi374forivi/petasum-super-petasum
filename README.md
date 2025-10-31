# petasum-super-petasum

A template repository for organization-wide GitHub issue tracking infrastructure.

## Overview

This repository provides ready-to-use templates and workflows for managing organization-wide issues, initiatives, incidents, and RFCs across multiple repositories within a GitHub organization.

## Guiding Principles

This repository follows a set of [Organization Commandments](COMMANDMENTS.md) inspired by best practices from leading open-source projects including Semgrep, TensorFlow, and Schema.org. These principles emphasize:
- Free & open source collaboration
- Privacy & security first
- Beginner-friendly, human-readable documentation
- Quality over quantity
- Transparency and inclusivity
- Interoperability and stability

See [COMMANDMENTS.md](COMMANDMENTS.md) for the complete set of principles that guide our approach.

## What's Included

### Issue Templates

- **Org-wide Initiative** (`.github/ISSUE_TEMPLATE/org-wide-initiative.yml`) - For tracking cross-repo, cross-team initiatives
- **Org-wide Incident** (`.github/ISSUE_TEMPLATE/org-incident.yml`) - For tracking multi-repo or multi-team incidents
- **RFC (org-wide)** (`.github/ISSUE_TEMPLATE/org-rfc.yml`) - For proposing cross-repo changes for review

### Configuration

- **Issue Template Config** (`.github/ISSUE_TEMPLATE/config.yml`) - Configures issue template chooser with contact links

### Discussion Templates

- **Org Proposal** (`.github/DISCUSSION_TEMPLATE/org-proposal.yml`) - For early-stage proposals and RFCs

### Workflows

- **Auto-add to Project** (`.github/workflows/add-to-org-project.yml`) - Automatically adds issues labeled `org-wide` to an organization Project

## Usage

### For Organizations

1. **Option 1: Use as a centralized org-issues repository**
   - Fork or template this repository as `your-org/org-issues`
   - Configure the workflow to point to your organization Project
   - Add the required labels: `org-wide`, `initiative`, `epic`, `rfc`, `incident`, `sev-1`, `sev-2`, `sev-3`, `dependency`, `blocked`, `needs-triage`

2. **Option 2: Use in an org-level .github repository**
   - Copy the `.github` directory contents to your `your-org/.github` repository
   - The templates will be available across all repositories in your organization
   - Note: Consider visibility implications (public vs private)

### Configuration Steps

1. **Update the workflow file** (`.github/workflows/add-to-org-project.yml`):
   - Replace `https://github.com/orgs/your-org/projects/1` with your actual Project URL
   - Create a fine-grained PAT with access to the organization Project
   - Add it as a secret named `ORG_PROJECT_TOKEN`

2. **Update contact links** (`.github/ISSUE_TEMPLATE/config.yml`):
   - Replace `your-org` with your actual organization name
   - Update URLs to match your organization's resources

3. **Create labels** in your repository:
   - org-wide, initiative, epic, rfc, incident
   - sev-1, sev-2, sev-3
   - dependency, blocked, needs-triage
   - ready, in-progress, done, wontfix

## Best Practices

- **Centralized Repository**: Create a dedicated repository (e.g., `org-issues`) for organization-wide issues
- **Standardize Labels**: Use consistent labels across repositories
- **Organization Projects**: Track org-wide issues in an organization-level Project (Projects v2)
- **Cross-linking**: Reference issues across repos using `owner/repo#123` syntax
- **Triage SLAs**: Establish clear ownership and response times
- **Discussions for RFCs**: Use GitHub Discussions for early proposals, convert to issues when ready
- **Automation**: Use GitHub Actions to automate labeling, project assignment, and notifications

## Architecture Recommendations

### Recommended Setup

```
your-org/
├── .github/              # Shared templates, policies (can be public)
│   ├── ISSUE_TEMPLATE/
│   ├── CONTRIBUTING.md
│   ├── SECURITY.md
│   └── workflow-templates/
└── org-issues/           # Central org-wide issue tracking (private recommended)
    ├── .github/
    │   ├── ISSUE_TEMPLATE/  (these templates)
    │   └── workflows/       (automation workflows)
    └── docs/
```

### Visibility Considerations

- **Public .github repo**: Use for shared templates across public repositories
  - Issues here will be public
  - Not suitable for sensitive incidents or internal planning
  
- **Private org-issues repo**: Use for internal organization tracking
  - Issues remain private to organization members
  - Better for incidents, internal initiatives, and confidential planning

## Reference

This repository implements the patterns and templates described in the `copilot-chat-response-transcript` file, which provides comprehensive guidance on organization-wide GitHub issue management.

For guiding principles and commandments that inform these templates, see [COMMANDMENTS.md](COMMANDMENTS.md).

## License

This template is provided as-is for use by any GitHub organization.
