# The schema

Two YAML files; plain data, no code.

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
URL), `geonames`.

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
