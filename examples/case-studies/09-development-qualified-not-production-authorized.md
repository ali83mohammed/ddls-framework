# Case Study 09 — Development Qualification Without Production Authority

**DDLS v2.2 · Evidence-informed synthetic reconstruction · GOVERNED**

> Uses generalized release and lifecycle concepts only. No private package, signature, system identity, operational command, or internal artifact is included.

## Problem

A team builds a version-aware service upgrade capability and subsequently develops a host-effect adapter. The implementation and then the adapter become **qualified under isolated development rules**, but the target has not passed the independently authorized production handoff.

The parent objective is **safe operational transition**, not simply completion of source changes.

## Independent gates

| Gate | Fictional teaching status | Why this does not imply the next gate |
|---|---|---|
| Upgrade contract tests | DEVELOPMENT_QUALIFIED | Not proof of compatible live target |
| Host adapter tests | DEVELOPMENT_QUALIFIED | Not proof of exact production artifact trust |
| Candidate identity and trust | NOT_EVALUATED | Requires its own provenance |
| Target lifecycle preflight | NOT_EVALUATED | Must match actual, fresh target state |
| Production authorization | NOT_GRANTED | Never inferred from development success |
| Live operational acceptance | NOT_TESTED | Cannot exist before an authorized operation |

**Sequence matters:** An adapter that was initially missing may later be qualified in development. It is incorrect to keep describing it as incomplete after its accepted development tests.

## Five-question diagnosis

- Which revision-specific evidence supports each claim?
- Is the blocker missing adapter code, compatibility, artifact trust, or human approval?
- Does the agent have development permission, integration approval, or operational authority?
- If adapter code is missing, what bounded enabling capability suffices?
- If coverage already proves the adapter complete in development, doesn't that falsify the missing-adapter hypothesis?

## DDLS graph and decisions

```text
L0 SAFE_OPERATIONAL_TRANSITION
 ├─ L1 VERSIONED_UPGRADE_CONTRACT  → development evidence
 ├─ L2 HOST_ADAPTER                → subsequent development evidence
 ├─ exact artifact trust           → separate gate
 ├─ current target eligibility     → separate gate
 └─ operational authority          → NOT_GRANTED

Production activation: STOP
```

Use SHIFT for a demonstrated missing software capability, not for withheld approval. A development-qualified module does not make the parent production-ready. Each enabling child inherits the parent budget. Its work stops when its specific return conditions are met, even if other independent gates remain closed.

## Counterfactual without DDLS

An agent could mark deployment complete on the strength of local tests or write APPROVED into a local record. Those actions would be invalid, but this example does not claim that they occurred in an experiment.

## Safe outcome

Development can be accepted within scope, while activation remains on HOLD pending independent compatibility, trust and authorization evidence. Record exact unknowns and the next permitted review step. Never perform blind rollback of shared state.

**Lesson:** Development PASS, integration readiness, artifact trust, production permission and runtime success are different propositions.