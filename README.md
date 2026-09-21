# HVE Maps

Sovereign placement map for [Human Value Exchange](https://humanvalueexchange.com/).

Five wealth layers on the same Leaflet shell Jameson Lopp used for [physical Bitcoin attacks](https://jlopp.github.io/physical-bitcoin-attacks/) (Unlicense). The attack blotter is gone. The camera stays.

| Layer | Question | Live feeds in `data/` |
|---|---|---|
| Rails | Can you move value here? | BTC Map / OSM places + Bitnodes coords aggregated to countries (**no IPs stored**) |
| Fiscal | Is capital allowed to sit? | Tax Foundation ITCI 2025 + Heritage IEF 2026 snapshot |
| Energy | Cheap firm watts? | Ember yearly electricity (nuclear+hydro share, TWh) + public plant points |
| Vitality | Can a body compound here? | World Bank life expectancy + Aqueduct-style water stress snapshot |
| Time-price | What does an hour buy? | Hours to earn USD 10k from World Bank GNI/capita + PPP GDP/capita |

## Run locally

```bash
python3 -m http.server 8080 --directory .
# open http://localhost:8080
```

Rebuild layers after dropping new extracts as documented in `tools/build_layers.py`:

```bash
python3 tools/build_layers.py
```

## GitHub Pages

Settings → Pages → Deploy from GitHub Actions (workflow in `.github/workflows/static.yml`).
Site: `https://hanshwestphal.github.io/HVE-maps/`

## Why this repo is under HansHWestphal

There is no writable GitHub org named `hveknowops`. The HVE knowledge plane lives at [`HansHWestphal/hve-knowledge-and-operations`](https://github.com/HansHWestphal/hve-knowledge-and-operations). This map is a sibling public repo so Pages can ship without an org.

## Rules

- Public payloads only: regimes and infrastructure.
- No wallet, vault, treasury, or home coordinates.
- Bitnodes IPs are discarded in the ETL.
- Attribute upstream licenses in the footer.

## License

Map shell adapted from Lopp, Unlicense. Layer JSON is a mix of CC BY / official statistics / ODbL (OSM/BTC Map). See footer and `data/manifest.json`.
