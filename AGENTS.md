# DDLS v2.2 — Standing Agent Instructions

> Licensed under Apache License 2.0. Original DDLS framework: Ali Mohammed (2026). See [LICENSE](LICENSE) and [NOTICE](NOTICE).

These are the concise operational instructions for agents acting in this repository. The governing playbook is [DDLS v2.2](docs/DDLS-v2.2.md). Combine these rules with the target project's existing stronger policies.

## Default: be lightweight

- Default to **TRANSPARENT**: work normally on local bugs and low-risk tasks. **Do not create DDLS YAML, shift records, or extra loops for ordinary fixes.**
- Preserve the authorized objective, scope, acceptance, stop conditions, and current permissions.
- Use **MANAGED_SHIFT** only for an evidenced missing prerequisite requiring independent work. Reuse an issue/PR/checkpoint and concise return conditions.
- Use **GOVERNED** for security-sensitive, production, irreversible, high-impact architectural, or shared-state multi-agent work — whether or not a SHIFT occurs.

## Dependency and budget discipline

1. Diagnose before shifting; missing authorization and external conditions often require WAIT or ESCALATE, not new code.
2. Track a **single objective-level execution envelope** when enabling work is material. Nested/parallel loops get sub-allocations; they do **not** reset the parent's cumulative time, tools, tokens, cost, or shift limits.
3. Reserve capacity for integration, regression verification, and resuming the primary loop.
4. Default similar repair budget: **3 attempts per unchanged hypothesis**. Review before exceeding **3 active levels including the primary loop** or **2 total child shifts per objective**. These are review thresholds and may be changed only within explicit authority.
5. Assess evidence-backed progress after every enabling loop and before spawning another child. Stop, replan, or escalate if progress is absent or the budget is exhausted.
6. Use trustworthy provider cost/token telemetry when available. Otherwise mark them `UNKNOWN`, use configured tool/time/shift limits, and request review before significant expansion. Never invent usage numbers.
7. When multiple agents run, enforce explicit scope, file/shared-resource ownership, isolation, and aggregate budget — not merely per-agent limits.

## Safety, checkpoint, and evidence

1. Before a real shift, preserve a recoverable checkpoint, negative evidence, inherited prohibitions, and measurable return conditions. Prefer existing tickets/PRs to new paperwork.
2. Validate return conditions with real test/evidence references. Do not elevate self-reported `PASS` or `APPROVED` to verified truth.
3. Recheck relevant source, contract, schema, runtime, authority, and evidence drift before resume.
4. Development authority never implies permission to merge, deploy, migrate, restore, delete, rotate keys, or alter infrastructure.
5. Never automatically roll back shared, production, or irreversible state. Inventory effects and seek appropriate recovery authority.
6. If an authorized engineer changes the plan or stops work, reevaluate ongoing actions and authorization before further changes.

## Report proportionally

- **Ordinary work:** Result / Tests / Changes / Risks / Next action.
- **Managed shift:** Parent / Blocker evidence / Child / Checkpoint / Return conditions / Remaining budget / Next gate.
- **Governed work:** Add evidence provenance, authorities, drift, side effects, and recovery status.

**These text instructions do not constitute a tool-enforced budget, validator, or security boundary.** Never fabricate measurements, tests, permission, or outcomes.
