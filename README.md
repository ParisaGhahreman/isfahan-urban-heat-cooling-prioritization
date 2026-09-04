# Urban Heat Cooling Intervention Prioritization in Isfahan

A GIS and remote-sensing workflow for identifying and mapping priority areas for urban cooling interventions in Isfahan, Iran.

## Overview

This project integrates summer land surface temperature (LST), vegetation condition, population exposure, and built-up surface exposure to prioritize urban areas that would benefit most from cooling interventions, such as urban greening, shade provision, cool materials, and heat-resilient public-space design.

The final output is a three-level cooling-intervention priority map at a 500 m grid resolution:

* Low priority
* Medium priority
* High priority

## Study Area

**Isfahan, Iran**

The analysis uses a 500 × 500 m grid covering the municipal study boundary. The final analytical layer contains **2,296 grid cells** and covers approximately **549.17 km²**.

## Data Sources

* Landsat 9 Collection 2 Level-2 imagery for summer dates in 2023, 2024, and 2025
* GHSL population data (2020)
* GHSL built-up surface data (2020)
* OpenStreetMap boundary and contextual map data

Detailed source information is available in [`docs/data_sources.md`](docs/data_sources.md).

## Methodology

1. Seasonal LST and NDVI layers were created from Landsat 9 imagery for 2023–2025.
2. Median summer LST and NDVI composites were calculated to reduce the effect of single-date variability.
3. GHSL population and built-surface data were integrated into the 500 m analysis grid.
4. Thermal hotspot share, low-vegetation share, population exposure, and built-surface exposure were normalized and combined into a final cooling-priority score.
5. Final scores were classified into three classes using the **Equal Count (Quantile)** method.

### Final Classification Thresholds

| Priority class | Final priority score |
| -------------- | -------------------: |
| Low            |        0.0000–0.1467 |
| Medium         |       >0.1467–0.3206 |
| High           |       >0.3206–0.7293 |

## Key Results

| Priority level | Grid cells | Area (km²) | Share of study area |
| -------------- | ---------: | ---------: | ------------------: |
| Low            |        766 |     181.18 |               33.0% |
| Medium         |        770 |     186.86 |               34.0% |
| High           |        760 |     181.12 |               33.0% |
| Total          |      2,296 |     549.17 |                100% |

High-priority areas are concentrated mainly in the southern and south-central parts of Isfahan, with additional clusters along a central-to-east corridor and smaller clusters in northern and northwestern areas.

## Project Structure

```text
├── data/
│   ├── raw/                 # Source data and input layers (large rasters excluded from Git)
│   └── processed/           # Final vector layers and derived GIS outputs
├── docs/
│   ├── data_sources.md
│   ├── methodology_notes.md
│   └── MASTER_DOCUMENTATION.md
├── notebooks/
│   └── 01_Data_Inventory_and_Quality_Control.ipynb
├── outputs/
│   ├── figures/             # Publication-ready maps
│   └── tables/              # Descriptive and priority-area tables
├── Isfahan_Urban_Heat_Cooling_Prioritization.qgz
└── README.md
```

## Main Outputs

* **Figure 01:** Median summer LST map (2023–2025)
* **Figure 02:** Median summer NDVI map (2023–2025)
* **Figure 03:** Built-surface fraction map
* **Figure 04:** Population-density map
* **Figure 05:** Urban cooling intervention priority map
* **Figure 06:** Final cooling-intervention priority map with OpenStreetMap context
* **Table 02:** Descriptive statistics of spatial indicators and final priority scores
* **Table 03:** Area distribution of cooling-intervention priority classes

## Reproducibility

The project was developed in **QGIS 3.44** using the project file:

```text
Isfahan_Urban_Heat_Cooling_Prioritization.qgz
```

Large raw raster datasets are not included in this repository because of file-size limitations. They can be downloaded from their original sources listed in `docs/data_sources.md`.

## License

A license file will be added before the first public release.

## Citation

A `CITATION.cff` file will be added before the first public release.
## License

A license file will be added before the first public release.

## Citation

A `CITATION.cff` file will be added before the first public release.
