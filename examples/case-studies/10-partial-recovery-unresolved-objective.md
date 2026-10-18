# Case Study 10 — Successful Recovery, Unresolved Original Objective

**DDLS v2.2 · Evidence-informed synthetic reconstruction · GOVERNED**

> All identifiers, services, and operational details are fictional. This is not a disclosure of private incident logs, internal code, or a completed DDLS experiment.

## Original objective

A generic platform must recover both its main Controller and a separately managed Operations Coordinator after an authorized reboot, with a supported lifecycle upgrade path and independent operational authorization.

## Evidence and limitation

After a simulated controlled restart the Controller passes its own readiness gate, while the coordinator has no accepted post-reboot persistence result. A previous finalized installation has a different lifecycle contract from the new candidate. The development team may qualify a replacement upgrade mechanism in isolation, but has not obtained authorization for a live transition.

**Do not equate Controller recovery with completion of the parent objective.**

## DDLS dependency graph

```text
L0 PLATFORM_RECOVERY
 ├─ Controller reboot readiness             ACCEPTED in scenario
 ├─ Coordinator boot persistence            BLOCKED
 │   └─ Versioned lifecycle upgrade         DEVELOPMENT ONLY
 ├─ Exact production authorization          NOT_GRANTED
 └─ End-to-end operational acceptance       NOT_EVALUATED

L0: NOT COMPLETED
```

## Five blocker questions

1. Which component-specific checks establish each readiness claim?
2. Is the unresolved condition startup policy, incompatible lifecycle, missing approval, or a runtime failure?
3. Which changes can the agent safely perform without new authority?
4. What is the smallest supported upgrade contract preserving historical evidence?
5. What observation would refute the initial startup-policy hypothesis?

## Correct and incorrect decisions

- **Correct:** retain the Controller's independently accepted result; preserve the coordinator's blocked state; plan a compatible lifecycle transition and request authorization.
- **Incorrect:** announce global success from one healthy service, reinterpret a finalized old installation as incomplete, or execute a deployment because development tests passed.
- **Conditional:** create an enabling loop only if a missing software capability is supported by evidence. Missing human approval is WAIT/ESCALATE, not an automatic SHIFT.

All child work shares the original objective's budget. Preserve a reserve for final verification and return. Unknown token costs remain UNKNOWN.

## Return contract

The parent resumes only after independent Coordinator persistence evidence, validated lifecycle compatibility, trustworthy candidate identity, exact operational authorization, and applicable post-change tests. Development qualification alone cannot satisfy these conditions.

## Hypothetical comparison without DDLS

An agent might collapse the component-level statuses into a single PASS. This is a counterfactual risk, not a measured no-DDLS outcome.

**Lesson:** Partial recovery can be a genuine success while the original engineering objective remains unfinished.