# Sources and design influences

Reviewed on 2026-10-27. These upstream projects are references, not required dependencies or instructions automatically activated by this package. No upstream skill body is bundled. The procedures and templates here are original adaptations of common engineering practices.

| Source | Useful idea | Adaptation / deliberate limit |
|---|---|---|
| [Matt Pocock skills](https://github.com/mattpocock/skills), [domain-modeling](https://github.com/mattpocock/skills/blob/main/skills/engineering/domain-modeling/SKILL.md), [grill-with-docs](https://github.com/mattpocock/skills/blob/main/skills/engineering/grill-with-docs/SKILL.md) | Clarify domain language and durable decisions; compose focused helpers | Use a bounded interview, a domain glossary and meaningful decision notes. Consolidate docs at review boundaries; do not impose continuous file rewrites or endless grilling. |
| [Superpowers](https://github.com/obra/superpowers), [verification-before-completion](https://github.com/obra/superpowers/blob/main/skills/verification-before-completion/SKILL.md) | Support completion claims with actual verification evidence | Tie commands/results to revisions and inspect actual output. Do not adopt mandatory TDD, delegation or a different gate process implicitly. |
| [GitHub Spec Kit](https://github.com/github/spec-kit) | Connect product specification, technical plan, implementation tasks and validation | Trace requirements through module contracts to evidence. Do not require its CLI or duplicate every artifact in a second documentation system. |
| [GSD Core](https://github.com/open-gsd/gsd-core) | Maintain resumable phase state and include user verification | Keep compact state and explicit next authorized actions. Do not assume a specific context size, autonomous mode or subagent infrastructure. |

## Recommended borrowing order

1. Evidence-backed completion claims and honest unverified status.
2. Domain glossary and small, useful architecture decisions.
3. Requirement-to-module-to-test traceability.
4. Durable state for handoff and context recovery.
5. Optional specialized helpers after inspecting their exact rules.

A useful future addition is a set of host-specific behavioral test harnesses. It should measure stage-boundary violations, unnecessary reapproval, missed human edits and unsupported completion claims. Add a harness only when there is a real target host and a safe evaluation environment; no placeholder orchestration framework is included now.
