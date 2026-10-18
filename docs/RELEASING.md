# Maintaining and Releasing DDLS

This is the **maintainer workflow** for the existing [ddls-framework](https://github.com/ali83mohammed/ddls-framework) repository. It does not contain first-time repository creation commands.

## Before merging a change

1. Verify the [Core](CORE.md), [current v2.2 reference](DDLS-v2.2.md), [Quickstart](QUICKSTART.md), [agent instructions](../AGENTS.md), examples, and templates are consistent when normative guidance changes.
2. Preserve [v2.1](DDLS-v2.1.md) as an archived reference; distinguish historical version references from active guidance.
3. Maintain exactly one [Unreleased] section at the top of [CHANGELOG](../CHANGELOG.md). Describe changes in the correct released or unreleased section.
4. Check Markdown links, case-study indexes, YAML syntax, authorship, applicable [licenses](../LICENSE), and attribution.
5. Review public content for code, credentials, private logs, customer data, or internal infrastructure details. Case studies remain synthetic unless separately verified and approved for public disclosure.
6. No benchmark results are to be claimed without reproducible artifacts. The [evaluation protocol](VALIDATION-PLAN.md) describes a planned study, not completed experimentation.

## Pull request and review

- Prefer normal review via PR with the [optional SHIFT section](../.github/PULL_REQUEST_TEMPLATE.md) only when a real prerequisite has been qualified.
- Do not treat a PR text checkbox, YAML field, or agent-written statement as evidence of authority, tests, or actual budget spend.
- Sensitive or irreversible changes need host-enforced protections and separately authorized reviewers, not just a document.
- Editorial maintenance can remain under v2.2; a new numbered version is not automatically necessary.

## Releasing a reviewed version

1. Determine the intended semantic/documentation version and check whether the proposed tag already exists. **Do not overwrite existing release tags.**
2. Review the final repository revision, changelog, acceptance evidence, copyright and license mapping, links, and test claims.
3. Move relevant Unreleased entries beneath the new dated version, then retain a single Unreleased heading.
4. Publish a GitHub tag and release only after the owner authorizes the final identity and notes; do not force-push or reset protected branches to publish.
5. Verify the live release links, source archive, attribution, and notes after publication.

DDLS v2.2 is an **experimental engineering playbook**, not a certification or a tested automation platform. This repository ships no ddls-check, validator, CLI, or production enforcement system.
