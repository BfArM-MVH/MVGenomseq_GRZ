# Changelog

All notable changes to this repository are documented here.
Entries are grouped by component: **GRZ schema**, **Prüfbericht schema**, and **Repository**.

---

## [1.4.0] - 2026-03-19

### GRZ Schema (`GRZ/grz-schema.json`)

#### Added
- `cram` and `gvcf` to `fileType` enum in `sequenceData.files`.
- `cram` to the `if/then` block that requires `readLength` (alongside `bam` and `fastq`).
- `if/then` constraint at `labData` item level: `tumorCellCount` is now required when `sequenceSubtype` is `"somatic"`.
- `contains` / `minContains: 1` constraint on `mvConsent.scope` to enforce that at least one item with `domain: "mvSequencing"` and `type: "permit"` is present.
- `minItems: 1` on `donors`, `donors[].labData`, `donors[].researchConsents`, `sequenceData.callerUsed`, and `sequenceData.files` arrays.

#### Changed
- `sequenceData` is now **required** in `labData` items (was previously optional).
- `mvConsent.presentationDate` is now **required** (was previously optional).
- `fileSizeInBytes` type changed from `"number"` to `"integer"`.
- `additionalProperties` is not constrained, preserving forward-compatibility and allowing institutional extensions.
- Version bumped from `1.3.0` to `1.4.0`.

### Prüfbericht Schema (`Prüfbericht/`)

#### Fixed
- Renamed `Modellvorhaben_SubmissionSchema` → `Modellvorhaben_SubmissionSchema.json` and `submission_example` → `submission_example.json` so that editors and validators recognise them automatically.
- Fixed pre-existing JSON syntax error in `Modellvorhaben_SubmissionSchema.json`: stray backslash and unfinished editorial comment in the `submissionType` description made the file unparseable.

### Repository

#### Added
- `GRZ/examples/` with three reference submissions validated against `grz-schema.json`:
  - `example_single_germline.json` — single WGS germline, rare disease
  - `example_duo_tumor_normal.json` — duo WGS tumor/normal, oncological
  - `example_trio_rare_disease.json` — trio WES, rare disease
- `.github/workflows/validate.yml`: CI that validates GRZ examples against `grz-schema.json` (Draft 2020-12) and the Prüfbericht example against `Modellvorhaben_SubmissionSchema.json` (Draft-07) on every push and pull request.
- `.gitignore` covering internal and IDE files.

#### Changed
- `CHANGELOG.md` moved from `GRZ/CHANGELOG.md` to repository root to cover all components.

---

## [1.3.0] - 2025-10-01

### GRZ Schema (`GRZ/grz-schema.json`)

#### Added
- `noScopeJustification` to `donors.researchConsents`.
- `presentationDate` to `donors.researchConsents`.

#### Changed
- `researchConsents` items now require either `scope` or `noScopeJustification` (via `oneOf`).
- `researchConsents.schemaVersion` updated to reflect MII IG Consent v2025.0.1.

---

## [1.2.3] - 2025-09-05

### GRZ Schema (`GRZ/grz-schema.json`)

#### Added
- `researchConsents` to `donors` required properties.
- `noScopeJustification` to `donors.researchConsents`.

#### Changed
- `researchConsents` required properties changed to `presentationDate` and either `scope` or `noScopeJustification`.
