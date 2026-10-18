# DDLS v2.2 — From Policy to Available Controls

**Status:** Integration guidance, not proof that controls are enabled in any repository. This project does **not** include a validator, CLI, permission hook, or `ddls-check`.

DDLS instructions influence decisions; only the **host system's authorization controls** can reliably prevent disallowed actions. Never describe a self-written YAML field as production authority.

| DDLS safeguard | Practical existing mechanism | What the mechanism does *not* prove |
|---|---|---|
| Source scope and review | GitHub protected branches, pull-request reviews, CODEOWNERS + required review rules | It does not protect untracked external services |
| Test before merge | CI required status checks tied to target commit | Tests do not authorize deployment or guarantee correctness |
| Deployment and operational authority | Scoped service identities, protected environments, separate credentials, approvals | A PR checkbox or agent assertion is not an access-control boundary |
| Prevent risky agent tool actions | Host-side permission approvals and policy controls; supported pre-tool hooks | A plain prompt or local Git hook can be bypassed |
| Checkpoint and drift | Git commit/patch, reviewed diff, immutable artifact references | An existing SHA does not prove checkpoint restoration |
| Budget and retry controls | Platform usage counters, per-run caps, tool-call ceilings, operator review | A self-reported token figure is not trustworthy billing data |
| Recovery / rollback | Environment-specific reversible plan, backups, incident controls | Automatic rollback of shared state may be dangerous |
| Multi-agent isolation | Worktrees + separate write targets, coordination of shared services, scoped credentials | Separate branches do not isolate mutable databases |

## Human confirmation for sensitive actions

For any command capable of modifying production, migrations, credentials, or externally shared state:

1. Place the actual permission boundary at the tool/service or protected environment level.
2. Require scoped approval for the **specific operation and target**, not a generic "approved" field.
3. Recheck target and change identity just before execution; record actual outcomes, including partial failure.
4. Never rely on a text pattern alone to catch every dangerous shell/API operation.

## GitHub setup checklist (operator-owned)

- Configure branch/ruleset protection with required reviews and required CI checks.
- Add `CODEOWNERS` only where real owners/teams can review; combine it with appropriate protection rules. A file by itself does **not** enforce review.
- Configure environment-specific deployment approval gates, tokens, and credentials.
- Confirm GitHub Actions jobs and third-party actions do not unintentionally obtain write access to protected environments.
- Review the actual policy and permissions before claiming any gate is enforced.

## Tool-specific options

See [Codex](../integrations/codex.md), [Claude Code](../integrations/claude-code.md), and [Cursor](../integrations/cursor.md) for lightweight DDLS instruction placement and authority considerations. Tool behavior and UI change over time; consult current vendor documentation.

### Maintainer policy

No sample hook in this repository grants production access. Future enforceable controls require separately reviewed code and independent tests. This document maps possibilities; it does not implement them.