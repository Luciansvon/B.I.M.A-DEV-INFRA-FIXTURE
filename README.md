# B.I.M.A-DEV-INFRA consumer fixture

Minimal, data-only repository used to verify published reusable workflows from [B.I.M.A-DEV-INFRA](https://github.com/Luciansvon/B.I.M.A-DEV-INFRA).

## Active consumer

`repository-audit.yml` calls the reusable repository audit with the same reviewed full commit SHA in both required locations:

```text
workflow reference -> cb220412bf3d7be0e67cc364572eaf0183cda286
infra-ref input    -> cb220412bf3d7be0e67cc364572eaf0183cda286
```

The shared workflow checks this repository as untrusted data. It does not execute project code, use secrets, publish artifacts beyond retained audit evidence, or copy shared implementation into this repository.

## Release publication

`release-fixture.yml` uploads one asset and calls `release.yml` with a manual tag input, `RELEASE-NOTES.md`, the triggering commit SHA and a dry-run-free publication. The template creates the draft first, publishes it, and retains `release.json` with per-asset SHA-256.

## Expected evidence

Each run retains the raw repository-audit result, human-readable report, canonical evidence, execution metadata, and canonical SHA-256 for 14 days. A passing result intentionally creates no agent packet. Release runs retain `release-validation.txt` and `release.json` for 14 days.
