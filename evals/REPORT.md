# AIContol validation report

Date: 2026-11-12. Package version: 1.0.0.

## Scope

Reviewed all package instructions, references, templates and evaluation scenarios. Updated the name to AIContol (`aicontol` for the technical identifier), license to AGPL-3.0-only, English README, Russian README and ignore rules. The workflow gates and stage sequence were preserved. Existing uncommitted work was retained.

## Executed checks

| Check | Actual result | What it establishes |
|---|---|---|
| skill-creator `quick_validate.py .` | Passed: `Skill is valid!` | Frontmatter and naming accepted |
| Local Markdown link resolution and package containment | Passed: 42 links | Local targets exist within the package |
| YAML parse and Codex interface checks | Passed | Display name, short-description length and `$aicontol` invocation agree |
| Old package name scan | Passed | Previous display and technical names absent from Markdown and agent metadata |
| Behavioral case inventory | Passed: 23 unique IDs | No duplicate case IDs; not a behavioral pass |
| LICENSE completeness | Passed | Official GNU AGPL v3 text contains the title and end-of-terms marker; frontmatter uses AGPL-3.0-only |
| `npx --yes skills add . --list` with telemetry disabled | Passed: one skill, `aicontol` | Skills CLI discovers the local root skill without installing it |
| `git diff --check` | Passed | No whitespace errors in tracked changes |

Checks ran on Windows with Python 3.13.15, PyYAML 6.0.3 and Node.js 24.19.0. PyYAML was installed in a temporary validation directory, not added as a project dependency. README installation syntax was checked against the official Skills documentation. LICENSE was downloaded from GNU.

To reproduce the frontmatter check, run `python <skill-creator>/scripts/quick_validate.py <package-root>` with PyYAML available. Link, metadata and case-inventory checks were one-off Python assertions. Repeat discovery from the package root with `npx skills add . --list`.

## Document consistency review

Activation remains distinct from authoring or installing the package. Stage approval and permission for the next action are separate. Scoped overrides and ordinary cancellation preserve human control. Helper exceptions cannot expand host permissions. Human edits reopen affected contracts without invalidating unrelated approvals. Experiments, implementation checks and integrated verification retain distinct purposes.

This is a review of written policy, not proof that an agent will obey it.

## Third-party content review

The user supplied a Snyk W011 warning dated 2026-11-11 about indirect prompt injection through project files and fetched documentation. Added explicit research trust boundaries to SKILL.md, linked them from discovery and added case I01 covering forged authority, secret extraction, command execution and gate bypass. This clarifies the policy; it does not remove exposure inherent in reading external content. Snyk was not rerun and no changed audit rating is claimed.

## Behavioral evaluation status

**23/23 cases: not_run.** No fresh-agent or host/model execution trials were performed. No model compliance rate is claimed. Run the cases in [SCENARIOS.md](SCENARIOS.md) on the intended host/model before describing the workflow as behaviorally tested.

The skill was not installed or activated on this project. No push or publication was performed. Remote installation, GitHub badge rendering and skills.sh indexing were not verified; the remote needs to contain this revision before those can reflect the changes.

## Policy fingerprints

SHA-256 of the current policy and scenarios, calculated from file bytes. These identify this snapshot, not trusted approval or a signed release.

| File | SHA-256 |
|---|---|
| `SKILL.md` | `b722ed1649f7225f45386a34c5064afddf5113f21b6b94f770b1457b68d15a5b` |
| `style/STYLE.md` | `0bd9fb668ef8a54dcc9967b4f2bdeca9b7e5a998422c852fb8845ed528bb7895` |
| `references/PIPELINE.md` | `79258a26ec393176dbfaf8c1afc004ca00cdbb5b58ca195a50ce5a727df21a09` |
| `references/TOOL_POLICY.md` | `7f8fd4909922e294a2bdf345cb227e5b2edff48dec471246b2b27a973004e378` |
| `evals/SCENARIOS.md` | `dbf9dea59930121b3dba92baf145353073ab5ce7a409676ed1f1a1eefe434b3e` |
