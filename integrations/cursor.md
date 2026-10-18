# Using DDLS v2.2 with Cursor

**Goal:** Keep daily work lightweight, and present DDLS only when a real blocker or high-risk change requires it.

## Place instructions

Cursor supports **project rules** in `.cursor/rules/` as `.mdc` files. It also supports `AGENTS.md` as a simpler alternative. Prefer whichever fits the project's existing setup; do not install duplicate competing versions of the same DDLS instruction.

For a scoped project rule, include metadata appropriate for your Cursor version, such as a description and applicability. Include the short [DDLS Core](../docs/CORE.md) decision questions in the rule, or maintain them as referenced repository documentation.

## Workflow

1. The agent fixes ordinary local issues without writing DDLS contracts.
2. On a qualified blocker, ask for evidence, falsifiable prediction, minimal remedy, checkpoint, and return conditions.
3. For independent enabling work, keep the diff isolated in an appropriate branch or worktree. Protect shared data/services separately.
4. Treat review, CI, and deployment permissions as **external controls**, not promises in a project rule.

## Official references

- [Cursor project rules](https://prod.cursor.com/docs/rules)
- [Cursor rules help](https://prod.cursor.com/help/customization/rules)

Project rules guide model behavior; they are not an access-control system. DDLS introduces no Cursor plugin or validator.