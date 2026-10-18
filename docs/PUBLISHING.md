# Publishing DDLS v2.2 on GitHub

## 1. Review the release package

Confirm the spelling of the author's preferred public attribution and review all documents for private information. The case studies are synthetic teaching materials and should be checked for sensitive data before release.

## 2. Confirm the adopted licensing and attribution

Licensing is already defined; **do not replace it with an all-rights-reserved notice**.

- [LICENSE](../LICENSE) maps repository paths to CC BY 4.0 (documentation) and Apache-2.0 (developer integration materials).
- [ATTRIBUTION.md](../ATTRIBUTION.md) gives recommended credit to Ali Mohammed (2026).
- [NOTICE](../NOTICE) carries the Apache-2.0 attribution notice.
- Complete reference texts are in `licenses/`; the controlling canonical texts are linked from LICENSE.

The official source repository is https://github.com/ali83mohammed/ddls-framework.
Preserve this attribution when publishing derivatives. Do not imply that
independent implementations of abstract ideas have additional legal duties
beyond the applicable licenses.

## 3. Create the GitHub repository

Suggested repository name: `ddls-framework`  
Suggested description: `Dependency-Driven Loop Shifting — an engineering playbook for safe, dependency-aware AI-assisted software development.`

Suggested topics: `software-engineering`, `ai-assisted-development`, `coding-agents`, `dependency-management`, `engineering-workflow`, `developer-productivity`.

Choose public visibility if you want other engineers to read and discuss the framework. You can start private to review it first.

## 4. Initialize locally and push

From the directory containing `README.md`:

```bash
git init
git add .
git commit -m "docs: publish DDLS v2.2 engineering playbook"
git branch -M main
git remote add origin https://github.com/ali83mohammed/ddls-framework.git
git push -u origin main
```

These commands are intended for a new, empty repository or a fork with no prior commits. For an already-published repository, use normal commits and pulls; never force-push merely to repeat initial setup.

## 5. Tag the release

After reviewing the published content:

```bash
git tag -a v2.2.0 -m "DDLS v2.2 — Adaptive Workflow & Bounded Agent Execution"
git push origin v2.2.0
```

Use the GitHub Releases page to add a short release summary referencing `CHANGELOG.md`.

## 6. Guide adoption

In the repository description or introductory post, link directly to:

- `docs/DDLS-v2.2.md` — full document.
- `docs/QUICKSTART.md` — day-to-day adoption.
- `AGENTS.md` — copy/merge agent instructions.
- `templates/` — contract and report examples.

## 7. Keep updates coherent

When updating an operational rule, revise the full document, quickstart, agent instructions, affected templates, and changelog together. Distinguish tested findings from proposed improvements.
