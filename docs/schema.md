# The schema

Three YAML files; plain data, no code.

## names.yml

```yaml
<source-slug>:
  "<verbatim place-name string>": <decision row>
```

- **Section keys** are consuming-catalog source slugs (`cdli`, `oracc`).
- **Name keys** are the source's place-name strings **byte-exact** as
  they occur in that source's data — composites, `?`-suffixes,
  diacritics and all. Never normalized: the string IS the join key.
- **Decision rows**, one of:

```yaml
{refs: [cigs:GIR, pleiades:912855], status: matched}
{refs: [...], status: matched, certainty: low, note: "upstream ?-qualified; ..."}
{status: unlocatable, note: "site unidentified; RGTC 3 s.v."}
{status: region, note: "regional bin, not a place"}
{status: ghost}
{status: rejected, note: "the Umbrian homonym, not this corpus's referent"}
{alias_of: "Roma", certainty: low}
```

Rules (validator-enforced):

- `matched` requires ≥1 ref; every other status forbids refs.
- `unlocatable` and `rejected` require a `note`.
- `alias_of` must target an existing key **in the same section**; alias
  rows carry only `alias_of`/`certainty`/`note`. One hop, no chains.
- `certainty` ∈ `high` (default) · `low`.
- Duplicate section keys and duplicate name keys are refused (YAML
  last-wins silently loses rows otherwise).

## places.yml — the native minting lane

The registry is not only glue: where scholarship (text analysis,
enrichment, AI-assisted argument) establishes a place **no gazetteer
registers**, mint a record here and cite it from names.yml as `np:<ID>`.

```yaml
KARKAR_SU:
  name: Karkar (the Umma-province waterway station)
  lat: 31.9
  lon: 45.7
  evidence: >-
    Identified from the join of CDLI texts P123456/P234567 (the barge
    itineraries name it between Umma and KI.AN); argument in <ref>.
  refs: [cigs:JOK]   # related records — context, never identity
```

Rules (validator-enforced): ids match `[A-Z][A-Z0-9_]{1,23}` (the CIGS
mnemonic style); `name` and **`evidence` are required** — a minted place
is a reviewable scholarly claim; `lat`/`lon` come together or not at all
(absent is honest, never 0,0); `refs` cite *gazetteer* records as context
only — if a gazetteer actually holds the place, **match it in names.yml
instead of minting**; every `np:` ref in names.yml must have a record
here.

## namespaces.yml

```yaml
pleiades:
  name: Pleiades — ancient-world gazetteer
  id_shape: '\d+'
  uri: https://pleiades.stoa.org/places/{id}
```

Every ref's `namespace:` must be declared and its id must match
`id_shape` anchored whole. Current namespaces: `pleiades`, `tm`
(Trismegistos Geo), `cigs` (site mnemonics, e.g. `GIR` — no per-place
URL), `geonames`, and `np` — this registry's own minted records
(places.yml).

## Doctrine, restated as constraints

1. **Identity-default**: an unlisted (source, string) pair is
   unmatched. Consumers must render that as *unmatched*, never guess.
2. **No fuzzy matching**: rows are placed by judgment (or generated
   from a gazetteer's own authority — e.g. CIGS's `legacy_name` IS the
   CDLI composite — and reviewed); the registry never encodes a
   similarity algorithm.
3. **Namespaces are parallel**: a row may cite several, asserting the
   string denotes each; cross-namespace equivalence lives in the
   gazetteers' crosswalk data, not here.
4. **Provenance on anything non-obvious**: `note:` says why, so every
   row is reviewable years later.
