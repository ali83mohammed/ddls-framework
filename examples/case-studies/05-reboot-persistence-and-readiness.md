# Case Study 05 — Reboot Persistence and Readiness

**DDLS v2.2 · Synthetic educational reconstruction.** This case contains no private source, infrastructure identifiers, or measured incident data.

## Scenario

A generic application has a Core Service and a separate background Coordinator. After an authorized reboot, the Core Service passes readiness but the Coordinator remains inactive. It had been startable before reboot; persistent activation had not been established.

## Blocker qualification

- **Evidence:** Independently check each component's post-reboot status and the Coordinator's startup eligibility using authorized, read-only observations.
- **Classification:** Distinguish transient startability from persistent boot activation and from runtime startup-order faults.
- **Authority:** Do not change production lifecycle policies without independent permission.
- **Smallest remedy:** Fix persistent activation through a supported installation or upgrade contract, not an undocumented manual start.
- **Falsifier:** If persistent activation already exists, investigate startup ordering, dependencies or readiness instead.

## DDLS decision

The controller can be accepted independently; the Coordinator branch remains blocked. **DIAGNOSE → STOP → conditional SHIFT/REPLAN** is safer than declaring a global PASS. A candidate enabling task must provide a versioned lifecycle remedy and verified return conditions, while preserving deployment authority. Parent and child share the same resource budget.

## Hypothetical baseline without DDLS

An agent might conflate the Core Service's success with full platform recovery, or restart the Coordinator manually and incorrectly declare durable recovery. These are counterfactual risks, not observed outcomes.

## Acceptance and safe outcome

Separate readiness evidence, persistent activation verified against the intended installation state, authorized integration, and, if required, an independently approved reboot test without manual intervention. No development-only test grants production authorization. Until those gates pass, the Coordinator remains on HOLD.

**Lesson:** Installed, startable, running, boot-enabled, and healthy-after-reboot are distinct properties.
