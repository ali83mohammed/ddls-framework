# DDLS v2.1 — Engineering Case Studies

These examples show how an engineer or an AI coding agent can **choose the appropriate DDLS decision**, not merely how to perform a SHIFT.

> **Disclosure and source protection:** All scenarios, names, identifiers, artifacts, system relationships, and decision traces in this directory are **synthetic teaching materials**. They are informed by general patterns found in complex software systems. They are **not** reproductions, verified incident reports, benchmark results, proprietary source code, private configuration, or evidence from a specific product. Placeholder evidence is not proof that tests ran.

The case studies do not require access to any private repository. Use the [current DDLS v2.2 playbook](../docs/DDLS-v2.2.md) as the governing reference. These synthetic cases were authored under v2.1; their decisions remain educational examples rather than machine-enforced policies. v2.2 adds lightweight governance modes and shared budget rules; the earlier case narratives do not claim to demonstrate measured token usage.

## Case-study index

| Case | Decision under examination | What the engineer should learn | Companion record |
|---|---|---|---|
| [01 — Hidden dependency in background processing](case-studies/01-hidden-dependency.md) | `FREEZE → SHIFT`, nested enablement, conditional `PROMOTE` | Avoid solving infrastructure blockers through feature-specific patches | [Illustrative return contracts](contracts/01-return-contracts.yaml) |
| [02 — Development complete, deployment blocked](case-studies/02-deployment-gate.md) | `STOP / ESCALATE / WAIT` | Development acceptance, integration, and production authorization are separate | [Authorization gate](contracts/02-authorization-gate.yaml) |
| [03 — The blocker that did not require a shift](case-studies/03-no-shift-required.md) | `DIAGNOSE → WAIT → CONTINUE` | Diagnose external capabilities before creating unnecessary enabling code | [Diagnostic decision](contracts/03-diagnostic-decision.yaml) |

The earlier [backup-package verification walkthrough](backup-package-verification.md) remains available as a shorter linear-SHIFT introduction.

## How to read a case

1. Identify the original objective and the specific evidence required to call something a blocker.
2. Read the rejected alternatives; DDLS is a **decision discipline**, not a requirement to create extra tasks.
3. Inspect the graph or prerequisite chain and the return/authorization criteria.
4. Distinguish **simulated decision outcomes** from **real test evidence**. No tests were executed for these illustrative case studies.
5. Transfer the pattern, **not** the example's configuration or fictional status values, into your own project.

## Reuse and safety

These documents are published as DDLS documentation under **CC BY 4.0**; see [LICENSE](../LICENSE) and [attribution](../ATTRIBUTION.md). Do not insert actual secrets, internal URLs, database contents, private code, user data, infrastructure maps, or raw production logs into a public example. When producing a case inspired by nonpublic work, reconstruct it independently with synthetic names, data, and relationships; verify its teaching logic separately from its provenance.

No case authorizes an agent to access production, change permissions, deploy, or delete resources.