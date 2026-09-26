# Changelog

## Unreleased

- `names.yml`: + `kanripo` section, 10 rows — the first decisions from
  the Kanseki Repository × CHGIS text-mining review (top-50 board by
  document spread, 2026-09-26): 1 matched (杜陵 → `chgis:hvd_70633`,
  the Han county under 京兆尹, span 23–264), 4 region records (江北 ·
  西江 · 天竺 · 三江 — real geography no CHGIS administrative row
  matches; every offered candidate a 1911 village homonym), 5 rejected
  wrong-identities with the real referent named in the note (中都 ·
  平江 · 京口 · 南城 · 王城). The board's 40 generic-vocabulary
  collisions went to the consumer's stop list, not this registry;
  unlisted names stay honestly unmatched.

- `namespaces.yml`: + `chgis` (CHGIS/TGAZ, the China Historical GIS
  Temporal Gazetteer, Harvard–Fudan; id shape `hvd_\d+`, TGAZ
  placename URI). Consumer: Nabu's P96 chgis place-index module
  (82,117 historical placenames, CC0) — refs like `chgis:hvd_1` may
  now enter decisions and crosswalks.

## Unreleased — 2026-08-08 (the mint)

- Schema: `names.yml` (source → verbatim string → decision row; statuses
  matched · unlocatable · region · ghost · rejected; alias_of; certainty)
  + `namespaces.yml` (pleiades, tm, cigs, geonames with id shapes) +
  `bin/validate` (dependency-free; refuses duplicate source/name keys —
  the YAML last-wins shadowing class).
- Seed wave (generated from CIGS v1.7's own keys, reviewed): **cdli 133
  rows** (92 exact legacy_name matches + 40 `?`-suffix aliases + 1
  unique-name match; covers 250,484/273,210 docs) · **oracc 131 rows**
  (16 legacy + 115 unique anc/transc name matches; covers
  87,706/112,198). Two ambiguous oracc names and the 395-name long tail
  deliberately UNLISTED (identity-default: unmatched is visible).

## Unreleased — 2026-08-09

- Doctrine correction (owner ruling): nabu-places is NOT only glue —
  `places.yml` + namespace `np:` mint the registry's OWN place records
  where scholarship establishes a place no gazetteer registers.
  Evidence required per record; validator enforces np-ref existence,
  evidence presence, lat/lon pairing, and related-refs-are-context.

- 2026-08-09 · crosswalks.csv: 2,108 tm⇄pleiades equivalences harvested
  from Wikidata (P1958⇄P1584, CC0; SPARQL, retrieved 2026-08-09) with
  per-row source+date provenance; validator checks namespaces/shapes.
