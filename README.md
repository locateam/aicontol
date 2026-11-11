# AIContol

<p align="center"><em>F&#42;ck off, <strong>All in contol</strong>.</em></p>

[![GitHub stars](https://img.shields.io/github/stars/locateam/aicontol?style=flat&labelColor=000000&color=6AA6DA&cacheSeconds=300)](https://github.com/locateam/aicontol/stargazers)
[![skills.sh installs: pending](https://img.shields.io/badge/skills.sh_installs-pending-E1E5AC?style=flat&labelColor=000000)](https://skills.sh/locateam/aicontol)
[![Version: 1.0.0](https://img.shields.io/badge/version-1.0.0-DBE3E9?style=flat&labelColor=000000)](SKILL.md)
[![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-FBFBF8?style=flat&labelColor=000000)](LICENSE)

The install counter is pending until skills.sh indexes the skill; no installation count is claimed.

English · [Русский](README.ru.md)

AIContol is a skill for building software with an AI agent while you review the work. The agent researches, proposes, writes code and runs checks. You decide what to build, edit the artifacts and approve each next step.

Version 1.0.0. Static checks are recorded in the [validation report](evals/REPORT.md). Agent behavior has not yet been tested in fresh sessions.

## Install

With [Node.js](https://nodejs.org/) 22.20 or later and Git available, run:

```sh
npx skills add locateam/aicontol
```

The [Skills CLI](https://skills.sh/docs) lets you choose an agent and installs into the current project. To install globally for Codex:

```sh
npx skills add locateam/aicontol --skill aicontol --global --agent codex
```

The display name is AIContol; the technical skill name is `aicontol`.

To inspect the skills in a local checkout before installing:

```sh
npx skills add . --list
```

For a manual installation, copy the complete package into your agent's skills directory as `aicontol/`. Keep `SKILL.md` and its supporting directories together. Reload skill discovery if your agent requires it.

## Use

Select AIContol in your agent, or ask:

> Use $aicontol for this project. Start with the working agreement. I want to review each module myself.

The agent first agrees the process, allowed actions, language and review size with you. Installing the skill does not authorize it to begin project work.

## How the work moves

1. Agree on the process, scope of autonomy and override phrase.
2. Clarify the problem, users and scope together.
3. Choose the stack, architecture and engineering rules.
4. Consolidate project documentation, decisions and state.
5. Define module contracts, architectural sketches and work order.
6. Run bounded experiments where feasibility is uncertain.
7. Implement approved increments, test them and fix what fails.
8. Verify the integrated system and review the handoff.

You review the result before the next stage. Experiments and implementation also have checkpoints per module or increment. Small tasks can use short stages or combined reviews when you approve that arrangement. Existing projects can reuse work you accept as already complete.

An experiment answers a risk question; implementation delivers maintained behavior. Tests run during implementation as well as at the end.

## Change the plan

The agent proposes `PIPELINE OVERRIDE:` as the default phrase. Once you accept it, you can give a scoped instruction:

> PIPELINE OVERRIDE: skip the feasibility prototype for M03 and start its approved implementation.

The agent records what was skipped and the missing evidence. You can always say "stop" or change the process in plain language. The phrase is a convenience, not a password.

This skill is a working agreement, not a security sandbox. It cannot guarantee compliance or override host permissions. Publishing, deployment, spending and external data transfers need their own applicable authorization. Other helper skills can be used within the agreement; conflicting workflow rules need a scoped decision.

## Package contents

| File | Purpose |
|---|---|
| [SKILL.md](SKILL.md) | Activation, approvals, overrides and continuity |
| [Style](style/STYLE.md) | Communication and review packets |
| [Pipeline](references/PIPELINE.md) | Stage contracts and checkpoints |
| [Tool policy](references/TOOL_POLICY.md) | Helper skills, MCP tools and exceptions |
| [Project state](assets/PROJECT_STATE.md) | Resumable state, decisions and permissions |
| [Module contract](assets/MODULE.md) | Interfaces, risks and acceptance cases |
| [Stage review](assets/STAGE_REVIEW.md) | Review template |
| [Evaluation scenarios](evals/SCENARIOS.md) | Behavioral cases to run in a disposable workspace |
| [Validation report](evals/REPORT.md) | Checks actually run and remaining gaps |
| [Sources](SOURCES.md) | Influences and deliberate differences |
| [Agent metadata](agents/openai.yaml) | Optional Codex UI metadata |

The instructions are in English. You choose the conversation and project documentation language. No particular framework, MCP server or subagent runtime is required.

## Make it installable from GitHub

Publish the complete package at `locateam/aicontol`, with `SKILL.md` at the repository root. Keep its `name: aicontol`, description and referenced files in the published revision. The repository must be accessible to whoever installs it; a public repository is the simplest option for public distribution.

No npm package or `package.json` is needed: `npx` runs the Skills CLI, which downloads the skill from GitHub. After publishing, check discovery:

```sh
npx skills add locateam/aicontol --list
```

Then try the installation command above. According to the [Skills FAQ](https://skills.sh/docs/faq), listing on skills.sh follows installations recorded through CLI telemetry. Adding a badge alone does not register a skill or create an install count.

## Contributing

Keep workflow changes in the entrypoint and references, communication changes in the style file, and reusable artifacts in templates. Validate frontmatter and local links, then run relevant [behavioral scenarios](evals/SCENARIOS.md) in a disposable workspace. Record the host/model, input, observed actions and outcome. A static validator cannot prove the agent will respect a checkpoint.

The README wording was reviewed using [Humanizer](https://github.com/blader/humanizer) as an editorial reference. It is not a runtime dependency.

## License

[GNU Affero General Public License v3.0 only](LICENSE) (`AGPL-3.0-only`).
