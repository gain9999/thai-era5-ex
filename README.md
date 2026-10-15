# Thailand Flood Events — Groundsource

Interactive map of **70,795 flood events in Thailand (2000–2026)** from the [Groundsource](https://gee-community-catalog.org/projects/groundsource/) global dataset. Live site: `https://gain9999.github.io/thai-groundsource/`

## What's here

- `index.html` — MapLibre viewer (PMTiles vector tiles, dynamic per-viewport loading)
- `thailand_floods.pmtiles` — 70,795 flood polygons, zoom levels 4–10 (8.0 MB)
- `stats.json` — per-year event counts

## Features

- Flood polygons colored by event start year (2000 → 2026)
- Year-range filter, minimum-area filter
- Click any event for start/end dates, duration, and area
- Per-year bar chart
- Tiles load dynamically based on map view and zoom — low zooms show a thinned sample, zoom in for full detail

## Data

Thailand subset extracted from `groundsource_2026.parquet` (2,646,302 global events), bounding box 97–106°E, 5.5–20.5°N, then clipped to Thailand's GADM country boundary: 28,402 events falling entirely outside Thailand (neighboring countries, sea) were removed, leaving 70,795. Date range: 2000-11-20 to 2026-01-26.

Each event: polygon boundary (WGS 84), start/end date, area in km². The dataset is **entity-based, not meteorology-based** — one large flood may appear as multiple entries for different reported places.

Known biases (from the authors): strong recency bias (~64% of events 2020–2025, reflecting digitized news growth, not flood frequency); spatial media bias (coverage follows digital news infrastructure); severity-dependent recall (high-impact events over-represented); geocoding errors may cluster regionally.

## Citation

> Mayo, R., Zlydenko, O., Bootbool, M., Fronman, S., Gilon, O., Hassidim, A., Kratzert, F., Loike, G., Matias, Y., Nakar, Y., Nearing, G., Sayag, R., Sicherman, A., Zemach, I., & Cohen, D. (2026). *Groundsource: A Dataset of Flood Events from News.* EarthArXiv. Unreviewed preprint.

Dataset: [doi.org/10.5281/zenodo.18647054](https://doi.org/10.5281/zenodo.18647054) — CC BY 4.0
