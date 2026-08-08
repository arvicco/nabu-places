# nabu-places

A small, curated registry of **place-matching decisions**: which gazetteer
identity each source's verbatim place-name string denotes. Born from
[Nabu](https://github.com/arvicco/nabu)'s holdings (the
[nabu-lects](https://github.com/arvicco/nabu-lects) pattern applied to
places), universal by construction: any project holding the same source
strings can reuse the same decisions.

## Why a decisions registry

Gazetteers (Pleiades, Trismegistos Geo, CIGS, GeoNames) already cover the
ancient world's names — what no existing framework stores is the *matching
decision*: that EDR's "Mediolanum" means the Insubrian Milan and not one of
its five homonyms, that CDLI's "Girsu (mod. Tello)" is `pleiades:912855`,
that "Irisagrig (mod. uncertain)" is honestly **unlocatable**. Matching by
code heuristics buries those judgments; this registry records them as
reviewable rows.

## The files

- **`names.yml`** — one section per source slug; keys are the source's
  VERBATIM name strings (byte-exact); rows are decisions:
  `{refs: [cigs:GIR, pleiades:912855], status: matched}` ·
  `{status: unlocatable, note: …}` · `{status: region, note: …}` ·
  `{status: ghost}` · `{status: rejected, note: …}` ·
  `{alias_of: "Roma", certainty: low}`.
- **`namespaces.yml`** — the citable gazetteer namespaces and their id
  shapes. Namespaces are parallel; cross-namespace equivalences are the
  gazetteers' own crosswalk data, never inferred here.
- **`bin/validate`** — dependency-free structural validator (run in CI and
  by consumers against their pinned copy).

## The doctrine

**Identity-default honesty**: an unlisted name is unmatched, visibly —
coverage claims stay honest because only decisions are rows. **No fuzzy
matching**: every row was placed by a person (or generated from a
gazetteer's own authority and reviewed), with `note:` provenance on
anything non-obvious. **"Unlocatable" is an answer**, not a failure.

## License

CC BY 4.0 (see LICENSE). Cite as: nabu-places, the place-matching decisions
registry, github.com/arvicco/nabu-places.
