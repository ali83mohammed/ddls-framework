# Case Study 01 — A Hidden Infrastructure Dependency

**DDLS v2.1 | Synthetic educational scenario | Decisions:** `DIAGNOSE`, `FREEZE`, `SHIFT`, nested enablement, optional `PROMOTE`.

> This case is fictional. It contains no source code, measurements, host information, configuration, or incident findings from a private system. All outcomes below are **conditional walkthrough steps**, not reports of tests that actually ran.

## 1. Engineering context

A generic application runs both user-facing control tasks and long-running maintenance jobs. The team intends to add a time-sensitive control action that must remain responsive when maintenance work is busy.

The illustrative environment uses a shared background execution resource. The team initially assumes existing scheduling mechanisms are sufficient; that assumption is not yet proven.

## 2. Original objective and constraints

**Primary loop `L0: CONTROL-ACTION`**

- **Objective:** Implement the new control action with a documented responsiveness requirement under representative background load.
- **Acceptance:** A reproducible, authorized test demonstrates both correct results and the project's agreed responsiveness criterion under competing load.
- **Allowed:** Feature code, isolated tests, and agreed extension points.
- **Prohibited:** Unapproved infrastructure changes, access to production, bypassing tests, or modifying unrelated workload behavior.
- **Authority:** Development only. Integration approval and deployment authorization are separate.

At the outset, `L0` is `ACTIVE`.

## 3. Detected blocker

During hypothetical test design, the engineer finds that the proposed control action and maintenance work contend for the same executor capacity. There is no trustworthy measurement of where scheduling delay occurs.

A proposed feature-only retry or higher-priority flag cannot establish the acceptance criterion without understanding and controlling contention.

**Required qualification evidence (not supplied by this case):**

- An isolated reproduction test with both workload categories.
- A trace showing where queued and executing time is spent.
- The exact acceptance threshold specified by the host project.
- A check that the suspected resource is genuinely shared.

**Decision:** Classify as a *potential architectural/operational prerequisite*; `DIAGNOSE` first. Shift **only if the evidence confirms that an enabling capability is missing**.

## 4. Rejected alternatives

| Alternative | Why it is not enough |
|---|---|
| Add aggressive retries to `L0` | Can increase load without removing contention |
| Raise an arbitrary task priority | Does not prove resource isolation or service behavior |
| Add execution capacity without measurement | Changes the runtime and may hide rather than resolve the root cause |
| Declare the test flaky | Weakens the original acceptance contract |
| Modify live infrastructure to investigate | Outside the illustrative development authority |

These options are not universally invalid; the point is that none is authorized or supported by sufficient evidence in this scenario.

## 5. Dependency graph and planned shifts

If diagnosis verifies the missing capabilities, record:

```text
L0  CONTROL-ACTION
 └── HARD prerequisite → L1  ISOLATED-SCHEDULING
                              └── HARD prerequisite → L2  WORKLOAD-OBSERVABILITY
```

Here the arrow means **depends on**, not "executes before".

- Freeze `L0` with a recoverable checkpoint and a measurable return contract.
- Open `L1` to develop a bounded scheduling/isolation capability in an authorized test environment.
- If `L1` cannot be validated without instrumentation, qualify a **second blocker** and open `L2`.
- Complete and accept `L2`, then resume `L1`, then re-evaluate and resume `L0` in LIFO order.

A loop must never be spawned merely because the diagram anticipates it. Each dependency must be separately justified.

## 6. Checkpoint, ownership, and context package

Before leaving `L0`, capture an immutable source revision or safely retained patch, test definitions and existing outcomes, assumptions, resource restrictions, and the next permitted action. Check that the checkpoint is reconstructable.

The `L1` agent receives only the relevant control-action contract, the shared execution interface, the diagnosis, rejected approaches, and inherited constraints. The `L2` agent additionally receives the exact measurement requirements. Both must preserve references to negative evidence rather than deleting it.

## 7. Enabling contracts

The companion [contract file](../contracts/01-return-contracts.yaml) shows two distinct agreements:

- **`RC-OBS` (`L2 → L1`):** Instrumentation can distinguish queued time from execution time in an isolated test. No sensitive payloads or production measurements are collected.
- **`RC-SCHED` (`L1 → L0`):** Control and maintenance work use a defined, tested isolation mechanism; existing maintenance behavior is covered by regression tests.

Both contracts start with `NOT_EVALUATED`; no tool or human should mark them accepted on the strength of this text.

## 8. Integration and resume gates

The **illustrative safe path** is:

1. Execute the agreed `L2` tests; attach evidence tied to a tested revision.
2. Accept and integrate `L2` only with integration authority.
3. Revalidate `L1` assumptions, then test and integrate its scheduling changes.
4. Before resuming `L0`, inspect source, contract, configuration, and authority drift.
5. Run the representative control/maintenance integration test against the agreed criterion.
6. Report development acceptance and deployment authorization **separately**.

No performance number or acceptance result is asserted here.

## 9. Failure and architectural promotion

**Failure path:** If instrumentation disproves the original contention hypothesis, use `INVALIDATE / REPLAN`; do not automatically build isolation work. If `L1` grows to require a broad scheduler replacement, stop the enabling expansion and consider `PROMOTE` with a new architecture review.

**Recovery:** Inventory artifacts, ownership, and side effects before cleanup. Do not tear down shared state or modify production.

**Conditional outcome:** `L0` returns to `ACTIVE` only after its return contract, permitted integration, and drift checks succeed. Otherwise the correct outcome remains `FROZEN` or `ESCALATED`.

## 10. Lessons learned

- The first useful DDLS action may be `DIAGNOSE`, not `SHIFT`.
- A bounded parent feature can reveal nested enabling work.
- An enabling loop may need to become a separate architecture initiative.
- A completed subtask does not imply an accepted parent or an approved rollout.
- Publishing a case study does not constitute test evidence.

**Practice question:** What observation would falsify the shared-executor hypothesis? If it does, which return contracts must be invalidated?