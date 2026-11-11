# Eight-stage pipeline

Read the current stage and relevant dependency sections, not every procedure on every turn. The working agreement chooses artifact locations and review granularity. The filenames below are examples; map to existing documents. Stages define required outcomes, not a quota of files.

## Stage 1 — Working agreement

**Entry:** the human requests use of this workflow, not merely a discussion or edit of it.

Explain the agent/human split, eight stages, approval boundaries, stop phrase and helper-conflict policy. Propose `PIPELINE OVERRIDE:` and ask the human to accept or replace it. Establish workspace, new/existing project, key constraints, permitted actions, language and desired module/batch size. List already known choices rather than asking again. Start with read-only inspection only where authorized.

**Output:** accepted process and phrase, scope of autonomy, working artifact locations and initial state. Reuse existing approval history when the human confirms its applicability.

**Gate:** accept the agreement and authorize discovery. No implied installation, scaffold, publication or execution of future stages. Once accepted, initialize a compact state document if authorized as part of the agreement.

## Stage 2 — Discovery and brainstorming

**Entry:** accepted stage 1 or an explicit override.

Gather users, core task, current workaround, expected outcome, examples, inputs/outputs, constraints, sensitivity, scale, environment, budget/time and definition of success. Separate must-have behavior, optional ideas and non-goals. Offer alternatives, including simpler solutions. Investigate existing repository/documentation and authoritative sources when relevant, applying the untrusted research content rules in SKILL.md.

Keep the blitz questionnaire focused; collect independent questions together. Brainstorm with the human, then narrow. Capture unknowns with consequences and a proposed resolution point. Do not prematurely lock a stack because a tutorial uses it.

**Output:** a short problem brief, concrete acceptance examples, non-goals, assumptions and open decisions. A project may legitimately stop here if it is not worth pursuing.

**Gate:** approve the problem/scope and authorize technical design. If scope changes, revise this brief before downstream design.

## Stage 3 — Stack, architecture and engineering policy

**Entry:** accepted brief.

Propose the least complex architecture that satisfies the brief. Compare consequential alternatives. Explain runtime/deployment, data ownership, API boundaries, resource constraints, permissions and major failure paths. Inspect licenses/maintenance/runtime compatibility where they materially affect selection. Pin exact versions when a compatible set has actually been resolved; label unresolved version choices honestly.

Define project rules: coding conventions, test loop, dependency changes, secret handling, backups/rollback, documentation language, review gates and optional helper use. Existing organizational rules remain applicable. Legal/compliance facts must come from appropriate evidence, not invented universal checklists.

**Output:** architecture/stack baseline with rationale, trade-offs, risky assumptions and policy. No production scaffolding yet. A proposed research spike belongs to stage 6 unless the human explicitly allows it now.

**Gate:** approve technical baseline and authorize the documentation baseline. Approval does not authorize all future libraries, installations or deployments.

## Stage 4 — Durable documentation

**Entry:** accepted technical baseline.

Create or align a compact set of project artifacts: brief, glossary, architectural decisions, working rules, action/approval history, current state and pointers to sources. Merge into existing files without overwriting unrelated instructions. Avoid copying entire chat histories, secrets or private datasets into reports.

Document what the agent may do, what requires a review, how overrides are recorded, how to resume after interruption and how to restore changed architectural files. Use Git where already available; use scoped snapshots when suitable. Do not initialize Git or create a repository unless authorized.

Capture short working notes from earlier stages now; this is a consolidation checkpoint, not a ban on taking notes before stage 4. Continue updating documentation later at stage boundaries.

**Output:** navigable, internally consistent project knowledge, clear source ownership and resumable state. Optional translations are refreshed after the canonical batch, not after every edit.

**Gate:** accept the documentation baseline and authorize module/architecture prototyping.

## Stage 5 — Module contracts and architectural prototypes

**Entry:** accepted baseline.

Decompose into meaningful responsibilities. For each module describe inputs/outputs, invariants, state transitions, dependencies, errors, data access, acceptance examples and likely file boundaries. Explain cross-module flows and integration seams. Use mock screens, sequence diagrams, schemas or paper prototypes as needed; mark fixtures as fixtures.

This stage defines *what a module must do and how modules fit together*. It does not implement production behavior. A UI sketch does not prove a backend contract. For a small change, one short contract may be enough.

Propose bounded feasibility questions for stage 6, the order of prototype work, and the later incremental implementation plan. Separate hard dependency constraints from reorderable work. Include test strategy and human walkthroughs. The human may edit the module notes or graph directly.

