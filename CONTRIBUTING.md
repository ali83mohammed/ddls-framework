# Contributing to DDLS

Contributions that improve clarity, correctness, safety, and daily usability are welcome.

## Evaluation and truthfulness

Contributions that report neutral or negative findings are welcome. Label illustrative scenarios as synthetic, observational reports as observed, and evaluation results as measured. Do not claim a benchmark was executed unless reproducible artifacts and trustworthy evidence exist. The project's [Core](docs/CORE.md) and [evaluation protocol](docs/VALIDATION-PLAN.md) define the current testable hypothesis.

## What to submit

- A reproducible counterexample where a DDLS rule fails.
- A proposed change that reduces operational ambiguity.
- Evidence from an AI-assisted development workflow.
- A documentation correction or a clearer example.

## Issue guidelines

Describe the current rule, the actual or hypothetical scenario, the observed or expected failure, the proposed correction, and any security/production implications.

## Change guidelines

1. Keep the full playbook and abbreviated agent rules semantically consistent.
2. Distinguish **mandatory safeguards** from **configurable defaults**.
3. Never imply that successful tests authorize production operations.
4. Prefer operationally testable language over marketing claims.
5. Update `CHANGELOG.md` for normative behavior changes.
6. Avoid real credentials, private repository details, customer data, or production logs.

## Status of the framework

DDLS v2.1 is published as an operational engineering playbook. It is not an assurance that every possible scenario has been validated or that its guidance replaces project-specific controls.

## Licensing and credit

Contributions are accepted under the license applicable to the destination path, as listed in [LICENSE](LICENSE): **CC BY 4.0** for the documentation and **Apache-2.0** for the developer integration materials. Contributors should submit only material they can license accordingly and should identify third-party sources requiring separate permission.

The original DDLS framework attribution remains **Ali Mohammed (2026)**. Contributors retain credit for their own original changes; describe significant adaptations in the pull request and changelog. See [ATTRIBUTION.md](ATTRIBUTION.md).
