# Generated Manifest Contract v0.1

This contract defines how winget manifests are generated in `winget-manifests`
from canonical metadata in `hummbl-dev/packages`.

## Input

Generation consumes two canonical inputs from `hummbl-dev/packages`:

1. **Package identity registry** — the canonical mapping of a HUMMBL package to
   its identity (package id, publisher, product name).
2. **Release artifact receipt** — the canonical record of a specific release
   artifact (version, artifact hash, artifact URL, build provenance).

A manifest is only generated when both inputs are present and consistent.

## Output

The output is a winget YAML manifest conforming to the winget manifest schema,
with **deterministic fields** derived solely from the two inputs. No field is
hand-edited; every field is reproducible from the same inputs.

## Field mapping

Canonical input fields map to winget manifest fields as follows:

| Canonical input | Winget manifest field |
|---|---|
| `packageId` (registry) | `PackageIdentifier` |
| `version` (receipt) | `PackageVersion` |
| `publisher` (registry) | `Publisher` |
| `productName` (registry) | `PackageName` |
| `artifactUrl` (receipt) | `InstallerUrl` |
| `artifactHash` (receipt) | `InstallerSha256` |
| `architecture` (receipt) | `Architecture` |
| `license` (registry) | `License` |
| `shortDescription` (registry) | `ShortDescription` |

Fields not listed here are not populated by the generator unless a future
contract version explicitly adds them.

## Validation

Before a generated manifest is staged, it must be **validated** against the
receipt:

- Every mapped field in the manifest must match the corresponding receipt or
  registry field **exactly**.
- `PackageVersion` must equal the receipt `version`.
- `InstallerSha256` must equal the receipt `artifactHash`.
- `InstallerUrl` must equal the receipt `artifactUrl`.

If any field mismatches, the manifest is invalid and must be regenerated. A
mismatched manifest must not be staged.

## Non-canon posture

Generated manifests are non-canon. The receipt and registry in
`hummbl-dev/packages` are authoritative. This contract describes the
derivation; it does not assert identity.
