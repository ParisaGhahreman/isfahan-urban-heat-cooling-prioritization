# Data Sources

## Landsat 9 Surface Reflectance and Thermal Data

Summer satellite imagery was obtained from the **USGS EarthExplorer** platform.

* Product: Landsat Collection 2, Level-2
* Satellite: Landsat 9
* Path/Row: 164/037
* Spatial resolution: 30 m
* Analysis dates:

  * 2023-07-26
  * 2024-07-28
  * 2025-07-31

The following Landsat bands were used:

| Variable                  | Landsat 9 band | Purpose                           |
| ------------------------- | -------------- | --------------------------------- |
| Red reflectance           | SR_B4          | NDVI calculation                  |
| Near-infrared reflectance | SR_B5          | NDVI calculation                  |
| Surface temperature       | ST_B10         | Land surface temperature analysis |

Source: [USGS EarthExplorer](https://earthexplorer.usgs.gov/)

## Global Human Settlement Layer (GHSL)

Population and built-up surface indicators were obtained from the European Commission Joint Research Centre's Global Human Settlement Layer.

| Dataset     | Reference year | Spatial resolution | Use in this project    |
| ----------- | -------------: | -----------------: | ---------------------- |
| GHS-POP     |           2020 |               1 km | Population exposure    |
| GHS-BUILT-S |           2020 |               1 km | Built-surface exposure |

Source: [Global Human Settlement Layer](https://human-settlement.emergency.copernicus.eu/)

## OpenStreetMap

OpenStreetMap data were used for the Isfahan study boundary, contextual map display, and urban green-space information.

Source: [OpenStreetMap](https://www.openstreetmap.org/)

## Data Availability

Original Landsat and GHSL raster files are not redistributed in this repository because of their file sizes. They can be downloaded from the official sources above. Derived final outputs, including the final 500 m cooling-priority GeoPackage, are provided in this repository.
