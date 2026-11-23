# Lifecycle and production checks

Use only gates relevant to the requested scope. Existing projects may enter at any phase, and several phases can run together. Record why a material gate is inapplicable or unresolved. Review likely failure modes and operational ownership whenever a change creates a new dependency or user-facing workflow. For material risks or customer control requirements, add the applicable checks from [Enterprise engineering assurance](enterprise-assurance.md). For formal business acceptance or a transfer of ownership, use [Client delivery and handoff](client-delivery.md).

| Phase | Evidence to look for |
| --- | --- |
| Discovery | Users, problem, outcome, assumptions, and constraints |
| Requirements | Scope and exclusions, acceptance criteria, dependencies, unresolved decisions |
| UX and design | Key journeys and accessible interaction, including loading, empty, error, and recovery states |
| Architecture | Data ownership and lifecycle, interfaces, trust boundaries, compatibility, reliability and cost tradeoffs |
| Implementation | Complete user or API path, maintained conventions, focused changes, reproducible build |
| Data and integrations | Validations, existing data, migration compatibility, provider sandbox behavior, retry/idempotency and partial failure handling |
| QA | Relevant automated/manual runs and regressions against acceptance criteria |
| Security and privacy | Defensive review of permissions, boundaries, secret handling, dependency findings, retention, delete/export and applicable human review |
| Performance and accessibility | Measurable targets for critical paths, representative device and network coverage, keyboard and assistive technology checks as applicable |
| Staging and acceptance | Candidate identity, production-like configuration, representative scrubbed or synthetic data, staging smoke checks and owner acceptance as needed |
| Production release | Rollout and recovery plan, release authorization, production smoke checks within authorized scope |
| Operations and improvement | Observable service health, incident ownership, support path, dependency maintenance and feedback to the backlog |

## Platform-specific coverage

- **Website and web app:** Check real navigation, responsive layouts, browser compatibility, forms and accessibility. Where applicable, check deep links, indexing and metadata, sessions and role restrictions.
- **Android and iOS:** Check supported OS/device matrix, permissions, background/resume, offline recovery, installation and upgrades, signing/store configuration, and staged release options. Distinguish simulator coverage from physical-device results.
- **Desktop:** Check OS support, file permissions, local data, install/uninstall, signed packaging and updater behavior where applicable.
- **API and backend:** Check contract compatibility, authorization, validation, timeouts, job retries, idempotency, pagination, rate limits, and downstream failures as applicable.
- **AI features:** Version the model, prompt and evaluation set. Test representative tasks and edge cases, score against explicit quality thresholds, and review privacy, instruction boundaries, tool permissions, fallback behavior, latency, and cost. Record the environment and sampling limits for probabilistic results.

## Release and monitoring

- Identify the release artifact or commit, target, config differences, and staging evidence. Check migration compatibility, deployment order, and recovery for persistent changes. Verify restore evidence where recovery depends on backups. Define rollback triggers, the last known good version, and who can act. For irreversible schema or store changes, plan forward recovery and containment.
- Plan a staged rollout or equivalent where supported. Define smoke checks and success/abort signals. With authorized release access, observe rollout, smoke-test critical paths, and report health against those signals.
- Identify signals and owners for relevant uptime, errors, latency, saturation, job backlogs, provider events, conversion failures, and spend. For each critical alert, record threshold or condition, destination, owner, and first action. Verify signal arrival and alert routing where access permits. Minimize personal and sensitive data in logs and telemetry.
- For incidents, identify impact and start time from evidence, contain within authorized scope, recover and verify health, then record follow-up actions and owners. For a health check, state the observed time window, sources, and blind spots.
- Reuse existing tooling. Typical capabilities include CI, browser/device checks, error tracking, metrics/logs/traces, synthetic uptime, and privacy-aware product analytics. Choose tools based on platform, scope, and access when tool selection is requested. Operational guidance alone does not provision a live monitor.

## Common gaps

Look for account recovery, role boundaries, accessibility, data retention/deletion, migration of old records, third-party outages, duplicate messages or charges, support ownership, restore testing, reversibility, abusive usage, degraded networks, alert delivery, and operating cost. Raise gaps only when relevant and explain the impact, the evidence or missing decision, and the next action.
