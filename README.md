# Florida Monthly NDVI, Surface Water, Precipitation & Soil Moisture (2019–2024)

This repository provides a monthly summary of four key climate and environmental indicators for the state of Florida from January 2019 to December 2024. Using Google Earth Engine (GEE), the project extracts spatially averaged values of vegetation greenness, surface water occurrence, rainfall, and surface soil moisture across the state boundary.

## Dataset Summary

| Variable               | Source Dataset                                               | Description                                | Resolution   |
|------------------------|--------------------------------------------------------------|--------------------------------------------|--------------|
| NDVI                  | `COPERNICUS/S2_SR_HARMONIZED`                               | Vegetation index from Sentinel-2 imagery   | 10–30 meters |
| Surface Water         | `JRC/GSW1_4/MonthlyHistory`                                  | Monthly water class mode (open water only) | 30 meters    |
| Precipitation         | `UCSB-CHG/CHIRPS/DAILY`                                      | Daily precipitation, monthly summed        | ~5 km        |
| Surface Soil Moisture| `NASA/SMAP/SPL4SMGP/007`                                     | Surface layer root-zone moisture content   | ~9 km        |

## Methodology

- **NDVI** is computed using the normalized difference between NIR (B8) and Red (B4) bands of Sentinel-2. Monthly median composites are used after cloud filtering.
- **Surface Water** is extracted from JRC Global Surface Water by calculating the monthly mode of the water classification (class 2 = water).
- **Precipitation** is obtained from CHIRPS daily data and summed for each month.
- **Soil Moisture** uses SMAP Level-4 monthly mean surface values (`sm_surface`).
- All values are spatially averaged across the Florida state boundary using U.S. Census TIGER/Line shapefiles.

## Output

The final output is a CSV file with the following structure:

| Column              | Description                                               |
|---------------------|-----------------------------------------------------------|
| `date`              | Month in `YYYY-MM` format                                 |
| `mean_ndvi`         | Mean NDVI across Florida (unitless)                       |
| `mean_water`        | Mean surface water fraction (0–1, where 1 = full water)   |
| `mean_precip_mm`    | Total monthly precipitation (mm)                          |
| `mean_smap_surface` | Mean surface soil moisture (m³/m³)                        |

## Applications

- Monitoring seasonal flooding, wetland dynamics, and vegetation response  
- Evaluating the effects of rainfall and drought on Florida’s ecosystems  
- Supporting coastal zone management, agricultural planning, and climate risk mapping  
- Useful in understanding linkages between water availability, greenness, and precipitation in a hurricane-prone, wetland-dominant state

## Data Access

- [Sentinel-2 SR Harmonized (`COPERNICUS/S2_SR_HARMONIZED`)](https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR_HARMONIZED)
- [JRC Global Surface Water (`JRC/GSW1_4/MonthlyHistory`)](https://developers.google.com/earth-engine/datasets/catalog/JRC_GSW1_4_MonthlyHistory)
- [CHIRPS Precipitation (`UCSB-CHG/CHIRPS/DAILY`)](https://developers.google.com/earth-engine/datasets/catalog/UCSB_CHG_CHIRPS_DAILY)
- [SMAP Surface Soil Moisture (`NASA/SMAP/SPL4SMGP/007`)](https://developers.google.com/earth-engine/datasets/catalog/NASA_SMAP_SPL4SMGP_007)
- [Florida Boundary (U.S. Census TIGER)](https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html)

## License

This dataset is derived from publicly available sources including:

- NASA SMAP Level-4 surface soil moisture products  
- Copernicus Sentinel-2 imagery (NDVI)  
- JRC Global Surface Water data  
- CHIRPS precipitation data from UCSB/CHG  
- U.S. Census TIGER/Line shapefiles for state boundaries

The dataset was processed using Google Earth Engine.  
Users are free to use, share, and adapt this data for research, education, and public use.  
Please cite the original data providers appropriately when using or referencing this dataset.
