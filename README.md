# Thailand Climate Extremes (ERA5-EX)

Interactive map of 34 annual climate-extreme indices over Thailand, 1950–2025, on a 0.1° grid — derived from ERA5-Land.

**Live viewer:** open `index.html` (served via GitHub Pages)

## What you can do

- **Pick any of 34 indices**, grouped: temperature extremes (15), rainfall extremes (11), compound events (8). Each has a plain-language explanation in the panel.
- **Scrub 1950–2025** with the year slider, or press play to animate.
- **Value / Anomaly toggle** — raw index value, or difference from the 1991–2020 mean.
- **Click any grid cell** for that year's value, the 1991–2020 mean, and the anomaly.

## Data

**ERA5-EX** (Peng et al., 2026): a global 0.1° gridded dataset of 26 ETCCDI indices + 8 bivariate compound-event metrics, computed from ERA5-Land daily temperature and precipitation, 1950–2025.

- Paper: https://doi.org/10.1038/s41597-026-08312-x (*Scientific Data*, CC BY 4.0)
- Dataset: https://doi.org/10.6084/m9.figshare.31812172 (CC BY 4.0)
- Percentile thresholds use the 1961–1990 baseline. Ocean / no-data cells are blank.

Tiles are served dynamically per viewport/zoom (PMTiles) — only the visible area loads.

## Files

- `index.html` — the viewer (MapLibre GL + OpenFreeMap basemap)
- `<INDEX>.pmtiles` — one per index (34 files); each cell carries `yr`, `val`, `clim` (1991–2020 mean)
- `stats.json` — per-index display ranges and metadata
- `variables.json` — index names, units, plain-language explanations

## Build

See `~/workspace/era5ex/` for the extraction scripts (`extract.py`, `varstats.py`, `gen_html.py`).
