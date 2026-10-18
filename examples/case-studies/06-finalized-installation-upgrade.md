# Case Study 06 — Finalized Installation and Versioned Lifecycle Upgrade

**DDLS v2.2 · Synthetic educational reconstruction · GOVERNED**

This fictional example contains no private installation ledger, signing material, source code, or production identifiers.

## Context

A background service was installed under **Generation A** and reached FINALIZED state. Its runtime is inactive. A Generation B installer exists, but its repair path only handles incomplete transactions, and its rotation path requires a healthy active installation.

**Original objective:** Restore supported operations without falsifying historical state.

## Five blocker questions

1. **Evidence:** Does a trusted lifecycle record confirm FINALIZED, not INCOMPLETE?
2. **Category:** Is the missing capability a legal state transition, rather than a broken repair routine?
3. **Authority:** Is production migration separately permitted? In this exercise it is not.
4. **Smallest remedy:** Define an explicit versioned upgrade contract preserving historical integrity.
5. **Falsifier:** If an existing supported transition already covers this exact finalized state, no new enabling loop is necessary.

## Strategy comparison

| Option | Condition | Decision |
|---|---|---|
| Restore Generation A and then upgrade | Authorized safe restore available | CONDITIONAL |
| Force repair or healthy rotation | Current contract must support inactive FINALIZED state | INELIGIBLE |
| Develop Generation A → B upgrade | Explicit audited lifecycle contract | Candidate SHIFT |

## DDLS path

`DIAGNOSE → REPLAN → conditional SHIFT → VALIDATE → STOP / WAIT`.

A child task may design and test the lifecycle upgrade in isolation. It draws on the **same** parent budget; broad redesign triggers PROMOTE and review. The return contract requires source-state identity, legal transition semantics, negative-case tests, compatibility, recovery rules and exact authorization. No development success automatically permits deployment.

## Hypothetical baseline

Without disciplined state qualification, an agent might relabel FINALIZED as INCOMPLETE or use an ineligible operation, weakening correctness. This is a counterfactual, not an actual experiment.

## Outcome

The safe synthetic outcome is **production NO-GO**, with the original record preserved until compatibility and permission gates are satisfied. Do not treat an inactive service as proof its historical installation failed.

**Lesson:** Repair, recovery, rotation and lifecycle upgrade are different operations with different preconditions.