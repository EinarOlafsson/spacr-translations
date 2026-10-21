# spaCR translation review sources

This public repository preserves editable, source-bound translation review records used by [spaCR](https://github.com/EinarOlafsson/spacr). The initial import contains exactly 6,472 approved files from spaCR nightly commit 5faff2d18603086a540a6886ab114d55313b46ed, retaining their original paths and bytes. Reviewed records, embedded historical entries and explicitly retired records retain their existing status; publication does not grant human or native-speaker approval.

`manifest.json` binds every source path to its size and SHA-256. spaCR pins this repository by full Git commit and manifest digest in `docs/translation_reviews_revision.json`. Generated API catalogs remain separately published through the existing Hugging Face pin; runtime distributions bundle their generated translations and do not fetch this repository at runtime.

## Authoring

Clone this repository alongside spaCR. From spaCR, write newly reviewed API records with `python tools/write_reviewed_api_record.py --help` and `--review-root /path/to/spacr-translations/docs/i18n/reviewed`. Preserve unrelated entries and source-bound review metadata. Other production review writers must likewise target this checkout. Follow spaCR's technical and language peer-review requirements; do not promote retired records.

After reviewed changes, run `python /path/to/spacr/tools/bootstrap_translation_reviews.py manifest --source .` here, commit the changed records and manifest, and push. In spaCR, run `python tools/bootstrap_translation_reviews.py pin --revision FULL_PUBLISHED_COMMIT`, then restore inputs in a fresh worktree with `python tools/bootstrap_translation_reviews.py fetch`. Hydration refuses differing local edits. Run the owning checks and normal generators, publish changed generated catalogs through their existing producer, and commit the new spaCR pin. See spaCR `docs/i18n/TRANSLATION_INPUTS.md` for offline-cache and consumer instructions.

The Git history starts with this byte-preserving import; earlier source history remains in the spaCR repository. The accompanying license is copied unchanged from spaCR.
