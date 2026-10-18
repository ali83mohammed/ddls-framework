# Case Study 07 — Approval Contract and Canonical Evidence Compatibility

**DDLS v2.2 · Evidence-informed synthetic reconstruction · GOVERNED**

> All schemas, artifacts and records are illustrative. No real approval, signature, code, or non-public release identity is reproduced.

## Engineering problem

A generic release workflow binds an approval to a versioned contract. A new candidate carries a required field absent from the old contract, and the verification step rejects it. A second possible cause is a difference in canonical byte representation, but this must **not** be asserted without byte-level evidence.

The parent objective is to deliver a **verifiable candidate**, not merely to make a build command return success.

## Blocker qualification

1. **Evidence:** Which exact schema rejection, digest comparison, or independent identity check failed?
2. **Class:** Is this an omitted required field, unsupported contract version, serialization mismatch, or wrong artifact?
3. **Authority:** Can the agent alter implementation? Can it issue approvals? These are **separate permissions**.
4. **Smallest fix:** Repair in-scope serialization/test logic, or qualify a truly missing contract evolution.
5. **Falsifier:** If logical fields and documented canonical bytes agree yet verification still fails, reject the serialization hypothesis and investigate provenance.

## DDLS choices

| Condition | Decision |
|---|---|
| Local bug in serializer or fixture | FIX, no new loop |
| Valid candidate needs a new schema capability | FREEZE → conditional SHIFT to versioned contract work |
| Wrong or missing authority | STOP / ESCALATE |
| Identity cannot be established | DIAGNOSE, do not assert PASS |

A contract-evolution child inherits the parent budget and prohibitions. Its return conditions require compatibility rules, positive and negative tests, verified source revision, and correct evidence provenance. There is no authority to loosen the verification policy.

## Without DDLS — hypothetical baseline

An agent might remove a required field to satisfy an obsolete contract, treat distinct byte hashes as equivalent, or suppress verification. These are possible failure modes **not measured control outcomes**.

## Failure and return

A correct rejection by an old verifier may prove the guard is working; it does not necessarily prove the underlying code is defective. If the needed schema change exceeds authority, preserve the parent checkpoint and escalate. **Acceptance remains NOT_EVALUATED** until real version-specific evidence exists.

**Lesson:** Refusal at an approval gate is evidence to investigate, not a reason to bypass the gate.