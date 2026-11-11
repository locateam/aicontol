# Stage review — template

Use as a concise review packet or response outline. Do not create a permanent file for every minor message. Remove this template note.

## Target

Stage, module/increment, artifact revision, reviewable file/diff/demo links.

## Result and scope

What changed, why, which accepted requirements it addresses, and which requested items remain unfinished. Distinguish prototype, mock and production behavior.

## Verification evidence

| Claim / requirement | Revision | Check actually performed | Result | Evidence |
|---|---|---|---|---|

Separate automated tests, code inspection, rendered UI inspection and human review. List not_run checks explicitly. Do not reuse stale evidence after a relevant change without rerunning it.

## Human walkthrough

1. Open/run the specific artifact in the approved environment.
2. Perform a concrete action.
3. Compare with the expected observable result.

Include a useful failure/error case where applicable. Provide commands and prerequisites when appropriate; do not hide cost, external side effects or credentials in a walkthrough.

## Limitations and decisions

Remaining uncertainty, failed/waived checks, relevant trade-offs, scoped helper exceptions, contract changes and approvals invalidated by them.

## Requested transition

"Approve [stage/module/revision] and authorize [exact next stage/module/actions], or specify corrections."

If an unresolved check requires a waiver, name that check and its consequence. Do not bundle unrelated deployment/publication permissions into routine acceptance.

## Actual human response

Fill only after the user replies: decision, reference, accepted/waived scope and newly authorized work. Until then, state is awaiting_review.
