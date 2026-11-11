# AGENTS.md

`kokeb-labs-open-boards/.github` holds the organization profile and the community files, issue forms, discussion
forms and pull request template that every repository in `kokeb-labs-open-boards` inherits.

Agents working here or in any board repository follow the Kokeb Labs
[agent rules](https://github.com/kokeb-labs/.github/blob/main/standards/agents.md). Read them first.

## This repository

- `profile/README.md`: the organization page. Keep the repository table in step with the repositories.
- Community files: adapted from `kokeb-labs-drivers/.github`. A change of rule goes to `kokeb-labs/.github` first,
  with an ADR.
- `docs/adr/`: decisions for this organization. A decision is made by an owner; an agent may draft one but never
  sets its status to `accepted`.
- No settings code, tokens or private material here; the organization's settings live in
  `kokeb-labs/.github/org/`.

## Rules for board work

- Agents propose; a person approves. Do not mark a requirement approved, a test passed or a board status forward
  without a reviewer who did not write the change.
- Never invent a measurement, a test result or a datasheet value.
- Everything in this organization is public: no customer data, quotes, prices or credentials, ever.

## Checks before pushing

- Markdown: markdownlint with line length 120 (tables and code blocks exempt).
- YAML: yamllint on `.github/`.
- Commits are signed off (`git commit -s`).
