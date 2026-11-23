# Universal AI Engineering Skill

**Public preview.** The compatibility table shows which agents have passed discovery or live use.

A portable [Agent Skill](https://agentskills.io/specification) for planning, building, verifying, releasing, and operating software. It reads the relevant conversation and repository, asks about decisions that matter, and gives short progress updates after each stage.

The skill includes a scenario simulation and test-and-repair loop, evidence-based release decisions, optional enterprise and client handoff checks, and a reusable progress and test results template. Focused changes use only the checks that apply.

[Try the password-reset walkthrough](docs/verify-a-feature-with-an-ai-agent.md) to see how the skill reports simulations, test results, and blockers.

## Use it in your agent

Copy the whole [universal-ai-engineering](universal-ai-engineering/) folder into one documented project skill location. Keep the name and references together. Select the installed skill through your agent's available skill picker or invocation command.

| Agent | Project skill location | Setup |
| --- | --- | --- |
| OpenAI Codex | `.agents/skills/universal-ai-engineering/` | [OpenAI skill guide](https://learn.chatgpt.com/docs/build-skills) |
| Claude Code | `.claude/skills/universal-ai-engineering/` | [Claude Code skill guide](https://code.claude.com/docs/en/skills) |
| Cursor | `.cursor/skills/universal-ai-engineering/` | [Cursor skill guide](https://cursor.com/docs/skills) |
| GitHub Copilot | `.github/skills/universal-ai-engineering/` on supported surfaces | [GitHub Copilot skill guide](https://docs.github.com/en/copilot/concepts/customizations/agent-skills) |
| Gemini CLI | `.gemini/skills/universal-ai-engineering/` | [Gemini CLI skill guide](https://geminicli.com/docs/cli/skills/) |
| Google Antigravity | `.agents/skills/universal-ai-engineering/` | [Antigravity skill guide](https://antigravity.google/docs/skills) |

These paths are documented by the host vendors. Actual skill activation and tool access depend on the host, version, organization settings, and permissions. Some hosts, including Gemini CLI, require the project to be trusted before discovering its skills. Review the project before marking it trusted. For ChatGPT Chat or Work, use the applicable plugin distribution route when native installation is needed. For a chat interface without skill loading, supply the [instructions](universal-ai-engineering/SKILL.md) and relevant [reference files](universal-ai-engineering/references/) as context. The agent can only check what its tools and the user allow.

Example request:

> Use Universal AI Engineering to compare our chat with this repository. Tell me what stage we’re in, find missing acceptance criteria, and run local checks for the current feature. Show what was simulated, tested, or blocked.

## Compatibility smoke tests

The checks used a disposable repository and a read-only prompt. Discovery means the CLI listed the installed skill. Live use means a model invoked it and produced a result.

| CLI | Observed result |
| --- | --- |
| Codex | Native discovery passed. |
| Claude Code 2.1.325 | Native discovery passed. Live use stopped at an expired OAuth session. |
| Cursor 2026.11.22-e9042b2 | The CLI started. Sign-in was required before native discovery or live use could be verified. |
| GitHub Copilot CLI 1.0.114 | Native discovery and live use passed. Copilot invoked the skill, reviewed the fixture, and labeled the simulation separately from unrun tests. |
| Gemini CLI 0.70.0 | Native discovery passed in a trusted test workspace. Live use required a configured authentication method. |
| Antigravity CLI 1.5.14 | The official plugin validator found the skill in a temporary wrapper with no errors or warnings. Project discovery and live use remain unverified because the live run required sign-in. |

## Contents

- [SKILL.md](universal-ai-engineering/SKILL.md) covers activation, context review, scope, reporting, the verification loop, and release decisions.
- [Lifecycle](universal-ai-engineering/references/lifecycle.md) covers software delivery stages, platform checks, and operations.
- [Enterprise assurance](universal-ai-engineering/references/enterprise-assurance.md) covers reliability, data and identity, AI governance, and release evidence.
- [Client delivery](universal-ai-engineering/references/client-delivery.md) covers outcomes, decisions, user acceptance, and transfer of ownership.
- [Status template](universal-ai-engineering/references/status-template.md) records progress, test evidence, and open decisions.

## Safety and permissions

The package is Markdown only. It includes zero executables, dependency installers, hooks, connectors, telemetry, or credentials. Its instructions scope access to the requested project, keep secret values out of reports and transfers, direct the agent to inspect unfamiliar commands, and require authorization for publishing, transfers, and production changes. The host's sandbox and permissions enforce access. Repository and test commands are still code supplied by the project. Prefer an isolated environment and test credentials for unfamiliar projects.

## GitHub examples

- The Agent Skills format uses short discovery metadata, a `SKILL.md` entry point, and optional reference files, scripts, and assets. This skill loads its detailed guidance only when needed. [Agent Skills specification repository](https://github.com/agentskills/agentskills)
- Anthropic's examples show a clear trigger description and task-specific instructions. [Anthropic skills](https://github.com/anthropics/skills)
- OpenAI's catalog organizes reusable workflows for Codex. [OpenAI skills](https://github.com/openai/skills)
- GitHub's community catalog demonstrates focused skills and related Copilot customizations. [Awesome Copilot skills](https://github.com/github/awesome-copilot/blob/main/docs/README.skills.md)
- Vercel's React and web design skills show focused review criteria and use-case triggers. [Vercel Agent Skills](https://github.com/vercel-labs/agent-skills)

## License

[MIT](LICENSE). Copyright 2026 Asrasarker.
