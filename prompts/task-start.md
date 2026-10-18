# DDLS v2.1 — Task Start Contract

Copy this into an AI coding agent task and complete the placeholders. The standing rules are in [`../AGENTS.md`](../AGENTS.md).

```text
Operate under DDLS v2.1.

PRIMARY OBJECTIVE:
[Exact target outcome]

ALLOWED SCOPE:
[Files, modules, services, and environments you may modify]

PROHIBITED CHANGES:
[Protected resources, changes, or operations]

ACCEPTANCE CRITERIA:
[Specific automated tests, observed behavior, and evidence]

AUTHORITY:
- Development: [GRANTED / NOT_GRANTED]
- Integration: [GRANTED / APPROVAL_REQUIRED / NOT_GRANTED]
- Deployment: [GRANTED / APPROVAL_REQUIRED / NOT_GRANTED]
- Operational actions: [GRANTED / APPROVAL_REQUIRED / NOT_GRANTED]

STOP CONDITIONS:
[Events that require stopping or escalation]

EXECUTION REQUIREMENTS:
- Fix ordinary local issues within scope.
- Qualify a missing dependency with evidence before shifting.
- Use a default maximum of 3 substantially similar repair
  attempts per root-cause hypothesis unless authorized otherwise.
- Freeze with a recoverable checkpoint and explicit Return Contract.
- Preserve relevant negative evidence in a distilled context.
- Resolve circular dependencies through replanning rather than
  repeated nested loops.
- Separate development completion from integration and deployment.
- Verify acceptance, relevant drift, and authorization before resume.
- Inventory side effects before any cleanup or rollback.
- Stop and report when safe completion is not authorized or possible.

REPORT:
State / Work completed / Blockers / Evidence / Tests /
Revisions / Side effects / Authorization / Risks /
Next permitted action.
```
