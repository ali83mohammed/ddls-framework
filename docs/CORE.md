# DDLS Core — One-Page Daily Guide

**Dependency-Driven Loop Shifting · v2.2 · experimental playbook**  
**Author:** Ali Mohammed · **Full reference:** [DDLS v2.2](DDLS-v2.2.md)

> **DDLS is an engineering decision workflow, not an LLM's internal reasoning or tool-use loop.** A DDLS *loop* is a bounded engineering task with an objective, acceptance conditions, and a return or termination condition.

**Working hypothesis (not an established result):** With identical base safety rules and tools, an AI coding agent using DDLS will make fewer unjustified blocker decisions (including false SHIFTS), cross fewer unauthorized scope boundaries, and make fewer unsupported success claims than the same agent without DDLS. **Test it:** [Evaluation plan](VALIDATION-PLAN.md).

## Do the simplest safe thing first

```text
Work on the original task
  ├─ Ordinary issue?                      → CONTINUE or FIX
  └─ Something blocks acceptance?         → DIAGNOSE
       ├─ Code defect within scope?       → FIX
       ├─ External system or approval?    → WAIT / ESCALATE
       ├─ Verified missing prerequisite?  → SHIFT (checkpoint + return condition)
       └─ No safe/authorized path?        → STOP and report
```

These **six primary decision families** are the reader-facing interface: `CONTINUE`, `FIX`, `DIAGNOSE`, `SHIFT`, `WAIT / ESCALATE`, `STOP`. The [reference](DDLS-v2.2.md) retains detailed states and transitions, such as `INVALIDATE`, `PROMOTE`, and `REPLAN`, when needed.

## Five blocker questions — before every SHIFT

1. **Evidence:** What observable test, trace, contract, or specific failure supports the alleged missing capability?
2. **Classification:** Is this a code defect, permission boundary, external condition, or architectural prerequisite?
3. **Authority:** May the current engineer/agent resolve it within the authorized scope?
4. **Smallest remedy:** What is the smallest sustainable change that removes it? Could a direct FIX suffice?
5. **Falsifiability:** *If my hypothesis is right, I expect X; if I observe Y, I must reject or revise it.* What are X and Y?

If evidence is incomplete, **DIAGNOSE first**. A blocker need not be reproduced in production; safe observations may support it. Do not claim certainty without evidence.

## When SHIFT is justified

Preserve the parent work, then record this **short note** in the current PR/issue (no new YAML required):

```text
Parent goal:
Blocker + evidence / falsifiable prediction:
Child prerequisite + smallest change:
Checkpoint (commit or recoverable patch):
Return condition + test:
Authority and prohibitions:
Shared objective budget + reserved return capacity:
```

Work on the child only within inherited limits. Nested/parallel children **share** the original objective's budget. Suggested **review thresholds**: 3 substantially similar repairs per hypothesis, 3 active nested levels including the parent, or 2 child SHIFTS per objective. These are not fresh allowances. After each child or proposed deeper SHIFT, require evidence of progress, not lines of code. Stop/replan when budget or authority runs out.

**Return:** validate the child, obtain any required integration permission, check relevant drift and evidence freshness, and resume the parent. **Never equate** a written `PASS`, a successful unit test, or permission to edit code with deployment authorization.

## Keep it light, enforce real boundaries

**Default:** normal development, no DDLS paperwork. **Material SHIFT:** short note and checkpoint. **High-risk work:** use [governed controls](DDLS-v2.2.md), regardless of SHIFT.

Prompts guide agents; they **do not** enforce permissions, meter hidden tokens, or attest tests. Use trusted CI, scoped credentials, protected branches, and approval mechanisms where needed. See [enforcement mapping](ENFORCEMENT-MAP.md).

**Read next:** [Quickstart](QUICKSTART.md) · [Case studies](../examples/README.md) · [Agent integrations](../integrations/) · [Evaluation protocol](VALIDATION-PLAN.md).