# Changelog

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
