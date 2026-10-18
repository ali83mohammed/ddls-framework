# Case Study 03 — The Blocker That Did Not Require a Shift

**DDLS v2.2 | Synthetic educational scenario | Decisions:** `DIAGNOSE`, `WAIT`, optionally `FIX`, then `CONTINUE`.

> This is a fictional, privacy-preserving teaching case. It contains no device addresses, vendor-specific privilege strings, credentials, customer information, configuration exports, or actual operational logs.

## DDLS v2.2 governance and budget

**Mode:** Start in `TRANSPARENT` for code diagnosis and authorized read-only tests: no return contract, child task, or YAML is required. The [companion synthetic decision record](../contracts/03-diagnostic-decision.yaml) illustrates `WAIT` for an external operator and explicitly records `NO_SHIFT`. **No child budget is allocated**, and no access-changing permission is implied.

If the task later requires sensitive operations, independently move to `GOVERNED` and seek actual authority; do not upgrade the operation through paperwork.

## 1. Engineering context

A developer adds a scheduled snapshot task for a **generic managed endpoint**. In an isolated test fixture, the snapshot operation succeeds. A separately authorized read-only capability probe against a managed test endpoint returns an access-denied result.

An AI agent proposes implementing a new transport client or replacing the snapshot subsystem.

## 2. Original objective

**Primary loop `L0: SNAPSHOT-JOB`**

- **Objective:** Schedule snapshots using an existing, supported interface.
- **Acceptance:** Correct job execution in an authorized test environment and a clear, non-destructive failure when the endpoint's capabilities are insufficient.
- **Allowed:** Source changes and isolated test fixtures.
- **Not allowed:** Broadening endpoint privileges, altering access policy, using privileged credentials, or modifying production endpoints.

## 3. Diagnose before shifting

The engineer requests evidence to distinguish a code defect from an external capability constraint:

1. Does the same function pass against a known authorized fixture?
2. Does the endpoint return a clear authorization failure rather than a transport/protocol error?
3. Is the required capability documented as operator-managed?
4. Does the task contract grant the agent authority to change that external role? (In this case, **no**.)

The fixture result alone does not prove all code paths are correct. Together with the authorized probe, it is sufficient **in this fictional scenario** to route the issue to external authorization review instead of inventing a new subsystem.

No real probe was made while preparing this document.

## 4. DDLS decision: no SHIFT

Choose:

```text
ACTIVE → DIAGNOSE
       → WAITING_EXTERNAL (operator capability decision)
       → re-evaluate when the authorized operator responds
       → CONTINUE within L0, if the capability is present and tests pass
```

An operator may decide that additional access is inappropriate. In that case the result remains a documented limitation, and the original acceptance criteria may need authorized replanning.

**No Enabling Loop is created.** The parent work is not silently expanded to include endpoint security administration.

## 5. Why tempting alternatives fail

| Proposed action | Assessment |
|---|---|
| Write a new snapshot engine | Unjustified until the existing path is shown inadequate |
| Retry the denied operation indefinitely | Evidence already identifies an authorization boundary |
| Elevate access automatically | Not in the agent's authority |
| Suppress the error and report success | Misrepresents acceptance |
| Publish a raw access log as proof | May disclose internal information |
| Keep development suspended without a recheck condition | Creates an unmanaged external wait |

## 6. Diagnostic decision record

The [companion decision record](../contracts/03-diagnostic-decision.yaml) captures:

- `shift_performed: false`.
- The suspected blocker and illustrative (not real) evidence references.
- The current authorization boundary.
- The owner of the external decision.
- A recheck condition.
- The next permitted read-only verification.

The record is not a substitute for an operator's approval or proof that an access change occurred.

## 7. Validation after the external decision

Only after an authorized operator reports completion, the engineer may:

1. Verify capability with an explicitly permitted, non-destructive probe.
2. Run the snapshot behavior test in an appropriate environment.
3. Recheck source, interface, and authority changes.
4. Resume `L0` only if the original conditions are satisfied.

If the operator declines, choose `REPLAN`, `ESCALATE`, or `CANCEL` depending on the project's accepted objective. Never interpret silence as permission.

## 8. Recovery and side effects

No privileged operation is executed by the agent. If development experiments created isolated temporary fixtures, clean them only when ownership and safety are confirmed. No automatic rollback of shared state is implied.

## 9. Illustrative outcome

The expected **decision** is correct classification and a bounded external wait, not a completed snapshot in a real environment. There are no actual test results in this example.

## 10. Lessons learned

- An operational dependency can be real without requiring new code.
- The boundary between code capability and operator authority matters.
- `DIAGNOSE` and `WAIT` may be more valuable than `SHIFT`.
- A clear, correct failure is often better than an unauthorized workaround.
- Rechecks must establish facts; they do not replace authorization.

**Practice question:** If the authorized endpoint probe succeeds but snapshots still fail, what new evidence would justify changing `WAIT` to `FIX` or `SHIFT`?