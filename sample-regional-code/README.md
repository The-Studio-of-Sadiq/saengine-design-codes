# SAMPLE regional code (synthetic, not for design)

This package is a **sample** for authors of regional design codes. Every value in it is made
up. It names no real place and comes from no code, standard or gazette: **never use it for a
design.**

What it shows:

- `pack.json` with `extends: "bnbc2020"`: every table it does not provide comes from BNBC 2020
  unchanged;
- `covers: ["locations"]` and `data/locations.json`, which adds two fictional towns to BNBC
  2020's list (towns are merged by their key; the parent's towns stay);
- `requires.packages`, so the app offers to install BNBC 2020 first if it is missing;
- `sources` and `clauses`, which the design report prints next to each value: a real package
  names the document, table and page of every value.

To start your own: copy this folder, change `id`, `name`, `version`, `country`/`region`,
`sources` and the data, then run `saengine codepack validate <folder> --kind designCode` and see
docs/code-packs.md in the SAEngine repository for every table.

Licence: CC0-1.0 (copy it freely).
