# Using DDLS v2.2 with OpenAI Codex

**Goal:** Add low-overhead blocker discipline without making every small code fix an engineering ceremony.

## Place instructions

Codex recognizes repository instruction files such as `AGENTS.md`. In your project, **merge** the short rules from DDLS [Core](../docs/CORE.md) or the [standing guidance](../AGENTS.md) into the existing root `AGENTS.md`. Do not overwrite project-specific coding, security, or deployment rules. For directory-specific differences, prefer scoped instructions where supported.

Give individual tasks their ordinary scope, acceptance criteria, and explicit permissions. Do not paste the 22-section playbook into every run.

## Apply the workflow

1. For a normal defect: let Codex implement and test it, and report briefly.
2. If it proposes a genuine missing prerequisite: ask for the five [blocker qualification answers](../docs/CORE.md) **before** starting a child task.
3. For a justified SHIFT: preserve the relevant Git revision/patch; use an existing issue/PR note to record the return condition and inherited scope.
4. For longer or independent child work: use a separate Git branch/worktree when appropriate. A worktree alone does not isolate services or databases.
5. On return: review diffs, verify actual tests and integration permission, then check relevant drift.

## Permissions

Keep production credentials unavailable to the coding workspace whenever feasible. Use repository protection and host permission controls; a sentence in `AGENTS.md` is **not** a secure deny rule. Never give a coding agent authority to deploy merely by placing `deployment: GRANTED` in a file.

## Read more

- [Codex repository instructions source](https://github.com/openai/codex/blob/main/codex-rs/core/src/agents_md.rs)
- [OpenAI Codex development workflow guide](https://developers.openai.com/cookbook/examples/codex/iterating-development-workflows-with-codex)

DDLS does not require any Codex-only feature and provides no automated budget meter.