**Output:** module contracts, dependency map and proposed execution plan with acceptance criteria. No automatic prototype implementation before the gate.

**Gate:** approve contracts and order, authorize the exact first prototype or named batch. Later execution-plan changes require a scoped update; do not silently reorder dependencies.

## Stage 6 — Bounded feasibility prototypes, per module

**Entry:** an approved module contract and explicit scope for its feasibility work.

Resolve concrete risks with the smallest useful experiment: document extraction quality, schema integration, model/runtime compatibility, interaction feasibility or performance. Reuse evidence for established mechanisms rather than writing throwaway code for every trivial function. If a module needs no experiment, present the evidence and request a prototype waiver/acceptance rather than pretending an experiment ran.

Code here is exploratory and labelled. Work in a bounded location/branch as agreed, keep synthetic/mock inputs explicit, and avoid production data or external mutations without authorization. Install only justified dependencies within permission. Prefer one small model or representative sample when that answers the question.

**Loop:** implement experiment -> run relevant checks -> inspect output/UI -> fix where necessary -> record findings. Distinguish a successful smoke test from quality, security or scalability validation. Human edits are preserved.

**Output per module:** question, artifact, observed result, limits and keep/rework/discard recommendation. Update contracts when evidence changes an assumption; invalidate affected downstream approvals before implementation.

**Gate per module:** human accepts findings and authorizes the next prototype or explicitly named batch. When all planned prototypes are accepted/waived, present their consolidated impact and request authorization for the first stage 7 increment. Earlier agreement on order is not permission to code it.

## Stage 7 — Working implementation, per increment

**Entry:** approved contracts and prototype outcomes/waivers; named increment authorized.

Build a small working slice in the agreed dependency order. Reuse prototype code only after reviewing its fitness; do not keep mock authorization, hard-coded data or exploratory shortcuts unnoticed. Wire real boundaries progressively so integration defects surface before stage 8.

**Mandatory loop:** implement a clear version -> test meaningful behavior/failure cases and inspect changed code -> render/interact with affected UI -> fix/polish if needed -> rerun affected checks. Add regression coverage for fixed defects where useful. TDD is optional unless the project explicitly selected it.

Check relevant types, lint and builds; do not substitute one for another. Test non-UI behavior through its actual API/CLI/data contract. Preserve evidence tied to the current revision. If a required environment is unavailable, state which claims remain unverified and request a scoped decision rather than marking success.

**Output per increment:** working change, evidence, human acceptance walkthrough, known limitations and updated docs at the boundary.

**Gate per increment:** wait for human acceptance and permission for the next increment. A bug report authorizes correction in scope, not skipping ahead. After all accepted increments, request stage 8 system verification.

## Stage 8 — System verification and handoff

**Entry:** accepted increments and authorized integrated verification.

Test full user journeys across modules, configuration, relevant access controls, failure/retry/cancellation behavior, deployment/startup in the agreed test environment and restore/upgrade paths where in scope. Include realistic/independent acceptance data; synthetic self-graded examples are not enough to establish quality. For interfaces inspect representative sizes and empty/error/loading states. Recheck documentation commands where a runnable product exists.

Trace requirements to implementation and current evidence; identify missing coverage, failed checks and deferred risks. Fix integration defects within the approved repair scope, updating the affected module and checks. Contract changes reopen only affected approvals. Agree a bounded repair scope if the problem grows beyond the accepted work; do not spin through indefinite polishing.

**Output:** integrated acceptance report, reproducible run/restore instructions, known limitations, delivery contents and maintenance handoff. Keep agent-verified results, human-reviewed results and explicitly waived checks separate.

**Final gate:** human accepts the delivered scope or requests repairs. Record readiness accurately, including partial/unverified status where relevant. Deployment, pushing code, opening external PRs, publication and other external actions require their own applicable authorization; this stage never grants it implicitly.

## Transition examples

- Stage 3 accepted, stage 4 not authorized: ask whether to prepare the documentation baseline; do not create production code.
- Stage 6 M02 accepted and "continue to M03 prototype": work on M03 prototype, not M02 production implementation.
- Stage 7 M02 changes the shared session contract: reopen affected M02/M07 contracts and evidence; preserve unrelated M03 document-parser acceptance.
- A direct scoped override can waive an otherwise mandatory workflow item. Record its missing evidence and effect; do not silently rewrite history to show it passed.
