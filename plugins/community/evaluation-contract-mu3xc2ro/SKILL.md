# Evaluation Contract

## Separate Four Kinds of Evidence

1. Human annotation: `agree / revise / pending` describes the expected design,
   not whether an implementation works.
2. Prototype inspection: screenshot and interaction evidence from synthetic UI.
3. Deterministic tests: transitions, scoped contracts, integration and native tests.
4. Field effectiveness: observed user outcomes on a consented task, with a baseline.

No aggregate score may hide failed authorization, data loss, mistaken identity,
external action or privacy gates. Seven passing mock tests are not thirty passed
product cases. Every production result in `eval-matrix.json` begins `not_run`.
Source expectations remain available; proposed design resolutions are separate
fields when feedback changes the original expectation.

## Suite Structure

| Suite | Method | Release evidence |
| --- | --- | --- |
| Visual | Same-scale screenshots of Web/macOS, light/dark, width 1440/1024/390 | No overlapping text, readable contrast, bounded participants, content-first hierarchy |
| Interaction | Real browser automation and keyboard walkthrough | Draft/scope continuity, focus, menu dismissal, mention selection, selectable dates |
| Domain | Existing API fixtures + real canonical readback | Identity, source revision, relationship scope, idempotency, conflict and deletion |
| Model | Frozen authorized or synthetic fixtures; evidence-backed rubric | Grounded citations, uncertainty, no-action, attribution; no person scoring |
| Security | Adversarial tool text and revoked/expired grants at server/runtime boundary | Zero unauthorized reads/writes; immediate failed-closed behavior |
| Native | Signed development build on actual Mac | Picker cancel, OCR failure, sleep/wake, quick panel continuity, notification privacy |
| Field | Consented comparative tasks with the same source material | Less reconstruction and fewer corrections without less human control |

## Suggested Effectiveness Pilot

These are **proposed thresholds**, not measured results or scientific validity
claims. Recruit 5-8 target users for formative discovery, not significance claims.
Compare the current product and the candidate using balanced task ordering and
equivalent synthetic/authorized scenarios. Separate cold-start learning from
repeat-task efficiency. Record only task-level timing and error categories,
not raw private conversations in analytics.

| Metric | Task | Initial target |
| --- | --- | --- |
| First useful input | Start without a person | >=90% complete unaided; median <=15 seconds |
| Context retrieval | Resume correct Session and source | >=90% correct; median time at least 20% below measured baseline |
| Five-second clarity | State what changed on person page | >=80% identify the intended current dependency |
| Identity correction | Same-name contacts | Zero wrong identity confirmations in the pilot |
| Control comprehension | Distinguish confirm fact vs send message | All participants understand that confirmation does not send |
| Interaction burden | Count corrections, unnecessary dialog dismissals | Fewer than baseline without hiding consequential review |
| Perceived quality | Paired preference and reasoning | Collect preference and specific friction; no fabricated expert score |

If the existing Web flow cannot complete a task, report it as a baseline
failure; do not invent a relative percentage improvement. Summarize per-user
results and uncertainty rather than quoting precise significance from this
small formative sample.

## AI and Tool Correctness

For each model fixture store: input classification, authorized scope, expected
evidence fragment IDs, acceptable uncertainty/no-action, prohibited actions,
model/prompt/tool versions, attempt ID, and judge explanation linked to exact
output spans. Automated judges assist review; deterministic authorization
checks remain independent. Evaluate English and Chinese separately.

TS-030 must be tested with: grant expired before call; revoked during call;
tool reply requesting all contacts; Skill declares unavailable capability;
reauth cancelled; tool timeout; retry after reconnection with changed scope.
Re-check grant revision before accepting results and before any consequential
write. Untrusted tool content cannot alter authority. Failures preserve the
draft and visible recovery, and may not trigger hidden alternate connectors.

## Evaluation Record

Required fields: case ID, build ID, platform/OS, viewport/theme/text scale,
fixture classification, steps, observed result, evidence path, verdict,
limitations, reviewer and timestamp. Allowed verdicts: `passed`, `failed`,
`blocked`, `not_run`. Prototype observations require an explicit `mock` label.
Store screenshots only with synthetic or consented data; preserve source
retention/deletion boundaries. Never copy the private annotation store into a
public design artifact or model prompt.

## Design Acceptance Gate

One selected direction can be iterated against the user's detailed feedback,
but this iteration is not accepted automatically. Before a consequential
production migration, compare at least two rendered compositions at equal
scale, get user preference with reasons, and freeze the chosen direction.
Current v1 is one interactive direction; a second comparison remains pending.

Then approve by feature slice, not all screens as one checkbox. Freeze tokens,
page/state inventory and contract IDs with the accepted build. A later change
to authority or scope requires a new review even when pixels barely change.

## Provenance

Formalized by Open Design from candidate 5768d435-a9bf-4f51-84ba-acc70e529479.
