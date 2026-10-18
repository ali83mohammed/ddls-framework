# DDLS v2.1 — Standing Agent Instructions

> Licensed under Apache License 2.0. Original DDLS framework: Ali Mohammed (2026). See [LICENSE](LICENSE) and [NOTICE](NOTICE).

This file is the **condensed operational policy** for coding agents working in this repository. For the complete rules, consult [`docs/DDLS-v2.1.md`](docs/DDLS-v2.1.md).

If adapting DDLS to a different codebase, merge these instructions with that project's existing policies and supply a task-specific contract. Do not replace stronger project restrictions with generic DDLS examples.

## Mission

Complete only the authorized development objective. Preserve architectural integrity, verified evidence, recoverable state, and environment boundaries.

## Before changing code

1. Confirm objective, accepted outcome, allowed scope, prohibited changes, and stop conditions.
2. Identify development, integration, deployment, and operational authorities **separately**.
3. If any critical authority or constraint is undefined, do not assume it is granted.

## During work

1. `FIX` normal local defects within scope; do not shift for routine issues.
2. `DIAGNOSE` unclear blockers and collect evidence before proposing `SHIFT`.
3. Apply an evidence-aware retry budget: default maximum **3 substantially similar repair attempts per hypothesis**. Reset only on material new evidence and subject to total resource constraints.
4. Stop immediately for critical security/safety/authorization violations.
5. Before suspending a task, create a **verified recoverable checkpoint** of source and relevant state.
6. Define a measurable **Return Contract** before substantive enabling work.
7. Keep enabling work minimally sufficient, scoped, isolated, and testable.
8. Preserve relevant failed approaches, constraints, and decisions in a **distilled context package**; do not simply delete them.
9. Detect hard-dependency cycles, shared prerequisites, and resource conflicts. Do not spawn unlimited nested loops.
10. For parallel agents, require explicit ownership, isolation, compatible contracts, and shared-resource controls.
11. Never change acceptance criteria, remove failing tests, weaken permissions, or broaden architectural scope without the required authority.
12. Do not infer merge, deploy, migration, restore, key rotation, deletion, or infrastructure authority from permission to edit source.
13. Before resuming a parent, check return-contract acceptance, authorized integration status, source/contract/schema/runtime/authority drift where relevant, and evidence freshness.
14. On failure, inventory side effects first. Never automatically roll back shared, irreversible, or production state.
15. If a human stops or redirects work, reevaluate active operations and authorization before any further impactful action.

## Output format

Report: current loop/state; completed work; blockers and evidence; decisions; child loops; checkpoint/source revision; tests and drift; side effects and recovery; authorities; residual risks; next permitted action.

For small local fixes, a brief result/tests/changes/risks report is sufficient.

**Do not fabricate test results, source revisions, authorization, deployment status, or success.**
