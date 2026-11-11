# Contributing to Kokeb Labs Open Boards

This applies to every repository in the `kokeb-labs-open-boards` organization unless the repository has its own
`CONTRIBUTING.md`. The full rules are in the Kokeb Labs
[engineering standard](https://github.com/kokeb-labs/.github/blob/main/standards/README.md) and in the
[handbook](https://kokeb-labs.github.io/handbook/). This page is the short version for a first pull request. Where
they differ, the standard wins.

## Before you start

- For anything larger than a small fix, open an issue or a discussion first so we can agree on the approach.
- New board? Open a **Board request** first, then start from
  [`board-template`](https://github.com/kokeb-labs/board-template) and run `python3 tools/setup.py`; it produces a
  board repository with its record, its trace and its CI.
- New part or circuit block? Parts go to [`kokeb-libs`](https://github.com/kokeb-labs-open-boards/kokeb-libs) and
  blocks to [`kokeb-blocks`](https://github.com/kokeb-labs-open-boards/kokeb-blocks), each through its review.

## Branches and pull requests

- `main` is the only long-lived branch and only changes through pull requests.
- Branch from `main` as `feat/<topic>`, `fix/<topic>`, `docs/<topic>`, `ci/<topic>` or `chore/<topic>`.
- One change per pull request; prefer under about 400 changed lines of text and split larger work into a series.
  KiCad files change a lot on a small edit: say in the description what you changed in the design.
- Fill in the pull request template: what changed, why, how you verified it.
- Pull requests are squash-merged. The title becomes the commit subject on `main`, so write it as one.
- Add an entry under `## [Unreleased]` in `CHANGELOG.md` for anything a user would notice.

## Commit messages

- Subject in the imperative mood, under about 72 characters, no trailing period: `Add USB-C sink block`.
- An optional body after a blank line says why, not what.
- No attribution trailers other than the sign-off below.

## Sign-off (DCO)

Every commit carries a `Signed-off-by:` line certifying the
[Developer Certificate of Origin](https://developercertificate.org/): that you wrote the change or have the right to
submit it under the repository's licence. Add it with `git commit -s`. The name and email must match the commit
author. CI checks it; a pull request with an unsigned commit can't merge. Edits made in the GitHub web editor are
signed off automatically.

To fix a missing sign-off on your branch: `git rebase --signoff main`, then force-push your branch.

## The CI gate

Every pull request must pass its repository's CI. The one required check is `CI gate / gate`. For a board it runs
Markdown and YAML lint, the trace check and its tests, and the DCO check; ERC and DRC join it when a board has a
KiCad project. Don't merge on red; fix the cause, or fix the check and say why.

## The trace: a change starts at the right item

A board's requirements, risks and tests are data in `trace/`, linked by version
([schema](https://github.com/kokeb-labs/board-template/blob/main/trace/SCHEMA.md)). If you change what something
means, raise its `version` and review every item the check reports as suspect, in the same pull request. Never
reuse an ID. Never mark a requirement approved or a test passed without evidence and a reviewer who did not write it.

## Hardware changes

- Say in the pull request which revision the change is for, and whether anything was built or measured. If not, write
  "not verified on hardware" with the steps someone should run.
- Pins, supply ranges and limits follow the driver's `docs/hardware.yml` and the datasheet revision it names. A
  difference needs an ADR.
- Do not commit vendor datasheets, vendor symbol or footprint files you may not redistribute, or anything with a
  licence that does not allow it. Link the vendor's page and record the revision.
- Everything here is public. No customer data, quotes, prices or credentials.

## Documentation

Update the README, `docs/` and the trace in the same pull request as the design they describe, and the
`CHANGELOG.md` for anything a user would notice.

## Conduct and security

By taking part you agree to the [code of conduct](CODE_OF_CONDUCT.md). Report vulnerabilities privately as
[SECURITY.md](SECURITY.md) describes, never in an issue.
