# Worked Example — Backup Feature Blocked by Missing Package Verification

> **Illustrative scenario only.** This is not an execution report about a real production system.

## Initial task (L0)

The team is implementing an incremental backup feature. The acceptance criteria require both valid backup creation and safe restoration. During development, the team finds that the project has no trusted package-integrity verification capability.

The agent reproduces the gap with an isolated test. This is a **qualified capability dependency**, not merely a routine syntax or unit-test defect.

- **Parent loop:** `BACKUP-V2`
- **Blocker:** Package-integrity verification is missing.
- **Decision:** `FREEZE` followed by `SHIFT`.
- **Authority:** Development granted; integration requires approval; deployment and operational actions not granted.

## Freeze the parent

The agent records the immutable source revision, captures pending changes, notes passing and failing tests, and preserves the intended restore behavior. The checkpoint can be restored without relying on chat history.

## Define an enabling loop (L1)

- **Loop:** `PACKAGE-VERIFY`
- **Objective:** Introduce a package-verification interface that rejects altered or invalidly signed packages.
- **Allowed:** Verification module and tests.
- **Not allowed:** Production changes, bypassing signatures, unrelated refactoring.
- **Return contract:** Valid packages accepted; tampered and invalidly signed packages rejected; existing backup format remains compatible.

The agent receives a context package containing the contract, relevant repository interfaces, failed approaches, and the evidence for the blocker. It does not require the entire previous conversation.

## Validate, but do not deploy

The agent may report that its local tests passed **only after they actually run**, with linked source revision and test results. The parent must not resume on a claimed but unverified success.

Because integration authority is `APPROVAL_REQUIRED`, an accepted implementation may remain `READY_TO_INTEGRATE`. It must not be assumed merged or deployed.

## Resume decision

Once authorized integration occurs, the engineer checks for code, interface, schema, runtime, and authority drift as applicable. The parent checkpoint is restored, and integration and restore-compatibility tests are rerun where necessary.

Only then may `BACKUP-V2` return to `ACTIVE`.

## Failure alternative

If the enabling implementation fails or its assumptions prove false, the correct outcome is `DIAGNOSE`, `REPLAN`, or `ESCALATE`. The agent inventories side effects; it does **not** automatically reverse shared database changes or touch production.

## What this example illustrates

1. **The parent objective survives the shift.**
2. **The enabling scope remains narrow.**
3. **Development, integration, and deployment remain separately authorized.**
4. **Relevant failed attempts stay visible through evidence references.**
5. **Resumption depends on verifiable acceptance and drift checks.**
