---
name: geoskill-hotspot-analysis
description: 'Getis-Ord Gi*热点分析+核密度估计+多尺度显著性检验'
---

# 热点分析 | Hotspot Analysis

Identifies statistically significant hotspots (clusters of high values) and coldspots (clusters of low values) based on the Getis-Ord Gi* statistic, combined with Gaussian kernel density estimation (KDE) and multi-scale analysis. Outputs a Gi* z-score raster, significance-classified rasters at the 90/95/99% levels, and a kernel density raster.

## Core Algorithm / 核心算法

- Getis-Ord Gi* z-score
- Significance classification (90/95/99%)
- Gaussian kernel density estimation + multi-scale

## Dependencies / 依赖

```bash
pip install numpy rasterio scipy geopandas shapely
```

## Usage / 使用方法

### Example 1 (Synthetic Data, Offline)

```bash
python geoskill-hotspot-analysis.py --bbox 116.0 39.0 117.0 40.0 --synthetic --output-dir ./out
```

### Example 2 (Custom Region + Quiet Mode)

```bash
python geoskill-hotspot-analysis.py --bbox 121.0 31.0 122.0 32.0 --synthetic --output-dir ./out2 --quiet
```

### Example 3 (Real Input)

```bash
python geoskill-hotspot-analysis.py --input <your data file> --output-dir ./out3
```

### Example 4 (Extremely Small Region Boundary Test)

```bash
python geoskill-hotspot-analysis.py --bbox 116.39 39.90 116.40 39.91 --synthetic --output-dir ./out4 --quiet
```

## Output / 输出

| File | Format | Description |
|---|---|---|
| `gi_star_zscore.tif` | GeoTIFF/GeoJSON/JSON | Primary output |
| `hotspot_significance.tif` | GeoTIFF/GeoJSON/JSON | Primary output |
| `kernel_density.tif` | GeoTIFF/GeoJSON/JSON | Primary output |
| `hotspot_stats.json` | GeoTIFF/GeoJSON/JSON | Primary output |
| `output-manifest.json` | JSON | Run manifest |

## Data Source / 数据源 / Source

- Synthetic mode: generates physically consistent simulated data locally, with no external data source.
- Real mode: reads local input files, with no network requests.

## Privacy / 隐私声明 / Privacy

- Runs fully offline by default and makes no network requests.
- `--synthetic` mode reads no external data.
- All computation is done locally; user data is never uploaded.

## License / License

MIT

---

> 中文完整版：需要时再读 [references/SKILL.zh-CN.md](references/SKILL.zh-CN.md)，不要默认全量加载。
