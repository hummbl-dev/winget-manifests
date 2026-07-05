# Receipt: winget-manifests bootstrap v0.1

- **Repo:** `hummbl-dev/winget-manifests`
- **Branch:** `feat/devin/bootstrap-policy`
- **Action:** Bootstrap staging policy, generated-manifest contract, and winget
  package identity convention.

## Documents introduced

| Path | Purpose |
|---|---|
| `policy/staging-policy-v0.1.md` | Defines this repo as a downstream generated/staging surface from `hummbl-dev/packages`; non-canon posture. |
| `policy/generated-manifest-contract-v0.1.md` | Defines input (identity registry + release artifact receipt), output (winget YAML), field mapping, and validation rules. |
| `policy/package-identity-convention-v0.1.md` | Candidate winget package IDs (`HUMMBL.HUMMBL`, `HUMMBL.BaseN`, `HUMMBL.Ownward`) pending product naming audit. |

## Posture

- This repository is **non-canon**. Canonical package identity and release
  metadata remain owned by `hummbl-dev/packages`.
- Candidate package IDs are **not finalized** and must not be used to publish
  until the product naming audit completes.

## Issues addressed

- Closes #1 — Bootstrap winget staging policy and generated-manifest contract
- Closes #2 — Define winget package identity convention (candidate IDs)
