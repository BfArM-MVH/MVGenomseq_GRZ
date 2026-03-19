# Changelog

## [1.4.0] - 2026-03-19
### Added
- Added `cram` and `gvcf` to `fileType` enum in `sequenceData.files`.
- Added `cram` to the `if/then` block that requires `readLength` (alongside `bam` and `fastq`).
- Added `if/then` constraint at `labData` item level: `tumorCellCount` is now required when `sequenceSubtype` is `"somatic"`.
- Added `contains` / `minContains: 1` constraint on `mvConsent.scope` to enforce that at least one item with `domain: "mvSequencing"` and `type: "permit"` is present.
- Added `minItems: 1` on `donors`, `donors[].labData`, `donors[].researchConsents`, `sequenceData.callerUsed`, and `sequenceData.files` arrays.
- Added `GRZ/examples/` directory with three reference submission examples (single germline, duo tumor/normal, trio rare disease).
- Added GitHub Actions CI workflow (`.github/workflows/validate.yml`) to validate all example files against the schema on every push and pull request.

### Changed
- `sequenceData` is now **required** in `labData` items (was previously optional).
- `mvConsent.presentationDate` is now **required** (was previously optional).
- `fileSizeInBytes` type changed from `"number"` to `"integer"`.
- `additionalProperties` is not constrained, preserving forward-compatibility and allowing institutional extensions alongside required fields.
- Bumped version from `1.3.0` to `1.4.0`.

## [1.3.0] - 2025-10-01
### Added
- Added `noScopeJustification` to `donors.researchConsents`.
- Added `presentationDate` to `donors.researchConsents`.
### Changed
- Changed `researchConsents` items to require either `scope` or `noScopeJustification` (via `oneOf`).
- Updated `researchConsents.schemaVersion` to reflect MII IG Consent v2025.0.1.

## [1.2.3] - 2025-09-05
### Added
- Added `researchConsents` to `donors` required properties.
- Added `noScopeJustification` to `donors.researchConsents`.
### Changed
- Changed `researchConsents` required properties to `presentationDate` and either `scope` or `noScopeJustification`.
