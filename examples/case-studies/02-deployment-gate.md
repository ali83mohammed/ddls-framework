# Case Study 02 — Development Complete, Deployment Blocked

**DDLS v2.1 | Synthetic educational scenario | Decisions:** `VALIDATE`, `STOP`, `ESCALATE`, `WAIT`.

> Fictional systems, records, and decision outcomes. This case is not a report of a particular deployment or restore incident; it provides no real source, secrets, lifecycle identifiers, environment values, or observed test results.

## 1. Engineering context

A team has developed a generic service-update workflow. Its tests and local acceptance belong to **development**. Running it against an existing deployment would alter operational state and requires independent authority and compatibility evidence.

The deployment target's current lifecycle state has not been verified against the new update procedure.

## 2. Original objective and scope

**Development loop `L0: UPDATE-WORKFLOW`**

- **Objective:** Implement and test a workflow for updating a service without assuming the target's state.
- **Acceptance:** Authorized, isolated tests demonstrate correct state preflight, compatible transitions, and safe refusal when the target state is unsupported.
- **Allowed:** Code, non-production fixtures, and test documents.
- **Not allowed:** Real deployment, migration, restore, state-reset, or network modifications.

**Separate rollout work item `R0: AUTHORIZE-ROLLOUT`**

Its scope is to verify production eligibility and obtain permission. It does not inherit authority from `L0`.

## 3. Detection and evidence requirements

The rollout proposal encounters two missing inputs:

1. A trustworthy assertion that the target's current lifecycle state is supported by the new procedure.
2. An explicit authorization for that deployment operation and environment.

Even if a synthetic exercise **assumes** that `L0`'s local tests pass, it does not follow that `R0` may proceed. The example's record intentionally leaves all real evidence as `PENDING`.

The correct question is **"Is an enabling capability missing, or is this an unresolved operational gate?"**

## 4. Decision

- The development work may reach `COMPLETED` only if its own acceptance evidence exists; it may independently be `TESTED` or `INTEGRATED` under separate integration authority.
- The rollout work item remains `WAITING_EXTERNAL` or `ESCALATED` until its compatibility and authorization gates pass.
- Record `STOP` for any attempt to execute production changes while the gate is unsatisfied.
- **Do not create a new enabling loop just to work around a missing approval.**

If a genuine missing compatibility capability is subsequently demonstrated, qualify that *new* blocker separately and consider a bounded `SHIFT`.

## 5. Why alternatives are rejected

| Tempting shortcut | DDLS assessment |
|---|---|
| Treat successful unit tests as rollout approval | Tests are evidence, not authorization |
| Rewrite target lifecycle metadata to look compatible | May corrupt state and defeats preflight |
| Reuse another environment's permission | Authority is scoped to a specific action and environment |
| Bypass preflight to keep a release schedule | Weakens the agreed safety boundary |
| Automatically roll back a target in an unknown state | Recovery needs its own evidence and authority |

## 6. Gate relationships

```text
L0  UPDATE-WORKFLOW       development acceptance (independent)
        |
        | candidate output
        v
R0  AUTHORIZE-ROLLOUT    WAITING_EXTERNAL / ESCALATED
        ├── prerequisite: target lifecycle compatibility evidence
        └── prerequisite: deployment approval
                         |
                         v
             deployment action (NOT AUTHORIZED)
```

This is a **gate dependency**, not necessarily an Enabling Loop / LIFO scenario.

## 7. Authorization contract

The [companion gate record](../contracts/02-authorization-gate.yaml) tracks development, integration, deployment, and operational authorities separately. It starts with `deployment: NOT_GRANTED` and `readiness: PENDING`.

The rollout can become eligible only after authorized checks verify:

- Target identity, version, and current state by permitted means.
- Supported transition path and an applicable recovery strategy.
- Compatible source and deployment artifacts.
- Explicit approval for the exact target and operation.
- Acceptable freshness of all supporting evidence.

No gate is satisfied by documentation alone.

## 8. Safe stop and external wait

The agent must not attempt the operation. It records the blocker and target action category, without recording credentials or sensitive environment details. It requests a decision from the authorized operator and defines a recheck trigger.

If an operation may already have started, first establish its actual state. Do not assume that cancellation or rollback happened.

## 9. Outcome and recovery

**Illustrative outcome:** Development can be finished **conditionally on its own tests** while rollout remains blocked. The simulated `R0` state is `WAITING_EXTERNAL`; deployment is **not** `DEPLOYED`.

If the target lifecycle turns out to be unsupported, the operator can choose a revised deployment method, defer the release, or cancel the rollout. This is a `REPLAN` decision, not authorization to invent a recovery procedure.

## 10. Lessons learned

- `COMPLETED` for development and `DEPLOYED` are distinct statuses.
- A lack of permission is not a missing software capability.
- `STOP` can be the **successful** DDLS safety decision.
- The agent must not manufacture approvals or production compatibility evidence.
- Existing state is a fact to verify, not something to normalize by force.

**Practice question:** What new evidence would justify a genuine enabling loop rather than continuing to wait for authorization?