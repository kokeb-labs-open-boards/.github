## Summary

<!-- What changes, in one or two sentences. -->

## Why

<!-- The problem this solves. Link the issue, discussion or trace item (N-, R-, H-, V-). -->

## How verified

- [ ] CI green, including `CI gate / gate`
- [ ] Trace check clean: `python3 tools/kb_check.py`
- [ ] On hardware: <!-- board revision, what was built or measured; or "not verified on hardware" plus the steps -->

## Checklist

- [ ] Every commit is signed off (`git commit -s`)
- [ ] The title is an imperative commit subject (it becomes the squash commit)
- [ ] One logical change; no unrelated edits
- [ ] README, `docs/` and `CHANGELOG.md` updated for anything a user would notice
- [ ] Changed items have a new `version`, and every suspect link was reviewed, not just re-stamped
- [ ] No requirement set to `approved`, no verification set to `passed` or board `status` moved without a reviewer
      who did not write the change
- [ ] Pin, supply and limit values match the datasheet revision the driver's `hardware.yml` cites, or an ADR says why
- [ ] No secrets, customer data, prices, vendor datasheets or files I may not redistribute
