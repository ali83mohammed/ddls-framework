# Case Study 04 — When DDLS Overhead Is the Wrong Choice

**Synthetic counterexample · DDLS v2.2-compatible · Decision: `FIX`, not `SHIFT`.**

> An illustrative failure mode, **not** evidence that a real engineer or agent took these actions.

## Situation

A small library function incorrectly handles an empty input. Its unit test reproduces the failure. The fix fits within the developer's existing scope, requires no new service, and can be validated with the project's normal test suite.

## Hypothetical baseline: without DDLS

A developer reads the assertion, fixes the condition, reruns the unit tests, and reports the change. No new planning artifact is required.

## Overapplied DDLS (undesirable)

An agent incorrectly classifies the defect as a missing 'input validation architecture', creates an enabling loop and three YAML records, asks for unnecessary approval, and spends a substantial portion of its task budget preparing documents. This is **an imagined anti-pattern**, not observed data. The original error remains unfixed.

The alleged blocker has **no independent missing prerequisite**. The return contract adds no information beyond the already-failing unit test.

## Correct DDLS v2.2 outcome

Answer the five blocker questions:

| Question | Finding |
|---|---|
| Observable evidence | One failing local unit test |
| Category | In-scope implementation defect |
| Current authority | Code and test changes already permitted |
| Minimal remedy | Adjust one branch and rerun relevant tests |
| Falsification | If the local change does not address the test, diagnose before assuming a separate capability is missing |

Decision: **`FIX` in TRANSPARENT mode.** No SHIFT record, YAML, or new review gate. Keep the project's existing security rules and ordinary CI checks.

## What could invalidate this judgment?

If later evidence shows several independent components depend on a genuinely absent shared contract, qualification can be reopened. It must cite that **new evidence**, rather than retroactively describing a local bug as a hard dependency.

## What to measure in a real experiment

Compare time spent on documentation, unnecessary child tasks, tokens/tool calls where measurable, actual acceptance of the fix, and reviewer interventions. An overhead penalty is an acceptable **negative DDLS result** that should be published, not concealed.

## Takeaway

**A workflow that requires more ceremony to fix an ordinary bug than the bug itself has failed its proportionality objective.** See [Core](../../docs/CORE.md) and the [evaluation protocol](../../docs/VALIDATION-PLAN.md).