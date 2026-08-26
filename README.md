# Suburb Screener

**Live site:** https://018503.github.io/propdata/

Interactive property intelligence dashboard for Australian suburbs. Filter, sort, and explore suburb-level data including asking prices, rents, yields, vacancy rates, comparable sales, and auction results.

## Data Sources

- **SQM Research** — asking prices, weekly rents, vacancy rates, gross yields, 3-year time series
- **ABS Census** — renter percentages
- **Domain** — auction listings and results (VIC/NSW)
- **Comparable sales** — recent property sales per suburb

## Tech

- Static HTML + vanilla JS — no build step, no framework
- [DuckDB-WASM](https://duckdb.org/docs/api/wasm/overview) for in-browser Parquet queries (trends, comps, auctions)
- [Chart.js](https://www.chartjs.org/) for visualisations
- Designed for GitHub Pages deployment

## Files

| File | Description |
|------|-------------|
| `index.html` | Single-page app |
| `data/screener.json` | Suburb snapshot (vacancy, prices, yields, growth rates) |
| `data/series.parquet` | 3-year monthly SQM time series |
| `data/comps.parquet` | Comparable sales per suburb |
| `data/auctions.parquet` | Individual auction results (VIC/NSW) |

## Updating Data

Run `build_screener.py` from the parent directory to regenerate all data files from `suburbs.duckdb`:

```bash
python property_agent/build_screener.py
```

Then copy the outputs into `site/data/`.
