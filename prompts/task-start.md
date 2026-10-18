# DDLS v2.2 — Lightweight Task Start Prompt

Paste and fill only relevant sections. For routine tasks, a one-sentence objective and constraints are enough. The standing guidance lives in [AGENTS.md](../AGENTS.md).

```text
Operate under DDLS v2.2.

OBJECTIVE:
[What must work?]

SCOPE AND PROHIBITIONS:
[Relevant allowed changes and hard limits]

ACCEPTANCE:
[What must be demonstrated, and how?]

AUTHORITY:
[Allowed actions; integration, deployment, and operational permissions are separate]

DEFAULT MODE: TRANSPARENT.
Fix ordinary problems without DDLS YAML or extra loops.

If an evidenced missing prerequisite blocks acceptance:
- Select MANAGED_SHIFT, or GOVERNED if risk requires it.
- Preserve a recoverable checkpoint and concise return conditions.
- Reuse the current issue, PR, or task notes when possible.
- Allocate any child work from the remaining parent objective budget.
- Reserve time/tools for integration, regression testing, and resumption.
- Review evidence-backed progress before additional shifts.
- Default review thresholds: 3 similar repairs per hypothesis,
  3 active nested levels including the parent, and 2 child shifts
  for one objective. Never assume unlimited model budget.
- Use real usage telemetry if available; otherwise report UNKNOWN.
- STOP / REPLAN / ESCALATE for exhausted budget or absent progress.
- Never infer deployment, operational authorization, or test PASS.
- Verify return conditions and relevant drift before RESUME.

REPORT:
Ordinary: Result / Tests / Changes / Risks / Next action.
Shift: Parent / Evidence / Child / Checkpoint / Return conditions /
Remaining budget / Next gate.
Governed: additionally authorities, evidence provenance, side
effects, drift, recovery, and unresolved risks.
```

This prompt is operational guidance, not an enforcement or metering mechanism.
