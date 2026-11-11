# Security Policy

## Supported versions

sentry-dast is in a pre-release stage. No released versions are currently supported with security updates.

| Version | Supported |
| --- | --- |
| Pre-release (unreleased) | No |

## Reporting a vulnerability

Please report suspected security vulnerabilities privately. **Do not open a public issue for security-sensitive reports.**

- **Preferred:** use [GitHub private vulnerability reporting](https://github.com/Siddhesh-ai-del/sentry-dast/security/advisories/new) for this repository.
- Include: a clear description of the issue, affected components (if known), steps to reproduce, potential impact, and any suggested mitigation.

We will acknowledge receipt when possible and work to assess and address confirmed issues. Response timelines are best-effort during the pre-release phase.

## Scope

This policy applies to code, configuration, documentation, and automation published in this repository.

## User guarantees (pre-release)

- No implementation code is shipped in the initial repository state.
- As the project develops, security-relevant behavior (including safety controls and audit logging for planned agent actions) will be documented transparently.
- Secrets and credentials must never be committed to the repository.
