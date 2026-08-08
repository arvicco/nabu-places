# nabu-places

**The place-matching decisions registry.** Gazetteers of the ancient
world — [Pleiades](https://pleiades.stoa.org/),
[Trismegistos Geo](https://www.trismegistos.org/geo/),
[CIGS](https://zenodo.org/records/14568765),
[GeoNames](https://www.geonames.org/) — already hold the places. What no
shared resource holds is the **matching decision**: which of those
identities a source's verbatim place-name string actually denotes.

Consider three real strings from the corpora this registry serves:

- `"Girsu (mod. Tello)"` (CDLI's house composite) — **matched**:
  `cigs:GIR`, `pleiades:912855`.
- `"Mediolanum"` (an epigraphic corpus's bare name) — six Pleiades
  places carry that title; only a **recorded decision** can say which
  Milan is meant.
- `"Irisagrig (mod. uncertain)"` — the site is unidentified in reality;
  **unlocatable** is the honest answer, not a failed match.

`names.yml` records exactly these judgments, one row per (source,
verbatim string) — and *nothing else*. An unlisted name is unmatched,
visibly: coverage claims stay honest because only decisions are rows
(the identity-default doctrine, inherited from
[nabu-lects](https://arvicco.github.io/nabu-lects/)).

## The row vocabulary

| status | meaning | example |
|---|---|---|
| `matched` | the string denotes these gazetteer identities (`refs` required) | `{refs: [cigs:GIR, pleiades:912855], status: matched}` |
| `unlocatable` | a real ancient place whose site is unidentified (`note` required) | Irisagrig |
| `region` | the string is a regional bin, not a place | "Middle Egypt (from Kairo to Assiut)" |
| `ghost` | an attested string naming no identifiable place | fragmentary toponyms |
| `rejected` | examined and deliberately not matched (`note` required) | homonym ruled out |
| `alias_of` | redirects to another verbatim key in the same section | `"Roma?" → "Roma"` |

`certainty: low` marks upstream-qualified claims (a `?`-suffixed
provenience). Namespaces are declared in `namespaces.yml` with id
shapes; they are **parallel** claims — equivalences between gazetteers
are the gazetteers' own crosswalk data, never inferred here.

See [the schema](schema.html) for the full grammar and
[prior art](prior-art.html) for why this layer exists at all.

## Validation

`bin/validate` (dependency-free Ruby) refuses duplicate source/name
keys (YAML's silent last-wins is a data-loss class), closes the status
vocabulary, checks every ref against its namespace's id shape, and
requires notes where honesty needs them. Consumers re-run it against
their pinned copy.

## License

CC BY 4.0. Maintained as part of the
[Nabu](https://github.com/arvicco/nabu) research infrastructure.
