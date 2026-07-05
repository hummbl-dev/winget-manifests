# Staging Policy v0.1

## Scope

`winget-manifests` is a **downstream generated/staging surface** for HUMMBL CLI
releases. It is not a source of truth for package identity, release metadata, or
artifact integrity.

## Sources of truth

- **Canonical package metadata** lives in [`hummbl-dev/packages`](https://github.com/hummbl-dev/packages),
  including the package identity registry and release artifact receipts.
- **Manifests** in this repository are generated from that canonical metadata
  plus the corresponding release artifact receipts.

## What this repo tracks

This repository tracks **manifest generation and staging** only:

- Generated winget YAML manifests
- The mapping from canonical package metadata to winget manifest fields
- Staging state for manifests pending publication to winget

This repository does **not** track canonical identity. Package identifiers,
product names, and publisher identity are owned by `hummbl-dev/packages`.

## Non-canon posture

This repository is **non-canon**. Any field value that appears in a manifest
here is a derived projection of canonical metadata and is not authoritative.
If a manifest field conflicts with the corresponding receipt or registry entry
in `hummbl-dev/packages`, the canonical source wins and the manifest must be
regenerated.

## Versioning

This policy is versioned (`v0.1`) and may be revised. Changes to the staging
policy must be recorded as a new versioned document and referenced from a
receipt in `receipts/`.
