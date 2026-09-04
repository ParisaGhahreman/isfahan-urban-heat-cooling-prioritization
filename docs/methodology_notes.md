# Methodology Notes

## Objective

The objective of this workflow is to identify 500 m urban grid cells in Isfahan that should be prioritized for cooling interventions.

The final priority score integrates thermal stress, vegetation deficiency, population exposure, and built-surface exposure.

## Spatial Framework

* Study area: Isfahan, Iran
* Analysis grid: 500 × 500 m
* Coordinate reference system: EPSG:32639
* Number of final grid cells: 2,296
* Total analytical area: approximately 549.17 km²

Boundary cells were clipped to the study-area boundary; therefore, some cells have an area smaller than 0.25 km².

## Seasonal Thermal and Vegetation Indicators

Landsat 9 imagery from 2023, 2024, and 2025 was used to create median summer composites.

### Land Surface Temperature

Land Surface Temperature (LST) was derived from the Landsat Level-2 surface-temperature product. A median summer LST composite was produced from the three available summer dates to reduce single-date variability.

### Normalized Difference Vegetation Index

NDVI was calculated as:

```text
NDVI = (NIR − Red) / (NIR + Red)
```

where:

* NIR = Landsat 9 SR_B5
* Red = Landsat 9 SR_B4

A median summer NDVI composite was then produced for 2023–2025.

## Cooling-Need Score

Two spatial indicators were derived for each 500 m cell:

* `hot_mean`: share of the cell classified as a thermal hotspot
* `lowveg_mean`: share of the cell classified as low vegetation

Thermal hotspots were defined using the upper 20 percent of summer LST values. Low-vegetation areas were defined using the lower 20 percent of summer NDVI values.

The cooling-need score was calculated as:

```text
cooling_need = 0.60 × hot_mean + 0.40 × lowveg_mean
```

## Exposure Indicators

Two exposure components were derived from GHSL data:

* `population_exposure`: normalized population-related exposure
* `built_exposure`: normalized built-surface-related exposure

Population and built-surface indicators were evaluated in the spatial context surrounding each grid cell using GHSL data.

## Final Cooling-Priority Score

The final priority score was calculated as:

```text
final_priority_score =
    0.70 × cooling_need
  + 0.20 × population_exposure
  + 0.10 × built_exposure
```

This weighting gives the greatest importance to heat and vegetation conditions while still considering where people and built infrastructure are exposed.

## Priority Classification

Final scores were classified into three groups using the Equal Count (Quantile) method:

| Priority level |    Score range |
| -------------- | -------------: |
| Low            |  0.0000–0.1467 |
| Medium         | >0.1467–0.3206 |
| High           | >0.3206–0.7293 |

## Final Outputs

* Final grid layer: `data/processed/isfahan_final_cooling_priority_500m.gpkg`
* Publication-ready maps: `outputs/figures/`
* Summary tables: `outputs/tables/`
