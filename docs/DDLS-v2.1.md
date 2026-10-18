# DDLS v2.1 — Dependency-Driven Loop Shifting

## An Engineering Playbook for Dependency Management and Development Continuity with AI

**Engineering Operations Playbook — Version 2.1**

- **Concept and framework author:** Ali Mohammed
- **Release:** 2.1 — Agent Reliability & Execution Safety
- **Year:** 2026
- **License:** [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — see [LICENSE](../LICENSE) and [ATTRIBUTION](../ATTRIBUTION.md)
- **Discipline:** Software Engineering / AI-Assisted Development
- **Intended audience:** Software engineers, software architects, engineering leads, and users of AI coding agents

---

## 1. Definition and Engineering Philosophy

### 1.1 What is DDLS?

**Dependency-Driven Loop Shifting (DDLS)** is an engineering workflow for managing unexpected dependencies discovered during software development that prevent a task from being completed correctly or safely.

Rather than forcing a task to completion through uncontrolled workarounds, DDLS follows this approach:

1. Detect and qualify the missing dependency.
2. Preserve the current work state and original objective.
3. Select an appropriate strategy for resolving the dependency.
4. Execute enabling work within an independently bounded scope.
5. Test the outcome and verify compatibility.
6. Restore the context of the original task.
7. Resume development once the return conditions are satisfied.

The core sequence is:

**Freeze → Shift → Enable → Validate → Integrate → Resume**

This sequence does **not** imply that every problem requires a new loop. The correct decision may be a direct fix, an external wait, replanning, or termination.

### 1.2 The problem DDLS addresses

During software development—particularly with AI coding agents—engineers may encounter:

- A missing foundational service.
- An unplanned architectural prerequisite.
- A circular dependency between components.
- Missing permissions or system capabilities.
- A data model that cannot support a new requirement.
- Loss of context after a long sequence of attempts.
- Repeated, unsuccessful agent-generated fixes.
- A repository that changes while a task is suspended.
- Conflicting work performed by multiple agents.
- A completed enabling loop whose original parent remains blocked.

DDLS provides a disciplined response to these conditions without losing the original objective or control over the system.

### 1.3 Prior art and engineering positioning

DDLS draws on established concepts, including:

- **The Mikado Method:** Discovering and tracing dependencies during refactoring.
- **Double-Loop TDD:** Separating levels of development, testing, and verification.
- **Dependency graphs:** Expressing relationships among requirements and components.
- **Call stacks and context switching:** Preserving and restoring execution context, by analogy.
- **Architecture Decision Records:** Recording significant engineering decisions and their rationale.
- **Risk-based change management:** Matching change authority to risk.

DDLS does not claim to have invented these concepts or to replace them. Its proposed contribution is to combine them into an **operational protocol for work transitions caused by unexpected dependencies**, with return contracts, recoverable context, and explicit authorization boundaries.

It may be applied manually or through AI agents; a dedicated platform is not required. The call-stack analogy describes nested work context, not literal CPU scheduling, and Double-Loop TDD serves as a comparison rather than an equivalent dependency-management method.

### 1.4 Framework objectives

DDLS aims to:

1. Protect architectural integrity during development.
2. Preserve continuity across long-running tasks.
3. Reduce context loss and unnecessary rework.
4. Prevent uncontrolled task-scope expansion.
5. Manage nested, parallel, shared, and circular dependencies.
6. Improve work recovery after failures.
7. Separate development completion from integration and deployment authority.
8. Keep AI agents within clearly defined execution boundaries.
9. Reduce human administrative overhead through agent-generated records.
10. Make engineering decisions traceable and reviewable.

---

## 2. Governing Principles and Mandatory Rules

### Rule 1 — Preserve Original Intent

Every development task must have a clear objective and explicit acceptance criteria. Discovering a new dependency does not authorize changing or silently replacing that objective. Material changes require a recorded decision by an authorized owner.

### Rule 2 — Evidence Before Shift

Implementation difficulty is not automatically a missing dependency. Before creating an enabling loop, establish:

- What capability or prerequisite is missing.
- What evidence establishes that it is missing or invalid.
- How that deficiency blocks task acceptance.
- Why it cannot be addressed safely within the current scope.
- What deliverable would remove the blocker.

If the evidence is insufficient, **diagnose first; do not shift prematurely**.

### Rule 3 — No Uncontrolled Workarounds

Do not obtain superficial completion by disabling failing tests, reducing security requirements, bypassing authorization, introducing undocumented behavior, duplicating shared logic without justification, ignoring incompatibility, or adding an unowned temporary solution.

An interim solution is permissible only when explicitly authorized, bounded, observable, and associated with an owner and removal conditions.

### Rule 4 — Bounded Execution

Each loop must define its **objective, scope, constraints, acceptance criteria, authority, retry budget, and stop conditions**. An AI agent must not expand those boundaries on its own.

### Rule 5 — Evidence-Aware Retry Budget

The recommended default is **three substantially similar repair attempts per hypothesis**. Rewording the same attempted fix does not reset the budget.

When the budget is exhausted, the agent must diagnose the root cause and reassess the hypothesis, then stop or escalate if no safe, authorized path remains. A materially new piece of evidence may justify a different plan, subject to the overall resource budget. A critical safety or authorization violation requires an immediate stop, regardless of remaining retries.

### Rule 6 — Reliable State Preservation

Never suspend a development loop without preserving sufficient information to reconstruct it: source state, unmerged changes, decisions, tests, constraints, and the return contract. Conversation memory alone is not a reliable checkpoint.

### Rule 7 — Context Distillation, Not Context Deletion

Provide an enabling agent with a focused working context. Omit irrelevant conversational repetition while retaining relevant evidence, failed approaches, decisions, constraints, and retrievable references to the full record.

### Rule 8 — Minimum Sufficient Enablement

An enabling loop must deliver the smallest sustainable capability that satisfies its return contract. Minimal scope never justifies skipping security controls, tests, or compatibility requirements. Unrelated improvements belong in a backlog.

### Rule 9 — Validate Before Resume

An enabling output must be tested and shown to satisfy the parent's return conditions. Unit tests alone are insufficient where integration or compatibility testing is required.

### Rule 10 — Separate Environment Authorities

**Development, integration, deployment, and sensitive operational authorities are independent.** Permission to edit source does not imply permission to merge a protected branch, run a migration, modify production containers or networks, restore data, rotate keys, delete data, or issue sensitive SSH/CLI/API commands. Every action must remain within its explicit authorization.

### Rule 11 — Safe Recovery Over Automatic Rollback

Inventory and classify side effects before removing them. Never automatically roll back shared, production, or otherwise non-safely-reversible state.

### Rule 12 — Controlled Parallelism

Independent loops may execute concurrently only when dependencies, resources, contracts, isolation, and authorization allow it. Prevent contention over shared files, state, locks, services, and data.

### Rule 13 — Human Authority Preservation

An agent may recommend decisions and execute authorized work. High-impact architecture decisions, authority expansion, and sensitive production changes remain subject to an authorized human decision unless explicit preauthorization covers the action. Silence is not approval.

### Rule 14 — Stopping Is a Valid Outcome

When evidence or safe authorization is insufficient, stop and report the precise blocker. Apparent task completion must not take precedence over system safety.

---

## 3. Terminology and Operational Model

### 3.1 Primary Loop — L0

The original development task, such as `L0 = Implement Backup Engine`.

### 3.2 Enabling Loop — Le

A bounded work loop created to supply a missing prerequisite needed by another loop, such as `L1 = Implement Package Integrity Verification`.

### 3.3 Hard Blocker

An evidenced prerequisite that prevents satisfaction of a mandatory acceptance condition, or makes further execution violate a mandatory constraint.

### 3.4 Shift Point

The controlled transition from an active task toward a strategy for resolving a missing prerequisite.

### 3.5 Return Contract

A specification of the enabling output, required acceptance evidence, compatibility requirements, and conditions under which the parent may resume.

### 3.6 Checkpoint

A recorded, reconstructable state containing source changes, work context, tests, decisions, and constraints.

### 3.7 Dependency Graph

A directed representation of prerequisites between loops, capabilities, and components.

### 3.8 Loop Stack

A mechanism for managing nested execution context and the order in which suspended work is resumed.

### 3.9 Environment Gate

A check of authorization and operational prerequisites before an action in a given environment.

### 3.10 Evidence Artifact

A verifiable item such as a test result, error log, commit, or integration report.

### 3.11 Drift

A material change to source, contracts, database schema, runtime state, permissions, or evidence since the last validated checkpoint.

### 3.12 Loop Owner

The engineer or authorized agent responsible for a loop's execution state within specified authority.

---

## 4. Starting a Development Task with DDLS

### Step 1 — Define the Primary Loop

Define the task objective, permitted and prohibited scope, acceptance criteria, retry policy, and authorities before beginning.

```yaml
ddls_version: "2.1"
loop:
  id: "BACKUP-V2"
  role: "PRIMARY"
  objective: "Implement incremental backup"
scope:
  allowed:
    - "backup service"
    - "backup tests"
    - "required interfaces"
  prohibited:
    - "production deployment"
    - "network configuration changes"
    - "unrelated refactoring"
acceptance:
  - "Incremental backup succeeds"
  - "Restore compatibility verified"
  - "Existing regression tests pass"
retry_policy:
  similar_attempts_per_hypothesis: 3
authority:
  development: "GRANTED"
  integration: "APPROVAL_REQUIRED"
  deployment: "NOT_GRANTED"
  operational_actions: "NOT_GRANTED"
```

A separate YAML file is not necessary for every small task. A concise written contract is acceptable when risk is low.

### Step 2 — Execute

Proceed normally. Fix local defects within the current loop. Do not use DDLS as a reason to suspend work for every failed test or missing file.

### Step 3 — Detect and Classify

| Detected condition | Default decision |
|---|---|
| Local implementation defect | `FIX` |
| Minor gap within authorized scope | `CONTINUE` |
| Unknown root cause | `DIAGNOSE` |
| Verified architectural prerequisite | `SHIFT` |
| Multiple independent prerequisites | `PARALLELIZE` |
| Circular prerequisite | `REPLAN` |
| External prerequisite | `WAIT` |
| Material change to the objective | `ESCALATE` |
| Action outside authority | `STOP` |
| Invalid foundational assumption | `INVALIDATE` |
| Enabling work exceeds its approved scope | `PROMOTE` |

These are defaults, not unconditional commands: assess evidence, risk, and authority first.

### Step 4 — Freeze

When a shift is warranted:

1. Stop changes affecting the parent loop.
2. Record the source revision.
3. Preserve unmerged changes.
4. Record passing and failing tests.
5. Document the blocker.
6. Establish a return contract.
7. Verify that the checkpoint can reconstruct the work.

A dedicated Git branch, commit, or safely stored patch may be used. Never run destructive Git commands merely to obtain a clean worktree.

### Step 5 — Shift

Create a bounded enabling loop connected to its parent, with its own objective, scope, and return contract.

**Context-window hygiene:** Pass the enabling agent the new loop contract, return contract, applicable inherited constraints, directly relevant interfaces and files, pertinent diagnostic results, significant failed attempts, and verifiable evidence. Do not blindly transfer a long, irrelevant conversation history; do not erase knowledge necessary to avoid repeating mistakes.

### Step 6 — Validate and Integrate

Before accepting the enabling work:

1. Run the required tests.
2. Evaluate the return contract.
3. Review compatibility.
4. Verify compliance with constraints.
5. Run the appropriate integration tests.
6. Confirm evidence freshness.
7. Obtain integration approval where required.

Acceptance of an enabling loop does **not** confer production deployment authority.

### Step 7 — Resume

Before resuming the parent:

1. Restore the checkpoint.
2. Verify the source revision.
3. Check source-code drift.
4. Check contract and schema drift where applicable.
5. Check runtime drift for operational work.
6. Merge or rebase changes only when appropriate and authorized.
7. Revalidate affected assumptions.
8. Verify return-contract conditions.
9. Resume work.

If drift reveals a material conflict, resolve it or replan before editing further.

---

## 5. Dependency Graph and Loop Stack

DDLS uses two distinct models.

**Dependency Graph:** Captures what depends on what.

```text
       L0
      /  \
     L1  L2
      \  /
       L3
```

Here L0 depends on L1 and L2; both L1 and L2 depend on L3. An edge `A → B` means **A requires B**. The graph may initially contain cycles, which must be detected and resolved before treating affected prerequisite relationships as an executable DAG.

**Loop Stack:** Preserves suspended context in a sequence of nested dependencies.

```text
L0 → L1 → L2

Complete L2
Resume L1
Complete L1
Resume L0
```

**Key distinction:** The graph expresses dependency topology; the stack expresses nested context and return order. LIFO cannot represent every shared or parallel relationship.

---

## 6. Managing Dependency Types

### 6.1 Linear dependencies

`L0 → L1`: Use **FREEZE → SHIFT → VALIDATE → INTEGRATE → RESUME** when L1 provides a mandatory prerequisite for L0.

### 6.2 Nested dependencies

`L0 → L1 → L2`: Use LIFO where each loop requires the next one's output. The recommended default is a maximum nesting depth of **three loops including the primary loop**. Reaching the threshold triggers review—not automatic cancellation. Additional depth requires an explicit plan and approved budget.

### 6.3 Parallel dependencies

```text
      L0
     /  \
    L1  L2
     \  /
  Integration
```

L1 and L2 may run in parallel when:

- No mandatory dependency path orders one before the other.
- Their prerequisite subgraph has a valid directed acyclic ordering (DAG).
- Shared-state and lock contention are absent or safely coordinated.
- File and resource ownership is defined.
- Shared contracts are stable or versioned.
- Isolated workspaces are available.
- Authority and resource budgets permit concurrency.

Always run a joint integration check. **Being nodes in a DAG does not, by itself, establish safe parallelism.**

### 6.4 Circular dependencies

For `A → B → A`, stop spawning deeper loops. Verify that the cycle is real rather than a modelling error; identify the conflicting components and contracts; consider interface extraction, responsibility separation, or redesign; update the dependency graph; and resume only when an executable resolution exists. Escalate if none is safe.

### 6.5 Shared dependencies

If multiple parents need the same capability, prefer a single shared enabling implementation rather than duplicate ones. Maintain **separate return acceptance checks per consumer**: compatibility with one parent does not guarantee compatibility with another.

### 6.6 External dependencies

Move the loop into `WAITING_EXTERNAL` and record the awaited condition, responsible party, review trigger, and permitted alternatives. Do not pretend an external integration succeeded by substituting a mock for real acceptance evidence.

### 6.7 Enabling-loop scope expansion

When enabling work grows beyond approved scope, consider reducing or splitting it, revising the architecture, promoting it into an independent initiative (`PROMOTE`), deferring it, or cancelling it. Keep or explicitly replan the parent; do not hide a new architecture project inside a small enabling loop.

### 6.8 Assumption invalidation

Use `INVALIDATE` if a premise behind the blocker or proposed design proves false. Identify the invalid assumption, dependent decisions, invalidated tests and evidence, affected loops, and required revalidation. Do not continue on a disproven premise.

---

## 7. States, Decisions, and Transitions

Distinguish **work state** from **execution decision**.

### 7.1 Loop states

| State | Meaning |
|---|---|
| `PLANNED` | Registered but not started |
| `ACTIVE` | Work is in progress |
| `BLOCKED` | A dependency prevents progress |
| `FROZEN` | Checkpointed and suspended |
| `WAITING_EXTERNAL` | Awaiting an external condition |
| `VALIDATING` | Results are being checked |
| `READY_TO_RESUME` | Return conditions have been satisfied |
| `ESCALATED` | Awaiting an authorized decision |
| `INVALIDATED` | A foundational assumption is no longer valid |
| `COMPLETED` | Acceptance criteria have been satisfied |
| `CANCELLED` | Intentionally terminated |

An enabling loop is a **role**, not a lifecycle state: it may itself be `ACTIVE`, `VALIDATING`, or `COMPLETED`. When a suspended parent resumes, it returns to `ACTIVE` after passing the resume gate.

### 7.2 Delivery states

Track code delivery separately from loop state:

- `NOT_SUBMITTED`
- `TESTED`
- `READY_TO_INTEGRATE`
- `INTEGRATED`
- `DEPLOYED`

A loop may be development-complete even when its output has not been deployed.

### 7.3 Decision tokens

| Token | Action |
|---|---|
| `CONTINUE` | Continue in the current loop |
| `FIX` | Repair a local issue |
| `DIAGNOSE` | Collect more evidence |
| `FREEZE` | Preserve and suspend work |
| `SHIFT` | Create an enabling loop |
| `PARALLELIZE` | Execute independent work concurrently |
| `WAIT` | Await an external condition |
| `PROMOTE` | Turn enabling work into an independent initiative |
| `REPLAN` | Change the plan or architecture |
| `VALIDATE` | Check acceptance conditions |
| `INTEGRATE` | Integrate authorized outputs |
| `RESUME` | Resume suspended work |
| `INVALIDATE` | Revoke the validity of an assumption or result |
| `ESCALATE` | Request a higher-authority decision |
| `STOP` | Stop actions affecting the system |
| `CANCEL` | Terminate with controlled reconciliation |
| `COMPLETE` | Close the task after acceptance |

Each requested transition must be checked against the current state, authorization, and prerequisites.

### 7.4 Transition integrity

Automated DDLS implementations should:

- Persist transition records durably.
- Make retries idempotent where possible; guard non-idempotent side effects.
- Reject stale-state transitions when the underlying state has changed.
- Assign unique operation IDs to sensitive transitions.
- Record partial failure before retrying.
- Never infer success without verification.

These safeguards are especially important in multi-agent or concurrent systems.

---

## 8. Retry Budget and Diagnostic Policy

### 8.1 What counts as an attempt?

A repair attempt is a change or remedial action intended to test a particular root-cause hypothesis, followed by suitable validation. Merely rerunning a test need not count as a *new repair attempt*, but it still consumes time and resource budgets.

### 8.2 Default policy

```yaml
retry_policy:
  max_similar_attempts_per_hypothesis: 3
  require_validation_after_attempt: true
  reset_requires_material_evidence: true
  critical_violation_action: STOP
  exhausted_action: DIAGNOSE
```

### 8.3 What constitutes material new evidence?

Examples include a new stack trace identifying a different failure layer, an isolated test disproving the previous hypothesis, documented version incompatibility, evidence locating the defect in another service, or an overlooked runtime prerequisite.

Renaming a variable or rewriting essentially the same attempted fix does **not** count as new evidence.

### 8.4 Preventing infinite attempts

Where appropriate, also cap diagnostic time, tool calls, compute budget, file changes, and reopening of the same blocker. When measurable progress stops, escalate or replan rather than experimenting indefinitely.

---

## 9. Checkpoints and Context Management

### 9.1 Minimum checkpoint contents

```yaml
checkpoint:
  loop_id: "BACKUP-V2"
  source_revision: "<commit-sha>"
  working_tree: "CLEAN_OR_CAPTURED"
  implementation_status:
    completed: []
    pending: []
  evidence:
    passing_tests: []
    failing_tests: []
    failed_approaches: []
  constraints: []
  decisions: []
  dependencies: []
  parent_return_contract: "<reference>"
  environment:
    schema_version: "<if-applicable>"
    runtime_revision: "<if-applicable>"
```

Never embed passwords, private keys, or other secrets in checkpoints.

### 9.2 Context distillation

When handing work between agents, create a concise, reference-backed **Context Package** containing the objective, acceptance criteria, restrictions, sources of truth, significant decisions, relevant negative evidence, required files, current state, and next authorized action. A summary must not delete facts needed to reconstruct a decision.

### 9.3 Drift checks before resumption

- **Source drift:** Relevant files or interfaces have changed.
- **Contract drift:** A relied-upon interface or agreement has changed.
- **Schema drift:** The data schema or migration state has changed.
- **Runtime drift:** Service versions or configuration have changed.
- **Authority drift:** Permissions have expired, changed, or been revoked.
- **Evidence drift:** Prior tests no longer represent the current source or environment.

Material drift requires revalidation before execution resumes. Do not automatically perform a potentially disruptive rebase or merge.

---

## 10. Return Contract

Do not close an enabling dependency solely because an agent announces success. Acceptance must be evidence-backed.

```yaml
return_contract:
  id: "RC-001"
  parent_loop: "BACKUP-V2"
  enabling_loop: "PACKAGE-VERIFY"
  required_capability:
    description: "Verify package integrity"
    interface: "PackageVerificationService"
  acceptance:
    - "Valid packages accepted"
    - "Tampered packages rejected"
    - "Invalid signatures rejected"
  compatibility:
    - "Existing backup format preserved"
  prohibited_changes:
    - "No production mutation"
    - "No security bypass"
  evidence:
    - "test report"
    - "source revision"
    - "integration verification"
  authorization:
    integration: "APPROVAL_REQUIRED"
    deployment: "NOT_GRANTED"
  resume_conditions:
    - "Capability accepted"
    - "Required integration complete"
    - "Parent checkpoint restored"
    - "Relevant drift checks passed"
  invalidation_triggers:
    - "Interface incompatibility"
    - "Failed regression"
    - "Changed security assumptions"
```

**Return-contract rules:**

1. Conditions must be specific and verifiable.
2. Conditions must not be silently weakened.
3. Material amendments require a recorded decision.
4. Every consumer of a shared capability has its own acceptance obligations.
5. Evidence must identify the tested code and environment versions.
6. Stale or invalidated evidence requires revalidation.

---

## 11. Safe Recovery and Side-Effect Reconciliation

A failed or cancelled loop must not assume all changes are safely reversible.

### 11.1 Side-effect classification

| Side-effect type | Default strategy |
|---|---|
| Local, loop-owned, safely removable | `CLEAN_TEARDOWN` |
| Proven safely reversible | `CONTROLLED_ROLLBACK` |
| Requires an inverse business/operational action | `COMPENSATION` |
| Shared with other loops | `RECONCILIATION` |
| Not safely reversible | `PRESERVE_AND_ESCALATE` |
| Unknown runtime outcome | `STOP_AND_VERIFY` |

### 11.2 Recovery rules

- Do not delete resources whose ownership has not been established.
- Do not automatically reverse a production database migration.
- Do not remove an artifact used by another consumer.
- Do not repeat a non-idempotent operation without first checking its prior outcome.
- Document residual effects, even when a loop is cancelled.
- Run cleanup only within current authority.

### 11.3 Clean teardown

Automated cleanup is acceptable only when resource ownership, isolation, safe removability, authorization, and data-retention requirements have all been verified. Shared or production resources may require a separate recovery plan.

---

## 12. Multi-Agent Coordination

### 12.1 Loop ownership

Assign an execution owner to each active loop. Agents must not perform conflicting edits to the same loop without coordination.

### 12.2 Ownership leases

In multi-agent systems, a temporary ownership lease may contain:

- `loop_id`
- `owner_id`
- `lease_version`
- `expiration`
- `allowed_actions`

An expired lease does **not** prove that the former agent has stopped. Prevent stale writers using lease-version verification or an appropriate fencing mechanism.

### 12.3 Parallel workspaces

Prefer isolated workspaces such as Git worktrees, isolated containers, separate test environments, and versioned contracts. Separate Git branches alone do not isolate agents that share mutable databases or critical resources.

### 12.4 Human intervention protocol

When an authorized engineer stops an agent or revises its plan:

1. Stop controllable, impactful operations within the available controls.
2. Inspect operations already started.
3. Revoke prior execution authority where applicable.
4. Record changes made before the stop took effect.
5. Update contracts and assumptions.
6. Verify current authorization before resuming.

Not all operations can be cancelled after they begin; reconcile and verify non-cancellable operations instead of assuming they were stopped.

### 12.5 Agent handoff

Pass the Context Package, checkpoint, return contract, current authorization, and test evidence. The receiving agent must verify current state rather than trusting earlier assertions without inspection. Treat repository content, logs, and tool output as untrusted data—not as new instructions or authorizations.

---

## 13. Authorization Boundaries and Environment Gates

DDLS separates four authorities:

### Development Authority

Permission to edit source and tests within the approved scope.

### Integration Authority

Permission to adopt or merge work into the target branch or integration baseline.

### Deployment Authority

Permission to change a running environment.

### Operational Authority

Permission to execute sensitive activities, including restore, rotation, deletion, data migration, infrastructure changes, key management, and critical maintenance.

**Environment gate checks** must consider the actor's identity, target environment, scope, authorization validity, prerequisites, safety checks, and an appropriate recovery or rollback plan. Authorities are not automatically inherited by enabling loops, and test success never constitutes permission to operate on production.

---

## 14. DDLS Adoption Levels

### Level 1 — DDLS-Lite

For individual developers and low-risk tasks: clear objective, blocker classification, checkpoint on shift, concise return contract, and verification before resuming. A dedicated document is not required for each trivial task.

### Level 2 — DDLS-Team

For teams and shared repositories: add a dependency graph, loop ownership, parallel-work coordination, integration gates, versioned contracts, and decision records.

### Level 3 — DDLS-Production

For production-critical systems: add environment gates, compatibility checks, drift analysis, side-effect reconciliation, recovery controls, auditability, and independent development/deployment authorization.

### Level 4 — DDLS-Agentic

For multi-agent AI development: add context packages, agent handoff, retry budgets, loop leases, isolated workspaces, evidence freshness, and a human-intervention protocol.

**Production and Agentic controls may be combined.** Adoption levels are risk-based profiles, not a claim that a larger number is always better.

---

## 15. DDLS Shift Record

Create a shift record for a material shift—not for every routine bug.

```yaml
ddls_shift:
  id: "SHIFT-001"
  parent_loop: "BACKUP-V2"
  enabling_loop: "PACKAGE-VERIFY"
  blocker:
    category: "CAPABILITY"
    description: "..."
    evidence: "..."
    impact: "..."
  decision:
    action: "SHIFT"
    reason: "..."
    alternatives_considered: []
  checkpoint:
    source_revision: "<commit-sha>"
    reference: "<checkpoint-location>"
  return_contract: "RC-001"
  execution:
    owner: "..."
    max_similar_retries: 3
    scope: []
  authority:
    development: "GRANTED"
    integration: "APPROVAL_REQUIRED"
    deployment: "NOT_GRANTED"
  status: "ACTIVE"
```

Agents should generate this record automatically from available evidence. Humans intervene primarily for decisions requiring their authority.

---

## 16. Standard Execution Report

Use this report for material work transitions:

```text
DDLS EXECUTION REPORT

Primary Loop:
Current Loop:
Loop State:

Objective:
Blocker:
Evidence:
Classification:

Decision:
Decision Reason:

Source Revision:
Checkpoint Reference:
Dependency Changes:

Retry Attempts:
Failed Hypotheses:
New Evidence:

Return Contract:
Acceptance Results:
Integration Results:
Drift Check:

Side Effects:
Recovery Status:

Development Authority:
Integration Authority:
Deployment Authority:
Operational Authority:

Unresolved Risks:
Next Permitted Action:
```

For a small task, use the lighter **Result / Tests / Changes / Risks / Next Action** report. Reporting overhead should be proportional to engineering risk.

---

## 17. DDLS Agent Contract — Operational Prompt

The following contract can be used with Codex or another coding agent. Set the task-specific placeholders for each assignment.

```text
You are operating under the
DDLS v2.1 Engineering Workflow.

Your responsibility is to complete the
authorized development objective while
preserving architectural integrity,
recoverability, and execution boundaries.

PRIMARY OBJECTIVE:
[Define the requested outcome]

ALLOWED SCOPE:
[Allowed files, components, and services]

PROHIBITED CHANGES:
[Explicit restrictions]

ACCEPTANCE CRITERIA:
[Required tests and completion conditions]

AUTHORITY:
[Development, integration, deployment,
and operational permissions]

DDLS EXECUTION RULES:

1. Preserve the original development
   objective and its acceptance contract.

2. Continue normal implementation when
   issues can be resolved within scope.

3. Classify blockers before deciding
   whether to FIX, SHIFT, WAIT, REPLAN,
   STOP, or ESCALATE.

4. Apply evidence-aware retry limits.
   Allow at most 3 substantially similar
   repair attempts per hypothesis by
   default.

   Do not reset the budget without
   material new evidence.

   Stop immediately on critical safety
   or authorization violations.

5. Never create an enabling loop without
   a qualifying dependency and a
   defined Return Contract.

6. Create a verified, recoverable
   checkpoint before suspending
   the parent loop.

7. Distill the working context for
   enabling loops.

   Preserve relevant failed attempts,
   constraints, decisions, and evidence
   through durable references.

8. Implement only the minimum
   sufficient enabling capability.

9. Detect nested, circular, shared,
   and parallel dependencies.

10. Do not spawn uncontrolled nested
    loops or expand architectural scope
    without the required authority.

11. For parallel work, enforce ownership,
    isolation, contract compatibility,
    and resource-conflict controls.

12. Validate enabling outputs before
    integration.

13. Treat integration, deployment, and
    sensitive operational actions as
    independently authorized activities.

14. Before resuming a suspended parent
    loop, verify source, contract,
    schema, runtime, and authorization
    drift where relevant.

15. When assumptions become invalid,
    stop affected execution and
    identify impacted dependencies.

16. Inventory side effects before
    any rollback or cleanup.

    Never automatically roll back
    shared, irreversible, or production
    state.

17. Preserve an auditable record of
    decisions, revisions, tests,
    failures, and remaining risks.

18. Respect human intervention,
    approval gates, and revoked
    permissions.

19. Do not interpret missing approval
    as implicit authorization.

20. Complete the original loop only
    after its acceptance criteria
    are satisfied.

OUTPUT REQUIREMENTS:

Report:

- Current loop and state
- Completed work
- Blockers and evidence
- Decisions taken
- Enabling loops created
- Checkpoint reference
- Source revisions
- Tests and validation results
- Drift findings
- Side effects and recovery status
- Authorization status
- Unresolved risks
- Next permitted action

If safe completion is not possible,
stop and report the precise blocker.

Never fabricate evidence, permissions,
test results, or successful outcomes.
```

Place stable agent rules in `AGENTS.md` or the instruction file used by your agent, and specify objective, scope, and acceptance for each task. Avoid copying the entire playbook into every context window when it is already available as a stable source of truth.

---

## 18. Daily Operating Procedure

**Before starting:** Confirm the objective, scope, constraints, acceptance criteria, and authorizations.

**During execution:** **Continue unless a qualified blocker requires a different decision.** Fix routine local issues directly; use DDLS shift handling for genuine missing dependencies.

**When opening an enabling loop:** Record blocker evidence, checkpoint, return contract, execution scope, retry budget, authorities, and return conditions.

**Before resuming:** Verify enabling acceptance, contract compatibility, relevant drift, required integration state, evidence freshness, restored context, and continuing authorization.

**When finishing:** Report what was completed, tested, changed, left unchanged, and remains at risk. State integration and deployment status separately.

---

## 19. Measuring DDLS Effectiveness

Measure outcomes rather than counting shifts or reports.

| Metric | Purpose |
|---|---|
| Resume Success Rate | Successful resumption of eligible suspended work |
| Time to Resume | Delay between enabling acceptance and parent resumption |
| Enabling Rework Rate | Rework in enabling outputs |
| Repeated Failure Rate | Recurrence of substantially similar failed attempts |
| Context Recovery Failure Rate | Adequacy of checkpoints and handoffs |
| Integration Failure Rate | Quality of convergence and compatibility |
| Unauthorized Changes | Authorization violations |
| Scope Expansion Rate | Growth beyond approved enabling scope |
| Original Objective Lead Time | End-to-end delivery impact |
| Recovery Success Rate | Effectiveness of failure handling |
| Escaped Defects | Problems missed before delivery |

Define metric denominators and observation windows before comparing outcomes. DDLS is not assumed to accelerate every project; in low-risk, trivial work, its overhead may exceed its benefit.

---

## 20. Definition of Done

A primary loop may be marked complete only when:

1. Its approved objective has been achieved.
2. Its acceptance criteria pass.
3. Mandatory dependencies have been resolved or dispositioned by an authorized decision.
4. No material changes remain undocumented.
5. No unacceptable constraint violations remain.
6. Test evidence is tied to identifiable source and environment state.
7. Integration and deployment status are explicitly tracked separately.
8. Known residual risks are recorded.
9. Child loops are closed or their remaining dependencies accurately recorded.
10. Another engineer can review the outcome without relying on the agent's memory.

If development is complete but deployment has not occurred, state that distinction explicitly.

---

## 21. Boundaries and Non-Goals

DDLS does **not** replace software architecture, code review, CI/CD, version control, incident management, security engineering, test engineering, or project management.

It does **not** guarantee discovery of every dependency, resolution of every architectural problem, defect-free code, successful resumption in all cases, faster delivery in every context, reversible changes, or agent autonomy without human oversight.

It aims to make dependency-driven development more disciplined, verifiable, and recoverable.

---

## 22. The DDLS Engineering Principle

**Preserve Intent. Qualify Dependencies. Isolate Enablement. Verify Outcomes. Resume Safely.**

If you discover that completing a feature requires a missing foundation, do not force completion through uncontrolled workarounds.

If you must build that foundation, do not lose the original objective.

If the foundation is completed, do not resume until its validity and compatibility are verified.

If the approach fails, do not compromise system integrity to conceal that failure.

**DDLS is an engineering workflow for maintaining disciplined development continuity when software reveals dependencies that were not known during initial planning.**

---

*DDLS v2.1 — Dependency-Driven Loop Shifting*  
*Engineering Operations Playbook*  
*Ali Mohammed — 2026*
