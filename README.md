# cambridge-address-import

The **Cambridge city checkout** of the address-import family — city #7,
scaffolded 2026-08-15 by the breadth-first onboarding loop (engine
`future-work/multi-city/onboarding-queue.md`). Status: **onboarding**. No
proposal published, no uploads made; the config is a first draft for
conflation baseline runs.

The pipeline lives in the engine repo,
[`address-importer-friend`](https://github.com/skfd/address-importer-friend)
(see its README for setup). This repo carries only Cambridge's `config.toml`,
credentials (`.env.*`, gitignored, from the `.example` files), and — locally,
gitignored — `data/` with the OSM extract and `data/cambridge/tool.db`.

```bash
cd ../address-importer-friend
python run.py --city-dir ../cambridge-address-import
```

Source data: City of Cambridge address points via the sibling
[`ontario-address-changes`](https://github.com/skfd/ontario-address-changes)
tracker (`data/cambridge/cambridge.db`, 54,025 active rows / 42,132 civic
addresses at snapshot 26, 2026-08-07). The 2026-08-12 portfolio survey put
the gap in the high-80s percent.

Traits (details in config comments): no stable source key (synthetic
identities, the Quinte West shape); ALL-CAPS abbreviated streets (upload
gated on the title-casing TODO); `ADDRESS_LABEL` appends the unit (the
Guelph trap, suffix form); 22% units collapsed to civic; ward 1–8 declared;
STATUS declared protectively (all ACTIVE today). Tiles subdivide the city's
38 "Planning Neighbourhoods" (99.93% point coverage, all names unique) via
the declared-field contract (`NHOOD_NAME`). Cambridge amalgamated
Galt/Preston/Hespeler in 1973; the source carries no former-municipality
field — the neighbourhood fabric encodes locality instead.

Before any production upload: wiki proposal page, forum announcement, and
feedback window per the
[OSM Import Guidelines](https://wiki.openstreetmap.org/wiki/Import/Guidelines)
— Toronto's [`IMPORT_PROPOSAL.mediawiki`](https://github.com/skfd/toronto-2-address-import/blob/main/IMPORT_PROPOSAL.mediawiki)
is the template.

MIT licensed.
