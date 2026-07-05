# Winget Package Identity Convention v0.1

## Convention

Winget package identifiers in this repository follow the
**`Publisher.PackageName`** convention required by the winget manifest schema:

```
<Publisher>.<PackageName>
```

- `Publisher` is the canonical publisher name from the package identity
  registry in `hummbl-dev/packages`.
- `PackageName` is the canonical product name from the same registry.

## Candidate IDs

The following **candidate** winget package identifiers are proposed, pending the
product naming audit in `hummbl-dev/packages`:

| Candidate PackageIdentifier | Publisher | PackageName |
|---|---|---|
| `HUMMBL.HUMMBL` | HUMMBL | HUMMBL |
| `HUMMBL.BaseN` | HUMMBL | BaseN |
| `HUMMBL.Ownward` | HUMMBL | Ownward |

## Status: CANDIDATE

These identifiers are **candidate IDs only**. They are not finalized and must
not be used to publish to winget until the product naming audit in
`hummbl-dev/packages` completes and the canonical package identity registry is
updated.

Once the audit completes, the finalized identifiers will be sourced from the
registry and this document will be superseded by a new versioned convention.

## Non-canon posture

This convention is **non-canon**. Canonical package identity is owned by
`hummbl-dev/packages`. The candidate IDs here are a staging-side proposal for
how canonical identity would project into winget, not an assertion of identity.
