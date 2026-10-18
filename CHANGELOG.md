# Changelog

## [2.1] — 2026

**Agent Reliability & Execution Safety**

- Added evidence-aware retry budgeting (default: three substantially similar repairs per hypothesis).
- Distinguished context distillation from context deletion.
- Added source, contract, schema, runtime, authority, and evidence drift considerations.
- Clarified that a DAG alone does not imply safe concurrency.
- Replaced blanket teardown/rollback language with risk-aware side-effect reconciliation.
- Explicitly separated loop state, delivery state, and decision tokens.
- Added multi-agent ownership leases and safeguards against stale writers.
- Defined human intervention and agent handoff expectations.
- Clarified independent development, integration, deployment, and operational authorities.
- Organized full playbook, quickstart, agent instructions, templates, and an illustrative example.
- Published documentation under CC BY 4.0 and reusable agent materials under Apache-2.0, with explicit attribution to Ali Mohammed (2026).

## [2.0] — Historical baseline

- Introduced dependency graph alongside nested loop stack.
- Added dependency types, enabling strategies, return contracts, recovery governance, and adoption profiles.

_The historical baseline entries summarize the evolution described in the project design discussion; they are not claims of independently audited software releases._
