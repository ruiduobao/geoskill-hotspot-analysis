# Hotspot Analysis (geoskill-hotspot-analysis)

> Getis-Ord Gi* hotspot analysis + kernel density estimation + multi-scale significance testing

---

## 1. Overview

Identifies statistically significant hotspots (clusters of high values) and coldspots (clusters of low values) using the Getis-Ord Gi* statistic, combined with Gaussian kernel density estimation (KDE) and multi-scale analysis. Outputs Gi* z-score raster, 90/95/99% significance level rasters, and kernel density raster.

## 3. Quick Start

```bash
pip install -r requirements.txt
python geoskill-hotspot-analysis.py --bbox 116 39 117 40 --synthetic --output-dir ./out
```

## 4. CLI Parameters

Run `python <skill>.py --help` for the full list. Common parameters:

| Parameter | Type | Description |
|---|---|---|
| `--bbox` | `float[4]` | WGS84 bounding box `min_lon min_lat max_lon max_lat` |
| `--input` | `path` | Local input file (GeoJSON/GeoTIFF/etc.) |
| `--output-dir` | `path` | Output directory (default `./output`) |
| `--synthetic` | `flag` | Use synthetic data instead of real input |
| `--quiet` | `flag` | Suppress non-essential stdout |

## 5. Input / Output

| File | Format | Description |
|---|---|---|
| `gi_star_zscore.tif` | GeoTIFF/GeoJSON/JSON | Primary output |
| `hotspot_significance.tif` | GeoTIFF/GeoJSON/JSON | Primary output |
| `kernel_density.tif` | GeoTIFF/GeoJSON/JSON | Primary output |
| `hotspot_stats.json` | GeoTIFF/GeoJSON/JSON | Primary output |
| `output-manifest.json` | JSON | Run manifest |


## 6. Technical Principle

- Getis-Ord Gi* z-score
- Significance classification (90/95/99%)
- Gaussian kernel density estimation + multi-scale

## 8. License

MIT License. See [`LICENSE`](./LICENSE) for full text.

---

> 中文完整版：[references/SKILL.zh-CN.md](references/SKILL.zh-CN.md)
