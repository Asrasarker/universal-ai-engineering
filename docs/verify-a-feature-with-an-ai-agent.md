# How to tell when your coding agent has actually verified a feature

A coding agent can finish editing a feature before anyone knows whether the user flow works. Password reset is a good example. The page can build, the form can submit, and the reset email can still fail to arrive.

I released Universal AI Engineering as a public preview for people taking a product from idea to launch with AI. It’s an MIT-licensed skill for compatible coding agents. It starts by reading the relevant conversation and repository, then helps you identify the next decision, choose what to build, and gather evidence that the result is ready to ship. Password reset is one way to see the verification step in action.

## Try it on a single feature

Pick an existing feature your agent can inspect in a local or test environment. After [installing the skill](https://github.com/Asrasarker/universal-ai-engineering#use-it-in-your-agent), give it a prompt like this:

> Use Universal AI Engineering to review password reset in this repo. Read our relevant chat and repo notes. Simulate a valid reset and an expired link, then run the available local checks. Show me what you actually verified. Ask before making changes.

For a reset flow, here is what counts as evidence:

| Scenario | What to verify |
| --- | --- |
| Valid reset | The test user receives a reset link and can sign in with the new password. |
| Expired link | The account stays unchanged and the user can request a fresh link. |
| Link used twice | The second attempt leaves the account unchanged. |
| Mail sandbox unavailable | The agent reports email delivery as blocked and identifies the missing prerequisite. |

A walkthrough of the expired-link case is a simulation. A passing browser check against a fake mail provider can verify the UI and local test setup. Real delivery needs evidence from the relevant mail environment. The skill keeps those outcomes visible, so a passing build can’t stand in for an unrun feature check.

## What the preview has verified

GitHub Copilot invoked the skill on a disposable repo and distinguished a simulation from tests it hadn’t run. Codex, Claude Code, and Gemini CLI discovered the skill in their project folders. Antigravity’s plugin validator found the skill. The [compatibility table](https://github.com/Asrasarker/universal-ai-engineering#compatibility-smoke-tests) lists the remaining sign-in and verification gaps.

If you try the skill on a real feature, I’d like to hear where it helped and where it got in the way. Share your agent and version, the stage you were in, and the expected behavior. A small, redacted example makes it easier to investigate.

[Download the preview](https://github.com/Asrasarker/universal-ai-engineering/releases/tag/v0.1.0-preview) · [Share feedback on GitHub](https://github.com/Asrasarker/universal-ai-engineering/issues)
