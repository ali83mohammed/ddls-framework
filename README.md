# DDLS — Dependency-Driven Loop Shifting

**A practical engineering playbook for dependency-aware software development with AI coding agents.**

**Version:** 2.2 — Adaptive Workflow & Bounded Agent Execution  
**Framework author:** Ali Mohammed  
**Year:** 2026  
**Official repository:** https://github.com/ali83mohammed/ddls-framework

> **Core principle:** Preserve Intent. Qualify Dependencies. Isolate Enablement. Verify Outcomes. Resume Safely.

## What is DDLS?

DDLS is a workflow for handling unexpected prerequisites discovered during software development. When a genuine dependency blocks a task, DDLS helps engineers preserve the original objective, isolate the necessary enabling work, verify its outcome, and safely resume the suspended task.

**Freeze → Shift → Enable → Validate → Integrate → Resume**

DDLS does not require a shift for every bug. Routine issues stay within the current task. It supports direct fixes, external waiting, architectural replanning, parallel enabling work, escalation, and cancellation when appropriate.

## Start here

**Start with the [one-page DDLS Core](docs/CORE.md).** The full playbook is an advanced reference, not mandatory reading for everyday coding. DDLS v2.2 is an **experimental engineering playbook**: its proposed benefits have not yet been established through controlled trials.

**Falsifiable hypothesis:** With identical safety rules and tools, adding DDLS Core improves blocker-decision accuracy, including fewer unjustified SHIFTs and unsupported completion claims, versus a comparable agent without DDLS. See the [proposed evaluation protocol](docs/VALIDATION-PLAN.md); **no experiment results are claimed**.

| Resource | Use it for |
|---|---|
| [One-page Core](docs/CORE.md) | Primary developer/agent entry point; decisions and five blocker questions |
| [Evaluation protocol](docs/VALIDATION-PLAN.md) | Pre-registered-style pilot design: 50 proposed runs, no results |
| [Enforcement map](docs/ENFORCEMENT-MAP.md) | Existing controls versus instruction-only safeguards |
| [Integrations](integrations/) | Codex, Claude Code, and Cursor adoption guidance |
| [Pull-request template](.github/PULL_REQUEST_TEMPLATE.md) | Optional compact SHIFT note for real blockers |
| [Full DDLS v2.2 playbook](docs/DDLS-v2.2.md) | Current daily workflow and engineering rules |
| [DDLS v2.1 archive](docs/DDLS-v2.1.md) | Previous release, preserved for reference |
| [Quickstart](docs/QUICKSTART.md) | A short decision procedure and worked flow |
| [AGENTS.md](AGENTS.md) | Standing instructions for AI coding agents |
| [Task-start prompt](prompts/task-start.md) | Scope, acceptance, and authority for a particular task |
| [Templates](templates/) | Primary-loop, shift, checkpoint, return-contract, and reporting records |
| [Case-study collection](examples/README.md) | Four synthetic cases: nested SHIFT, deployment STOP, NO SHIFT, and excess overhead |
| [Worked example](examples/backup-package-verification.md) | Freeze / shift / enable / validate / resume without production changes |
| [License](LICENSE) and [Attribution](ATTRIBUTION.md) | Permitted reuse and credit to the framework author |
| [Change history](CHANGELOG.md) | Version notes |
| [Contributing](CONTRIBUTING.md) | How to report issues and contribute improvements |
| [Release maintenance](docs/RELEASING.md) | Maintainer checklist for releases and documentation consistency |

## The DDLS decision path

```mermaid
flowchart TD
    A[Execute current task] --> B{Qualified blocker?}
    B -- No --> C[Fix or continue in current loop]
    C --> A
    B -- Yes --> D{Dependency type and risk?}
    D -->|External| W[WAIT and record recheck trigger]
    D -->|Circular or invalid premise| R[REPLAN / ESCALATE]
    D -->|Authorized enabling work| F[FREEZE with verified checkpoint]
    F --> S[SHIFT to bounded enabling loop]
    S --> V[VALIDATE return contract]
    V --> G{Integration approved and compatible?}
    G -- No --> H[Preserve state / request authorization / replan]
    G -- Yes --> I[INTEGRATE as authorized]
    I --> J[Check drift and restored context]
    J --> K[RESUME parent loop]
```

