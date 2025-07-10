# Contributing to the Range42 Project

The Range42 project is an open-source initiative focused on creating realistic, scalable cybersecurity training environments. Our project is composed of multiple sub-projects contributed by cybersecurity professionals, educators, researchers, and enthusiasts who actively use and improve the Range42 platform. The Range42 project fully supports the [Contributor Covenant Code of Conduct](CODE_OF_CONDUCT.md) to foster an inclusive and collaborative environment for learning and advancing cybersecurity education.

The [Range42 roadmap](ROADMAP.md) is driven by the needs of our user communities including cybersecurity training organizations, educational institutions, corporate security teams, government agencies, and individual practitioners seeking hands-on cybersecurity experience.

Participating in the Range42 project is accessible to everyone, regardless of their experience level. Get familiar with [how we use GitHub at Range42 Project](GITWORKFLOW.md), then read on for details on how you can contribute:

## Reporting bugs, suggesting features

The most common way to contribute to the Range42 project is to report bugs, issues, or suggest new features and scenarios.

:todo: Adapt with real-world repos
Each project component ([Range42 core](https://github.com/Range42/core/issues), [scenario-library](https://github.com/Range42/scenario-library/issues), [infrastructure](https://github.com/Range42/infrastructure/issues), [assessment-engine](https://github.com/Range42/assessment-engine/issues), [documentation](https://github.com/Range42/docs/issues) or any other projects within the [Range42 organization](https://github.com/Range42/)) has its own issue management system. Don't forget that you can cross-reference issues between sub-projects.

### Issue tracker guidelines
- **Use the provided issue template.** When reporting an issue on GitHub, please use one of the [issue templates](https://github.com/Range42/core/issues/new/choose). Do not delete or remove parts of it. The issue template is designed to gather essential information about your environment, the scenario being used, and steps to reproduce the issue.
- **New issues should include all relevant information.** Add comprehensive details including:
  - Range42 version and deployment method
  - Operating system and virtualization platform
  - Scenario/exercise being run
  - Expected vs actual behavior
  - Screenshots or logs where applicable
  - Network configuration details (if relevant)
  - Performance metrics (if performance-related)
- **Security policy.** To disclose a security issue confidentially, please see the [Reporting Security Vulnerabilities](#reporting-security-vulnerabilities) section.
- **Avoid duplicate issues.** Search both open and closed issues before creating a new one. If you find a similar issue, comment on the existing one rather than creating a duplicate. This helps us track interest and priority.
- **No guarantees on implementation.** Creating an issue is a way to submit items for consideration. The Range42 team will prioritize based on project roadmap, community needs, and available resources.

### Following up afterward

When developers resolve your issue, the GitHub issue will typically be closed from the relevant commit message. We maintain a main stable branch with regular updates and feature branches for development.

If you test a fix and find it doesn't resolve your issue, please comment on the original issue explaining the situation. We'll receive a notification and respond accordingly.

Issues may be closed with specific resolutions like `R: invalid`, `R: duplicate`, or `R: wontfix`. Each label has a description explaining the decision.

## Reporting security vulnerabilities

:todo: Check what those link to, SECURITY.md ?
View our [Security Policy](https://github.com/Range42/core/security/policy).

Given the nature of cybersecurity training environments, we take security reports seriously and have established procedures for responsible disclosure.

## Contributing to Range42 core

Before you get started, read our [coding guidelines](CODINGSTYLE.md).

If you want to contribute to the [Range42 core](https://github.com/Range42/core) project:

- First fork the [Range42 core project](https://github.com/Range42/core)
- Branch off from `main` (main branch is the primary development branch) `git checkout main`
- Create a branch for your contribution `git checkout -b feature/new-scenario-engine`
- Work on your fix or feature (focus only on that feature, avoid debug code or unrelated changes)
- Commit your changes with meaningful commit messages following our [Commit Message Best Practices](https://github.com/Range42/core/wiki/CommitMessageBestPractices). Use prefixes like `feat:` for new features, `fix:` for bug fixes, `docs:` for documentation, or `refactor:` for code improvements.
- Push and [open a pull request](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) via GitHub.

For changes to scenarios, assessments, or infrastructure components, see the [Scenario Development CheckList](https://github.com/Range42/core/wiki/Scenario-Development-CheckList).

### Recommendations for quick PR merges:
- Small, incremental changes are preferred over large, complex ones
- Include tests for new functionality
- Update documentation when adding new features
- Ensure scenarios are tested in multiple environments
- Follow security best practices for training content

## Contributing to scenario libraries

Range42 scenarios are defined in structured formats (JSON/YAML) that describe:
- Network topologies
- Vulnerable services and applications
- Attack vectors and defensive measures
- Learning objectives and assessment criteria
- Resource requirements

### Scenario development process:
1. **Design phase**: Create a scenario specification document outlining learning objectives, target audience, and technical requirements
2. **Implementation**: Develop the scenario configuration files, supporting scripts, and documentation
3. **Testing**: Validate the scenario in isolated environments across different platforms
4. **Documentation**: Create instructor guides, student materials, and technical documentation
5. **Validation**: Run automated tests using our CI/CD pipeline

All scenarios undergo JSON/YAML validation and security scanning before integration.

## Contributing new attack scenarios

If you want to contribute realistic attack scenarios:

1. **Research and design**: Base scenarios on real-world attack patterns, TTPs (Tactics, Techniques, and Procedures), and current threat intelligence
2. **Create scenario files**: Develop configuration files following our [Scenario Schema](https://github.com/Range42/scenario-library/blob/main/schema/)
3. **Develop supporting materials**: Include network diagrams, VM configurations, and assessment rubrics
4. **Educational content**: Create learning objectives, prerequisites, and expected outcomes
5. **Testing**: Validate across different skill levels and environments
6. **Documentation**: Provide clear setup instructions and troubleshooting guides

For more information, see "[Developing Effective Range42 Scenarios](https://cyberrange-project.org/docs/scenario-development)" in our documentation.

## Contributing to infrastructure automation

Range42 infrastructure automation includes:
- Container orchestration configurations
- Virtual machine templates and provisioning scripts
- Network simulation and configuration
- Monitoring and logging systems
- Auto-scaling and resource management

To contribute:
1. Fork the [infrastructure repository](https://github.com/Range42/infrastructure)
2. Create or modify Infrastructure as Code (IaC) templates
3. Test deployments in multiple cloud environments
4. Validate security configurations and network isolation
5. Update documentation and deployment guides
6. Submit pull request with comprehensive testing results

## Building compatible tools and extending Range42

Range42 uses open standards and APIs for:
- Scenario definition and exchange
- Assessment and scoring
- User management and progress tracking
- Infrastructure provisioning
- Reporting and analytics

We encourage developers to build compatible tools and integrations. See our [API documentation](https://docs.cyberrange-project.org/api/) and [integration guides](https://docs.cyberrange-project.org/integrations/).

## Writing documentation

We welcome improvements to our documentation, particularly:
- **User guides**: Setup, configuration, and usage instructions
- **Instructor materials**: Teaching guides, assessment rubrics, and best practices
- **Developer documentation**: API references, architecture guides, and contribution workflows
- **Scenario documentation**: Learning objectives, technical details, and troubleshooting

See our [documentation contribution guidelines](https://github.com/Range42/docs/blob/main/CONTRIBUTING.md).

## Automatic integration and testing

All Range42 repositories include CI/CD pipelines that:
- Validate code quality and security
- Test scenario deployment and functionality
- Check infrastructure provisioning
- Verify documentation builds
- Run security scans on container images

Contributions to our testing infrastructure are welcome, including:
- Unit and integration tests
- Security testing frameworks
- Performance benchmarking
- Cross-platform compatibility tests

## Testing new releases and updates

Testing new Range42 releases helps ensure stability and functionality across different environments. Testing should be done in isolated environments, never in production training systems.

Areas that benefit from testing:
- New scenario deployments
- Infrastructure scaling and performance
- User interface changes
- API functionality
- Integration with external tools

If you'd like to test Range42 without a full installation, use our [pre-built VM images](https://cyberrange-project.org/download/#virtual-images).

## Translating Range42

We accept translations through our localization platform: https://crowdin.com/project/cyberrange

Help make Range42 accessible in your language by translating:
- User interface elements
- Documentation and guides
- Scenario descriptions and instructions
- Error messages and help text

Note that only reviewed translations are included in releases.

## For native English speakers

Most Range42 developers are not native English speakers. We welcome corrections and improvements to our English documentation, user interfaces, and communications.

## Improving the Range42 experience

As a Range42 user, contribute to our UX efforts by:
- Completing the [Range42 User Experience Survey](https://cyberrange-project.org/ux-survey)
- Providing feedback on scenario difficulty and effectiveness
- Suggesting improvements to the user interface
- Contributing to [user personas](https://docs.cyberrange-project.org/personas/) and [user stories](https://docs.cyberrange-project.org/user-stories/)

For UX-related questions, contact us at <ux@cyberrange-project.org>

## Improving the website

Help improve our website at https://cyberrange-project.org/. See [website-related issues](https://github.com/Range42/website/issues) for current improvement opportunities.

The website is built using Jekyll. You can [build a local copy](https://github.com/Range42/website/blob/main/README.md) to test changes before submitting pull requests.

## Community involvement

Join our community:
- **Discord**: Real-time chat and support
- **Forums**: Discussion and knowledge sharing
- **Monthly meetings**: Community calls and project updates
- **Conferences**: Present your scenarios and research at cybersecurity education events

## Recognition and attribution

Contributors are recognized through:
- Public acknowledgment in release notes
- Contributor badges and profiles
- Annual community awards
- Speaking opportunities at conferences
- Co-authorship on academic publications

## Getting started checklist

New contributors should:
1. Read this contributing guide and the Code of Conduct
2. Join our Discord or forum for introductions
3. Review open issues labeled "good first issue"
4. Set up a development environment using our setup guide
5. Start with small contributions like documentation or bug fixes
6. Engage with the community and ask questions

Remember: Every contribution, no matter how small, helps advance cybersecurity education and training. Thank you for your interest in making Range42 better!
