# Prior art — and the gap this registry fills

The ancient-world gazetteer landscape is rich; nabu-places adopts it
rather than competing with it. What follows is why a *decisions* layer
is still missing, and what each neighbor actually offers.

## The gazetteers (adopted as data)

- **[Pleiades](https://pleiades.stoa.org/)** — the ancient-world
  gazetteer: ~42k places, Greco-Roman core with a growing Near-Eastern
  layer, daily exports, CC BY. The backbone id namespace: nearly
  everything else crosswalks to it.
- **[Trismegistos Geo](https://www.trismegistos.org/geo/)** — ~65k
  places grown from papyrology; the finest-grained authority for
  Greco-Roman Egypt (nomes, villages, topoi), with multilingual name
  forms (Greek, Demotic, Coptic). CC BY-SA.
- **[CIGS](https://zenodo.org/records/14568765)** — the Cuneiform
  Inscriptions Geographical Site Index (Uppsala): ~600 sites
  purpose-built for the cuneiform corpus, each carrying Pleiades,
  GeoNames, OpenStreetMap *and* CDLI-provenience ids — a crosswalk
  hub in miniature. CC BY.
- **[GeoNames](https://www.geonames.org/)** — the modern-features
  complement (parishes, churches, tells' modern names). CC BY.

## The infrastructure neighbors

- **[Linked Places Format](https://github.com/LinkedPasts/linked-places-format)**
  — a JSON-LD interchange shape for gazetteer records (names,
  timespans, links). An *export dress* for a place layer, not a home
  for matching decisions.
- **[World Historical Gazetteer](https://whgazetteer.org/)** — a union
  index of contributed gazetteers with reconciliation tooling. Its
  reconciliation output stays inside its platform; the decisions are
  not a portable, versioned artifact.
- **Recogito / the Pelagios tradition** — annotation tools that let a
  scholar link a text's place-mention to a gazetteer id. The linking
  act is per-document annotation; corpus-scale per-string decisions
  (this registry's grain) are a different economy.
- **Wikidata** — CC0 crosswalk glue (Pleiades ⇄ Trismegistos ⇄
  GeoNames properties), mineable for equivalences; not an
  ancient-place authority in itself.

## The gap

Every corpus that ships place *names* without machine refs forces each
consumer to redo the same matching — and the hard cases (homonyms like
Mediolanum ×6, `?`-qualified proveniences, genuinely unlocatable sites,
house composite formats) are exactly where silent heuristics go wrong.
Reconciliation tools produce these judgments but don't publish them as
small, reviewable, reusable data.

nabu-places is that missing artifact: **the decisions themselves**,
keyed by the source's verbatim strings, versioned, validated, and
licensed for reuse — the
[nabu-lects](https://arvicco.github.io/nabu-lects/) registry pattern
(identity-default, closed vocabulary, honest non-answers) applied to
place identity.
