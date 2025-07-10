# How we use GitHub

Range42 issues and code are managed on [GitHub](https://github.com/range42).
This page focuses on aspects of GitHub usage that are specific to Range42.
This workflow evolves based on what we learn while using GitHub and feedback from our community.
For general GitHub usage information, see the [GitHub user documentation](https://docs.github.com/en/github).

## Get started

To create your GitHub account, visit the [registration page](https://github.com/join) in a web browser.
Then you will be able to open new issues, create pull requests, and fork your copy of our repositories.

## Organization

:todo: Adapt to real-world

All of our repositories are available under the [Range42 GitHub organization](https://github.com/range42).
The main Git repository and most issues live in the [Range42/core repository](https://github.com/range42/core).

We use git to maintain all code for the Range42 Project. We have divided the project into several components, each with its own separate repository. For example:

- `core.git` – The core Range42 platform and orchestration engine
- `scenario-library.git` – Cybersecurity training scenarios and exercises
- `infrastructure.git` – Infrastructure as Code templates and automation
- `assessment-engine.git` – Automated assessment and scoring system
- `docs.git` – Documentation, guides, and educational materials
- `ui.git` – Web-based user interface and dashboard

Range42 code is divided into multiple git repositories for the following reasons:

- **Clear boundaries**: Creates natural boundaries between different components, enforcing proper interfaces and enabling independent development without conflicts
- **Easier onboarding**: Smaller repositories make it easier for new developers to understand specific components and contribute patches
- **Licensing flexibility**: Different repositories can have different licenses based on their purpose and content
- **Deployment independence**: Components can be deployed and scaled independently
- **Team ownership**: Different teams can own and maintain specific components

### Git branches organization

Range42 uses several branch types:

- **Main branch**: The default branch `main` contains the latest stable code ready for production deployment
- **Development branch**: `develop` branch for integration of new features before they're ready for main
- **Feature branches**: Named `feature/description` for implementing new functionality
- **Bugfix branches**: Named `fix/description` for addressing specific bugs
- **Release branches**: Named `release/x.y.z` for preparing new releases
- **Hotfix branches**: Named `hotfix/description` for urgent production fixes

When Range42 developers make a code change that resolves an issue, the GitHub issue will typically be closed from the relevant commit message.
The main Range42 core branch, `main`, is considered stable and ready for production deployment.
Features are developed in separate branches and merged into `main` after thorough testing and review.

## How we use GitHub metadata

On GitHub, issues and pull requests have metadata.
Being consistent in the use of GitHub metadata makes collective work smoother.

### Title and description

The title should be a short but clear description of what this is about. For scenarios and infrastructure changes, include the component name in the title.

### Status and resolution

:todo: Add labels

Open issues may have a status label, starting with `S:`. Each label has a description of what it represents.
See the [list of status labels](https://github.com/range42/core/labels?q=S%3A+), along with their descriptions.

Closed issues may have up to one resolution label, starting with `R:`. See the [list of resolution labels](https://github.com/range42/core/labels?q=R%3A+) and their descriptions. When an issue doesn't fit into Range42's mission, we reject it by creating a comment explaining why it's being rejected, closing the issue, and adding the `R: wontfix` label. When an issue is closed as a duplicate, we create a comment that mentions the other issue and add the `R: duplicate` label.

The main advantage of using these labels is to organize and visualize issues on project boards.
Using these labels accurately improves the team's workflow.

### Assignee

We use the Assignee field to help organize our work as a team, focus on current priorities, and avoid individual over-commitment.
Most tasks should be available for anyone who has spare capacity and the required skills.
In general, issues and pull requests should not be assigned to anyone.

We do assign them if at least one of these conditions is met:

- Someone is actively working on it
- The task is important and urgent
- The milestone is set to the next Range42 release
- Only one person can complete the task (helps identify bottlenecks)
- Security-related issues requiring specific expertise

### Milestone

[Milestones](https://github.com/range42/core/milestones) represent commitments that Range42 contributors and users can rely on.
They help prioritize work and communicate release timelines to the community.

### Type of work

To indicate the type of work needed to complete the next step on an issue, we use labels that start with `T:`.
See the [list of 'type of work' labels](https://github.com/range42/core/labels?q=t%3A) and their descriptions:

- `T: scenario` – Cybersecurity scenario development
- `T: infrastructure` – Infrastructure and deployment work
- `T: assessment` – Assessment engine and scoring
- `T: documentation` – Documentation updates
- `T: security` – Security-related changes
- `T: ui` – User interface improvements

### Component labels

We use component labels starting with `C:` to categorize issues by Range42 component:

- `C: core` – Core platform functionality
- `C: scenarios` – Training scenarios and exercises
- `C: infrastructure` – Deployment and infrastructure
- `C: assessment` – Assessment and scoring system
- `C: ui` – User interface and dashboard

### Other labels

See our [full list of labels](https://github.com/range42/core/labels) for other categorized labels we use.

## Relationships between issues

GitHub has limitations when expressing semantic relationships between issues. Here's how we overcome them:

- **Parent/subtask**: Issues with the `T: epic` label indicate parent issues with subtasks. Child issues mention the parent issue in comments
- **Related issues**: Related issues are listed in descriptions or comments, creating automatic cross-references
- **Scenario dependencies**: Use comments to link related scenarios or infrastructure requirements

## How to document progress

### Create and update issues

For details about labels, see [metadata](#how-we-use-github-metadata). If you plan to work on an issue, leave a comment expressing interest or ask to be assigned to avoid duplicate work.

Keep all knowledge useful to others on the issue, or at least linked from there.
When committing changes that resolve an issue, include `#NNNN` in the commit message, where NNNN is the issue number. GitHub will automatically reference this commit on the corresponding issue. For example:

```
feat: [core] Add network isolation scenario (#1234)
fix: [doc] Resolve container startup timing issue (#5678)
chg: [doc] Update deployment guide (#9012)
```

Use conventional commit prefixes:
- `feat:` for new features
- `fix:` for bug fixes  
- `docs:` for documentation
- `refactor:` for code refactoring
- `test:` for adding tests
- `chore:` for maintenance tasks

You can also add additional information after the commit prefix, e.g. [doc] [lic] [i8n] but this is not mandatory.

### Report progress or failure

It's important to:
- Keep the team informed about your commitment to assigned issues and expected timelines
- Avoid individual over-commitment and feelings of failure

If you don't think you can work on an issue soon, make this clear on the issue or de-assign yourself.

### Propose changes

We use Pull Requests (PRs) to propose, review, and merge changes.
You can comment on issues and pull requests.
[Our code of conduct](https://github.com/range42/.github/blob/main/CODE_OF_CONDUCT.md) applies.

To submit your work:
- Fork us on GitHub
- Push your work to a dedicated git topic branch
- Create a pull request (PR) when ready for review
- In the PR description, summarize what problem this PR solves and reference related issues: "Closes #xxx, #yyyy"

Follow these conventions when submitting changes to any Range42 repository:
- Submit one pull request per fix/feature/change
- Keep the number of commits per PR small
- Ensure your PR is mergeable into the target branch
- Make sure CI/CD checks pass
- For scenario changes, include testing documentation
- For infrastructure changes, test in multiple environments
- Any major functionality should be feature-flagged by default

### Request input from someone else

If you need input on an issue or pull request, ask your question in a comment, mentioning them with their GitHub username: `@username`. To raise attention of a team, mention the corresponding team: `@Range42/security-team`.

GitHub will send email notifications about mentions.

### Act upon input requests

Provide requested information quickly to make the Range42 contribution process efficient and enjoyable.

When input is requested from you on an issue or pull request:
- GitHub may send you an email notification
- Ensure your GitHub notification settings allow you to receive these messages
- If you cannot provide input immediately, track this task using personal organization tools or create a new issue assigned to yourself

## Automatic integration and testing

Range42 uses comprehensive CI/CD pipelines for code quality and security:

### Security scanning
- **CodeQL**: Static analysis for security vulnerabilities
- **Container scanning**: Security scans for all container images
- **Dependency checking**: Automated vulnerability scanning of dependencies

### Testing
- **Unit tests**: Component-level testing

When you submit a PR, consider the results of all checks. Ensure your code builds without errors and passes all security scans.

If CI/CD checks fail, review the output carefully. Not all failures are necessarily caused by your changes, but it's important to understand the results.

### Scenario testing

For scenario contributions, additional validation includes:
- **Educational effectiveness**: Scenarios must meet learning objectives
- **Technical accuracy**: Attack vectors and defenses must be realistic
- **Resource requirements**: Must specify accurate system requirements

## Access control

If you need to do something in GitHub and lack the needed permissions, ask the Range42 team to grant appropriate access.
For example, you'll need "Triage" access to add labels or assign issues.

### Permission levels
- **Read**: View code and issues
- **Triage**: Manage issues and pull requests
- **Write**: Push to repositories and manage some settings
- **Maintain**: Manage repository settings and teams
- **Admin**: Full repository administration

See [GitHub's access permissions documentation](https://docs.github.com/en/github/getting-started-with-github/access-permissions-on-github) for details.

## Security considerations

Given Range42's focus on cybersecurity training:
- Never commit real credentials or sensitive data
- Use placeholder data for examples
- Sanitize any logs or debugging information
- Follow secure coding practices
- Report security issues through our [Security Policy](SECURITY.md)

## Documentation requirements

All contributions should include appropriate documentation:
- **Code changes**: Update inline comments and API documentation
- **New features**: Update user guides and tutorials
- **Scenarios**: Include instructor guides and learning objectives
- **Infrastructure**: Update deployment and configuration guides
