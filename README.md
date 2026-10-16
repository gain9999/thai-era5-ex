# Thailand Climate Extremes (ERA5-EX)

Interactive map of 34 annual climate-extreme indices over Thailand, 1950–2025, on a 0.1° grid — derived from ERA5-Land.

**Live:** https://gain9999.github.io/thai-era5-ex/

## What you can do

- **Pick any of 34 indices**, grouped: temperature extremes (15), rainfall extremes (11), compound events (8). Each has a plain-language explanation in the panel.
- **Set a year range** with the From/To sliders (default 1950–2025); the map shows the mean over the selected range. Press play to animate single years through the range.
- **Value / Anomaly / Full Mean** — raw value or range mean, difference from the 1991–2020 mean, or the full 1950–2025 mean.
- **Click any grid cell** for the value, anomaly vs 1991–2020, all-time max with its year, cell coordinates, and a 1950–2025 timeseries chart with a draggable marker.

## Data

**ERA5-EX** (Peng et al., 2026): a global 0.1° gridded dataset of 26 ETCCDI indices + 8 bivariate compound-event metrics, computed from ERA5-Land daily temperature and precipitation, 1950–2025.

- Paper: https://doi.org/10.1038/s41597-026-08312-x (*Scientific Data*, CC BY 4.0)
- Dataset: https://doi.org/10.6084/m9.figshare.31812172 (CC BY 4.0)
- Percentile thresholds use the 1961–1990 baseline. Ocean / no-data cells are blank.

Tiles are served dynamically per viewport/zoom (PMTiles) — only the visible area loads. Two resolutions: 0.5° cells at zoom 4–6, full 0.1° cells at zoom 7–8.

## Files

- `index.html` — the viewer (MapLibre GL + OpenFreeMap basemap)
- `<INDEX>.pmtiles` — one per index (34 files, 0.1° cells, zoom 7–8); each cell carries `y1950`…`y2025`, `clim` (1991–2020 mean), `fmean` (1950–2025 mean)
- `<INDEX>_low.pmtiles` — one per index (34 files, 0.5° aggregated cells, zoom 4–6); same properties
- `stats.json` — per-index display ranges and metadata
- `variables.json` — index names, units, plain-language explanations

## Build

The tiles were built from the ERA5-EX NetCDF files (Figshare, ~6 GB) with a Python + tippecanoe pipeline: clip to the Thailand bbox (97–106°E, 5.5–20.5°N), mask fill values, write one GeoJSONL feature per cell with all 76 years as properties, then tile per index. The viewer is a single self-contained `index.html`.
