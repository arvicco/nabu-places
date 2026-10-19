# Changelog

## Unreleased

- 2026-10-19 · `names.yml`: the cdli provenience wave, 63 rows over
  the 134 composites CDLI's catalogue carries with no decision
  (22,726 documents). 35 matched — 28 through CIGS v1.7 sites held
  under a differing composite (CIGS id + its Pleiades record; ancient
  and modern names agree, e.g. Ebla = Tall Mardīkh, Bābili = Babylon,
  Kalhu = Nimrūd; Imgur-Enlil takes TM 54483 because the Pleiades id
  CIGS cites no longer resolves), 7 through Pleiades/TM records found
  by name where CIGS has none (Dūr-Abī-ēšuḫ, Lagaba, Abdju/Abydos,
  Kesh at Tell Wilaya, Gišša at Umm al-Aqarib, Kar-Mullissu,
  Hursagkalama); 3 at certainty low (Kish at Barguthiat — CIGS's
  Girumu mound; Kulišhinaš, which CIGS keys to Amuda against the
  composite's "uncertain"; upstream-?-qualified Malgium). 26 aliases — upstream
  ?-qualified variants (low), current spellings of seed keys
  (Šuruppak, Irisaĝrig), stray-character variants, Agamatanu →
  Ecbatana, Carchemish (mod. Europos) → Karkemish, Chagar Bazar →
  Ašnakkum. 1 region (Umma region), 1 rejected (Elbonia, upstream's
  placeholder for modern forgeries). Reach: 22,104 of the 22,726
  documents. 71 names (424 documents) deliberately unlisted —
  unidentified Neo-Assyrian/Neo-Babylonian settlements with no
  gazetteer record, fragmentary names, a two-site composite, and
  homonym-ambiguous strings.

- 2026-10-10 · namespaces.yml: the `thurayya:` namespace — the
  al-Ṯurayyā Gazetteer of the early Islamic world (Romanov, Seydi et
  al.; data CC BY 4.0 per the project's DATA-LICENSE.md, 2026-09-22).
  Id shape is upstream's own recipe: transliteration stem +
  tenth-degree coordinate stamp + class letter (R/S/W/O), e.g.
  BAGHDAD_443E333N_S. 2,331 referenceable places (xroads route
  junctions carry placeholder names and are not referenced).

- `namespaces.yml`: + `nrct` — the 日本歴史地名大系 placename dataset
  (80,502 entries, CC BY 4.0, DOI 10.20676/00000448; Heibonsha's
  historical gazetteer as published machine-readable by ROIS-DS/NII
  geoshape). Id shape `\d{12}` (the dataset's own 12-digit ids,
  censused over the full 2025-07-19 CSV cut); the URI template is the
  dataset's per-entry resource page. Opens the Japanese places lane:
  the consumer derives an `nrct` place-index slice (name keys = 地名
  verbatim + reading) on the chgis mold.

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
