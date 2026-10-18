# DDLS v2.2 — Five-Minute Quickstart

Start with the [one-page Core](CORE.md). The [DDLS v2.2 playbook](DDLS-v2.2.md) governs when details are disputed. This guide is deliberately shorter than an approval workflow.

## 1. Start in TRANSPARENT mode

Describe the objective, constraints, and acceptance in the task as you normally would. Fix local bugs normally. **No YAML, loop registry, or return-contract file is required.**

## 2. Decide whether the blocker is real

Before SHIFT, answer the [five blocker qualification questions](CORE.md): evidence, classification, authority, smallest remedy, and a falsifiable prediction.

| Observation | Correct next action |
|---|---|
| Ordinary code defect | `FIX` within current scope |
| Unknown cause | `DIAGNOSE`; collect reproducible evidence |
| Operator permission or external dependency | `WAIT / ESCALATE`; do not invent an enabling module |
| Proven missing prerequisite | `MANAGED_SHIFT`: checkpoint, short return conditions, bounded child |
| Production, security, irreversible or shared-state risk | `GOVERNED` regardless of whether you shifted |
| Hard circular dependency or invalid assumption | `REPLAN`, not indefinite nesting |

## 3. Keep the paperwork small

For a qualified shift, an existing issue, PR note, or safe checkpoint can contain:

`Parent / Blocker evidence / Child / Return condition / Checkpoint / Authority / Remaining budget`

Only use the [optional YAML templates](../templates/) when useful or required by project policy. The agent may draft these notes; the engineer reviews substantive decisions rather than retyping records.

## 4. Share one budget across the entire objective

Allocate child resources from the parent's **remaining** time, tool, token, and cost envelope. Reserve enough for integration and parent return.

**Default review thresholds:** 3 similar repairs per hypothesis; 3 active nested levels including parent; 2 total child shifts per original objective. They are not permission to exceed other limits.

If reliable token/cost metering is unavailable, mark it `UNKNOWN` and use known tool/time/shift ceilings. After each enabling loop or proposal to nest deeper, identify evidence-backed progress. No progress or exhausted resources → `STOP / REPLAN / ESCALATE`.

## 5. Return only when ready

Verify accepted return conditions, required integration authority, relevant source/contract/schema/runtime drift, and actual tests. `COMPLETED` development does **not** mean `DEPLOYED`.

## 6. Report at the right size

Normal work: `Result / Tests / Changes / Risks / Next action`.

Material shift: add checkpoint, return contract, child allocation, remaining parent budget, and next gate.

High-risk task: durable evidence, approvals, side effects, and recovery.

## Clarifications

- A shift is **not** required for a routine failure or an external approval.
- Nested children **never** replenish an objective's budget.
- "No progress" does not mean "no lines of code"; valid diagnosis may disprove a bad architectural hypothesis.
- An agent's claimed budget or test status is **not** independently verified. Unavailable trustworthy evidence remains `UNKNOWN`.
- DDLS v2.2 deliberately includes **no validator or CLI**.

Practice with the [synthetic case studies](../examples/README.md).
