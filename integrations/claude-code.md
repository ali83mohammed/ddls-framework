# Using DDLS v2.2 with Claude Code

**Goal:** Preserve an ordinary coding workflow while adding a safe decision gate when new prerequisites arise.

## Place instructions

Claude Code supports project instructions in a repository-level `CLAUDE.md`. Add a **small** DDLS Core summary there, or link to a local copy of [DDLS Core](../docs/CORE.md). Keep stronger existing project rules intact. Use the per-task prompt for objectives and actual authorization, not as a replacement for tool permissions.

## Apply the workflow

1. Diagnose a suspected blocker with the five Core questions.
2. Use a compact PR or issue comment to preserve the parent goal, evidence, checkpoint, return condition, and scoped authority for a real SHIFT.
3. If the change is sensitive, request explicit human approval via the product's supported permission flow before actions, and prevent access to disallowed credentials/services.
4. Verify actual tests, drift, and return conditions before resuming the parent.

## Hooks and real enforcement

Claude Code documents `PreToolUse` hooks that can request approval or deny a tool call. **Do not assume hooks are installed just because DDLS asks for them.** Review hook matcher coverage, permissions, failure handling, and current vendor behavior before configuring any enforcement. For high-impact infrastructure, independently restricted credentials and protected environments are safer than a pattern-matching Bash hook alone.

No hook code or `ddls-check` is included in this release.

## Official references

- [Claude guidance on CLAUDE.md](https://support.claude.com/en/articles/14553240-give-claude-context-claude-md-and-better-prompts)
- [Claude Code hooks documentation](https://code.claude.com/docs/en/hooks)

Interfaces and hook schemas can evolve; verify against the current vendor docs before deployment.