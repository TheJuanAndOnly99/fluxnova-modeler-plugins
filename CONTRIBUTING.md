# Contributing to Fluxnova Modeler Plugins

Thank you for your interest in contributing to this project!

## Contribution Guidelines

For the overarching contribution and governance policies, please refer to the main Fluxnova repository's [CONTRIBUTING.md](https://github.com/finos/fluxnova-bpm-platform/blob/main/CONTRIBUTING.md).

This document supplements those guidelines with plugin-specific contribution requirements.

## Code of Conduct

All contributors are expected to follow the [FINOS Community Code of Conduct](https://www.finos.org/code-of-conduct).

## How to Contribute

1. **Fork** this repository
2. **Create a feature branch** (`git checkout -b feature/my-feature`)
3. **Make your changes** following the guidelines below
4. **Run tests and linting** to ensure quality
5. **Commit your changes** with a clear, descriptive message
6. **Push** to your fork
7. **Open a Pull Request** against the `main` branch

## Development Setup

```bash
# Clone your fork
git clone https://github.com/YOUR_USERNAME/fluxnova-modeler-plugins.git
cd fluxnova-modeler-plugins

# Navigate to the plugin you're working on
cd plugins/code-editor-plugin

# Install dependencies
npm install

# Run all checks (lint, test, build)
npm run all
```

## Testing Policy

**All major changes must include tests.** This project maintains automated test suites to ensure code quality and prevent regressions.

### When Tests Are Required

- **New features:** Must include unit tests covering the new functionality
- **Bug fixes:** Should include a test that reproduces the bug and verifies the fix
- **Refactoring:** Existing tests must continue to pass; add tests if coverage gaps are identified

### Running Tests

```bash
# Navigate to the plugin directory
cd plugins/code-editor-plugin

# Run tests
npm test

# Run tests in watch mode during development
npm run test:auto

# Run full CI checks (lint + test + build)
npm run all
```

### Test Expectations

- Tests are run automatically on every pull request via GitHub Actions CI
- **All tests must pass** before a PR can be merged
- Test coverage should not decrease significantly with new changes
- Tests should be deterministic and not depend on external services

## Code Quality Standards

### Linting

This project uses ESLint for code quality. All code must pass linting before merge.

```bash
# Run linter
npm run lint

# Auto-fix linting issues where possible
npm run lint:fix
```

### Code Style

- Follow the existing code style in the repository
- Use meaningful variable and function names
- Keep functions focused and reasonably sized
- Add comments only when the code's intent is not self-evident

## Acceptable Contributions

Contributions are welcome in the following areas:

- **Bug fixes** with accompanying tests
- **New features** that align with project goals
- **Documentation** improvements
- **Test coverage** improvements
- **Performance** optimizations
- **Security** fixes (see [SECURITY.md](SECURITY.md) for vulnerability reports)

### Contribution Requirements

1. **License compatibility:** All contributions must be compatible with the Apache-2.0 license
2. **No new dependencies with Category X licenses:** See [FINOS License Categories](https://community.finos.org/docs/governance/software-projects/license-categories/)
3. **Documentation:** Update relevant documentation for user-facing changes
4. **Tests:** Include tests for new functionality or bug fixes
5. **CI passing:** All automated checks must pass

## Dependency Management

### Adding Dependencies

When adding new dependencies:

1. Prefer well-maintained packages with active communities
2. Check the license is compatible (Apache-2.0, MIT, BSD, ISC, etc.)
3. Consider the security posture of the dependency
4. Minimize the number of transitive dependencies where possible

The `dependency-review` workflow automatically checks new dependencies for:
- Known vulnerabilities
- License compatibility with FINOS policies

### Updating Dependencies

- Renovate is configured to automatically propose dependency updates
- Security updates should be prioritized and merged promptly
- Breaking changes in dependencies should be tested thoroughly

## Contributor Permission Escalation

<!-- TODO: Define specific maintainer contacts for this repository -->

Contributors who demonstrate sustained, quality contributions may be considered for escalated permissions (write access, maintainer status). The process is:

1. **Track record:** Demonstrated history of quality contributions over time
2. **Review:** Existing maintainers review the contributor's work and engagement
3. **Verification:** Basic identity verification through organizational affiliation or community vouching
4. **Approval:** Consensus among existing maintainers
5. **Onboarding:** New maintainers are added with appropriate permissions and onboarded to project processes

Escalated permissions are granted based on the principle of least privilege. Contributors receive only the permissions necessary for their role.

## Pull Request Process

1. **Create a descriptive PR title** summarizing the change
2. **Fill out the PR template** with relevant details
3. **Link related issues** using keywords like "Fixes #123"
4. **Wait for CI checks** to complete
5. **Address review feedback** promptly
6. **Maintainers will merge** once approved and CI passes

### PR Review Expectations

- PRs require at least one maintainer approval before merge
- Reviewers may request changes for code quality, test coverage, or documentation
- Large PRs may take longer to review; consider breaking into smaller changes

## Questions?

- For general questions, open a [Support Question](https://github.com/finos/fluxnova-modeler-plugins/issues/new?template=support_question.yml)
- For CLA/DCO questions, email [help@finos.org](mailto:help@finos.org)
- For security issues, see [SECURITY.md](SECURITY.md)