## v2.2: light by default

**TRANSPARENT** is the default: normal coding and a brief result, without required YAML or loop records. Use **MANAGED_SHIFT** only for a qualified missing prerequisite, with a short return contract recorded in an existing ticket or PR. Use **GOVERNED** for high-risk architecture or production-sensitive work, even without a shift.

For AI-assisted enabling work, use a **single objective-level resource envelope**: child loops do not receive a new budget. Review progress before adding another loop; report token or cost consumption as **UNKNOWN** if the host provides no reliable meter. No CLI or validator is included in this release.

## Five-minute adoption

1. **Set the objective.** Define allowed scope, prohibited changes, acceptance criteria, and authorities using [task-start.md](prompts/task-start.md).
2. **Work normally.** Fix routine problems without opening new loops.
3. **Qualify blockers.** Shift only when evidence establishes a missing prerequisite that cannot be resolved safely within scope.
4. **Checkpoint and contract on a real shift.** Reuse your PR or issue. Allocate time, tool, and available token/cost limits from the original objective, reserving enough for parent resumption.
5. **Review progress and resume.** Stop unproductive nested shifts or budget exhaustion. Confirm acceptance, integration authority, relevant drift, and parent readiness.

**Default retry recommendation:** No more than three substantially similar repair attempts per hypothesis without material new evidence. This is configurable, and critical safety or authorization violations require immediate stopping.

## Using DDLS with AI coding agents

Read the [agent instructions](AGENTS.md) and provide the [per-task contract](prompts/task-start.md). When adopting DDLS in an existing repository, **merge these instructions with the project's existing agent rules rather than overwriting them**. Project-specific safety and access controls take precedence over generic examples.

Agents may propose shifts and generate records. They may not infer permission to expand scope, merge, deploy, change protected infrastructure, or perform sensitive operations.

## Files and examples

The `templates/` directory contains YAML records that can be filled in manually or generated by an agent. The templates are examples of a human-readable record format, **not a formally validated wire protocol or a production orchestration engine**.

The [case-study collection](examples/README.md) demonstrates nested enabling work, a blocked deployment, and a no-shift diagnosis. All cases and the earlier backup example are **synthetic teaching materials**, not test reports, benchmarks, or disclosures from any private codebase.

## Design scope

DDLS complements, rather than replaces, software architecture, version control, CI/CD, code review, security engineering, incident response, and project management. It does not guarantee that every dependency can be resolved, that every change is reversible, or that every project will be faster.

## Licensing, reuse, and attribution

**You are welcome to adapt DDLS, translate it, build tools for any programming language, integrate it into AI coding assistants, and use it in commercial or proprietary products.**

The repository uses **two permissive licenses**, depending on the file:

| Materials | License | Key conditions |
|---|---|---|
| Framework documentation (`docs/`, `README.md`, `examples/`, etc.) | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) | Attribution, license link, and indication of adaptations when shared |
| AI-agent instructions, prompts, and reusable templates (`AGENTS.md`, `prompts/`, `templates/`, `.github/`) | [Apache-2.0](https://www.apache.org/licenses/LICENSE-2.0) | Retain required license and attribution notices, including relevant `NOTICE` material |

**Originally conceived and authored by Ali Mohammed (2026).** See the [license map](LICENSE), [NOTICE](NOTICE), and [attribution guide](ATTRIBUTION.md).

Preferred acknowledgement: *“Based on DDLS (Dependency-Driven Loop Shifting), originally conceived and authored by Ali Mohammed (2026).”*

Independent implementations of abstract DDLS ideas are welcome under any software license; credit is requested, but copyright licensing does not necessarily make such attribution legally mandatory without reuse of protected materials. Attribution must not imply endorsement by the author.

## Version

See [CHANGELOG.md](CHANGELOG.md). This is the **v2.2 experimental engineering playbook**, not a certification that all usage scenarios have been experimentally validated.
