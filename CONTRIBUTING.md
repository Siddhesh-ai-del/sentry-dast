# Contributing to sentry-dast

Thank you for your interest in contributing to **sentry-dast**. This repository is in a pre-release planning stage; contribution guidance will evolve as implementation begins.

## Reporting bugs

- Search existing issues before opening a new one.
- Use the **Bug report** issue form and include reproduction steps, expected behavior, and observed behavior.
- Redact secrets, tokens, credentials, and any sensitive data from logs and screenshots.

## Suggesting features

- Use the **Feature request** issue form.
- Describe the problem first, then the proposed solution, and explain which project principle the change advances.

## Development standards (planned)

When implementation work begins, contributions are expected to follow these standards:

- **Test-driven development:** write a failing test, implement the minimal change to pass, then refactor.
- **Coverage:** target 80%+ coverage for critical functionality.
- **Code quality:** small, focused changes; clear naming; no hardcoded secrets; input validated at boundaries.
- **Commits:** use [Conventional Commits](https://www.conventionalcommits.org/) (for example, `feat:`, `fix:`, `docs:`, `test:`).

## Pull requests

- Keep pull requests scoped to a single concern.
- Ensure tests pass locally before requesting review.
- Complete the pull request checklist, including confirmation that no secrets are committed.
- Maintainers may request changes to align with project principles and roadmap priorities.

## Code of Conduct

This project follows the [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you agree to uphold it.
