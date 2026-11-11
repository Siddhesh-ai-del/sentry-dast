# sentry-dast

[![License: MIT](https://img.shields.io/badge/License-MIT-1e1e2e?style=for-the-badge&labelColor=313244&logo=opensourceinitiative&logoColor=cdd6f4)](LICENSE)
[![Status: Pre-release](https://img.shields.io/badge/Status-Pre--release-1e1e2e?style=for-the-badge&labelColor=313244&logo=rocket&logoColor=cdd6f4)](#project-status)
[![Platform: Linux](https://img.shields.io/badge/Platform-Linux-1e1e2e?style=for-the-badge&labelColor=313244&logo=linux&logoColor=cdd6f4)](#installation)
[![Language: Python](https://img.shields.io/badge/Language-Python-1e1e2e?style=for-the-badge&labelColor=313244&logo=python&logoColor=cdd6f4)](#architecture)

**Deploy-triggered security agents for B2B travel platforms, designed to verify findings before reporting.**

## Overview

sentry-dast is a planned agentic dynamic application security testing (DAST) system for B2B travel platforms. The project addresses a specific gap: travel platforms change frequently, and the most damaging vulnerabilities are often business-logic flaws that periodic, generic scanning misses or reports too late. sentry-dast is being designed to react to platform changes, focus testing on the changed surface, and report only findings that can be reproduced with deterministic evidence.

| Principle | Description |
| --- | --- |
| Verified findings | Findings are intended to be confirmed by deterministic replay before reporting, reducing false positives. |
| Safety by design | Planned execution controls include scope enforcement, rate limiting, health checks, audit logging, and operator approval gates. |
| Change-aware testing | A deploy or change signal is intended to drive targeted analysis instead of broad, untargeted scans. |
| Business-context relevance | Planned triage emphasizes business impact in travel workflows such as bookings, fares, refunds, and cross-agency access. |

## Why sentry-dast

B2B travel platforms evolve through frequent deploys, API changes, supplier integrations, and role or access updates. In this environment:

- **Business-logic flaws carry high impact.** Examples include cross-agency access to bookings, fare tampering in requests, and duplicate refunds.
- **Periodic testing becomes stale.** Findings can reach owners after the codebase has already changed.
- **Generic scanning creates noise.** Untargeted payload spraying and weak verification increase false positives and reduce trust.

sentry-dast is planned to address these problems by combining change detection, targeted attack planning, deterministic verification, and ticket-ready reporting within explicit safety controls.

## Planned capabilities

> None of these capabilities are shipped yet. The list below describes intended functionality under active planning.

- **Deploy-triggered change detection:** react to webhook or change signals and diff the relevant API surface.
- **API discovery and inventory:** build a knowledge graph of endpoints, parameters, roles, and business objects, including classification of active, zombie, and shadow APIs from traffic context.
- **Targeted attack planning:** generate focused test plans for relevant classes such as insecure direct object reference (IDOR) and fare/price tampering, with a deterministic fallback when model-based planning is unavailable.
- **Safety envelope:** enforce host allowlists, rate limits, circuit breaking, and append-only request audit logging, with operator controls (kill switch and approval gates).
- **Deterministic verification:** replay minimal proof steps to confirm reproducible findings before creating reports.
- **Business-context triage and reporting:** score severity by business impact and produce ticket-ready findings for the appropriate owner.
- **Retest after fix:** re-verify open findings on subsequent changes and record closure evidence when a fix is confirmed.

## Project status

sentry-dast is **pre-release**. This repository currently contains planning, governance, and community health documentation only. No implementation code, installable package, or runnable release is available at this time.

### Roadmap

| Phase | Scope | Status |
| --- | --- | --- |
| Idea and research | Problem analysis, competitive/technical research, feasibility assessment, and submission materials for TBO VOYAGEHACK 4.0 | In progress |
| Foundation (P0) | Repository scaffold, safety envelope, and mock travel target with planted and non-flaw fixtures | Planned |
| Core detection and verification (P0) | Change detection, API crawl and knowledge graph, deterministic validators, replay verification, and ticket reporting flow | Planned |
| Planning and reporting loop (P0/P1) | Local model-assisted planning with deterministic fallback, triage outputs, and retest-after-fix workflow | Planned |
| Differentiators and demo readiness (P1/P2) | Zombie/shadow inventory reporting, OpenAPI artifacts, dashboard/demo polish, and submission packaging | Planned |
| Release hardening | Documentation, reproducible setup, and verified demo evidence for public release readiness | Planned |

## Installation

Not yet available. No installable release, package, or runnable build is published at this stage.

## Architecture

The intended architecture is a Python-based monolith with internal modules and a strict safety boundary:

- **Change detection:** ingest deploy/change signals and identify modified endpoints, routes, or relevant artifacts.
- **Discovery and knowledge graph:** crawl and analyze application surfaces to maintain endpoint, role, and business-object context (SQLite-backed in the planned design).
- **Planning:** select targeted test actions using deterministic playbooks, with optional local model assistance constrained to planning and reporting text.
- **Execution and safety envelope:** route all outbound test traffic through a single safety-controlled layer (allowlist, rate limiting, circuit breaking, audit log).
- **Verification and triage:** confirm findings through replay, deduplicate results, and assign business-context severity.
- **Reporting and retest:** generate ticket-ready outputs and re-verify findings after fixes.

External sidecars (such as a mock target application or local model runtime) are planned where they provide clear boundaries, but the core control loop is intended to run as one coordinated system.

## Repository layout

```text
sentry-dast/
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.yml
│   │   ├── config.yml
│   │   └── feature_request.yml
│   ├── CODEOWNERS
│   └── PULL_REQUEST_TEMPLATE.md
├── docs/
│   └── README.md
├── .gitignore
├── CHANGELOG.md
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── LICENSE
├── README.md
├── SECURITY.md
└── SUPPORT.md
```

## Contributing

Contribution guidelines are available in [CONTRIBUTING.md](CONTRIBUTING.md).

## Security

Please review [SECURITY.md](SECURITY.md) for supported status and private vulnerability reporting.

## Support

Support channels and availability are described in [SUPPORT.md](SUPPORT.md).

## License

This project is licensed under the [MIT License](LICENSE).
