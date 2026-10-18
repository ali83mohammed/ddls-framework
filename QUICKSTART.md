# DDLS v2.1 — Day-to-Day Quickstart

This guide is a compact companion to the [full playbook](DDLS-v2.1.md). In case of conflict, the full playbook governs.

## 1. Begin with a task contract

State **objective**, **allowed scope**, **prohibited changes**, **acceptance**, **authority**, and **stop conditions**. Use [`prompts/task-start.md`](../prompts/task-start.md) or [`templates/primary-loop.yaml`](../templates/primary-loop.yaml).

## 2. Keep ordinary work ordinary

Fix bugs and missing local code directly. A shift is justified only when a **qualified, evidenced prerequisite** cannot be addressed safely within the current task boundaries.

## 3. Apply this decision table

| You discover | Do this |
|---|---|
| Local defect within scope | `FIX` |
| Unclear root cause | `DIAGNOSE` |
| Missing required capability | `FREEZE` and `SHIFT` |
| Independent prerequisite work | Consider `PARALLELIZE` with resource isolation |
| A hard dependency cycle | `REPLAN` rather than push another loop |
| An external dependency | `WAIT` with a recheck trigger |
| An invalid assumption | `INVALIDATE` affected evidence and decisions |
| An unauthorized or unsafe action | `STOP` / `ESCALATE` |

## 4. Shift safely

Capture a reproducible checkpoint, including source revision, uncommitted changes, tests, assumptions, and authority. Define a verifiable **Return Contract** and provide the enabling agent a distilled context with references to relevant failures and decisions.

## 5. Verify and resume

Check enabling acceptance, compatibility, evidence freshness, integration authorization, and drift in source/contracts/schema/runtime/authority as relevant. Restore the parent context and resume only after its return conditions hold.

## 6. Failure is not an invitation for automatic rollback

Inventory side effects. Clean up only confirmed loop-owned, isolated, safely removable resources. Preserve or reconcile shared, irreversible, and production state until an authorized recovery plan is established.

## 7. Keep reporting proportional

For a local fix: **Result / Tests / Changes / Risks / Next Action**.

For a shift or high-risk transition: use [`templates/execution-report.md`](../templates/execution-report.md).

## Frequently confused terms

- **State vs. decision:** `FROZEN` is a state; `FREEZE` is the decision/event leading toward it.
- **Completed vs. deployed:** Completing a code task does not confer deployment authority.
- **Stack vs. graph:** The stack preserves nested execution context; the graph represents actual dependencies and parallelism.
- **Three retries:** Default per substantially similar repair hypothesis, not an absolute ban on new evidence-led approaches.
- **Context hygiene:** Distill relevant context; do not delete failed attempts and constraints needed for safe engineering.
