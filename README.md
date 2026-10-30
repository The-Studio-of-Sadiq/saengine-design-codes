# saengine-design-codes

Design code packs for [SAEngine](https://github.com/The-Studio-of-Sadiq/SAEngine): country and
regional loading, concrete, steel and foundation tables, installable from the app's Packages
page once it exists (marketplace round M3). Each top-level folder is one package
(`<id>/pack.json` and `data/<table>.json`), in the format of SAEngine's `docs/code-packs.md`.

| Package | What it is |
| --- | --- |
| `bnbc2020` | BNBC 2020, Part 6. A **read-only mirror** of the pack built into SAEngine (`mirrors.json` names the commit): change it in SAEngine, then copy it here with `scripts/marketplace/mirror_packages.py` there. |
| `sample-regional-code` | A **synthetic sample** for authors: extends `bnbc2020` and adds two fictional towns. Not for design. |

The SAEngine design code packs still have known limits (docs/code-packs.md, "What follows the
pack"): read them before relying on a pack for member design.

## Adding or changing a package

1. Start from `sample-regional-code` or `saengine codepack new <id> --extends bnbc2020 --dest .`.
2. Give `licence` as an SPDX id: `CC-BY-4.0` for data by default. A pack with `hooks` (Python)
   also needs a code licence SAEngine can run (`CC-BY-4.0 AND AGPL-3.0-only`) and its own line
   in `.github/CODEOWNERS`.
3. Name the source of every value (`sources`, `clauses`, the tables' `$sources`).
4. Raise `version` whenever a published package changes: a published version never changes.
5. Check locally: `saengine codepack validate <folder> --kind designCode`.
6. Open a pull request. CI (`.github/workflows/validate.yml`, defined once in
   [saengine-index](https://github.com/The-Studio-of-Sadiq/saengine-index)) runs SAEngine's
   validator and the repository checks on each changed package.

## Publishing

A maintainer pushes a tag `packages-YYYY-MM-DD` on main. `.github/workflows/publish.yml` zips
each package version not released before, records its size and SHA-256 in `packages.json` and
attaches them to an immutable GitHub Release; saengine-index then lists them in its signed
`index.json`. Running the workflow by hand is a dry run (the files are kept as an artifact).

Licences: each package states its own in `pack.json`; the workflows are AGPL-3.0-only like
SAEngine.
