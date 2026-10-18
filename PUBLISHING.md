# Publishing DDLS v2.1 on GitHub

## 1. Review the release package

Confirm the spelling of the author's preferred public attribution and review all documents for private information. The example is fictional and contains no production secrets.

## 2. Confirm the adopted licensing and attribution

Licensing is already defined; **do not replace it with an all-rights-reserved notice**.

- [LICENSE](../LICENSE) maps repository paths to CC BY 4.0 (documentation) and Apache-2.0 (developer integration materials).
- [ATTRIBUTION.md](../ATTRIBUTION.md) gives recommended credit to Ali Mohammed (2026).
- [NOTICE](../NOTICE) carries the Apache-2.0 attribution notice.
- Complete reference texts are in `licenses/`; the controlling canonical texts are linked from LICENSE.

When publishing, replace no author identity, and add the actual GitHub URL to
attribution examples or future editions once known. Do not imply that
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
git commit -m "docs: publish DDLS v2.1 engineering playbook"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/ddls-framework.git
git push -u origin main
```

Replace `YOUR-USERNAME`. These commands assume a new, empty GitHub repository; if GitHub has already created an initial commit, fetch and reconcile it rather than force-pushing.

## 5. Tag the release

After reviewing the published content:

```bash
git tag -a v2.1.0 -m "DDLS v2.1 — Agent Reliability & Execution Safety"
git push origin v2.1.0
```

Use the GitHub Releases page to add a short release summary referencing `CHANGELOG.md`.

## 6. Guide adoption

In the repository description or introductory post, link directly to:

- `docs/DDLS-v2.1.md` — full document.
- `docs/QUICKSTART.md` — day-to-day adoption.
- `AGENTS.md` — copy/merge agent instructions.
- `templates/` — contract and report examples.

## 7. Keep updates coherent

When updating an operational rule, revise the full document, quickstart, agent instructions, affected templates, and changelog together. Distinguish tested findings from proposed improvements.
