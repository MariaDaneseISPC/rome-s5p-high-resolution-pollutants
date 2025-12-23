**Rome S5P High-Resolution Pollutants Dataset**

This repository contains code, input data references, and final datasets associated with a reproducible workflow for generating high-resolution, spatially continuous atmospheric pollutant data derived from Sentinel-5P (TROPOMI) over the Rome metropolitan area.

The workflow relies exclusively on open-access satellite, climatic, and ancillary datasets and is implemented primarily in Google Earth Engine (GEE).

---

**Repository structure**

The repository is organised as follows:

rome-s5p-high-resolution-pollutants/
├── README.md
├── LICENSE
├── data/
│ ├── input_static/
│ │ ├── study_area/
│ │ ├── dem/
│ │ ├── road_density/
│ │ └── industrial_density/
│ ├── environmental_variables/
│ └── pollutants/
├── scripts/
│   ├── S5P_gapfill_downscale_clean.js
│   ├── S5P_gapfill_downscale_debug.js
│   ├── S5P_overpass_time_selector.js
│   └── imports_example.js

---

**Data description**

Each daily archive contains:

raw Sentinel-5P pollutant column data (NO₂, SO₂, CO) at native resolution (~3.5 × 7 km),

gap-filled and downscaled pollutant maps at 500 m spatial resolution,

ancillary explanatory variables (meteorological, morphological, anthropogenic) provided both at native resolution and harmonized to 500 m.

All raster datasets are provided in GeoTIFF format, projected in WGS84 (EPSG:4326).



**File naming convention**

Daily files follow this convention:

ERA5_CHIRPS_raw_YYYYMMDD.tif

ERA5_CHIRPS_500m_downscaled_YYYYMMDD.tif

P_column_raw_YYYYMMDD.tif

P_column_500m_gapfilled_YYYYMMDD.tif

where P is replaced by the pollutant name (NO2, SO2, CO) and YYYYMMDD indicates the acquisition date.

Files are compressed into daily ZIP archives to reduce storage size.



**Scripts**

The scripts folder contains all Google Earth Engine code used to generate and validate the dataset:

S5P_gapfill_downscale_clean.js
Clean, publication-ready version of the workflow used for:

meteorological data downscaling,

Sentinel-5P gap-filling and spatial downscaling to 500 m,

export of final raster products and validation tables.

S5P_gapfill_downscale_debug.js
Extended debug version including:

diagnostic prints,

map visualizations,

intermediate checks useful for testing, inspection, and adaptation of the workflow.

S5P_overpass_time_selector.js
Utility script used to identify the optimal Sentinel-5P overpass time over the study area by maximizing the number of valid pixels, providing the time window used as input for the main workflow.

imports_example.js
Example file illustrating the required Google Earth Engine imports (study area, static variables, DEM).
Since GEE asset paths are user-specific, users must upload the corresponding datasets to their own GEE accounts and update asset paths accordingly.



**Requirements**

To run the scripts, users need:

a Google Earth Engine account,

uploaded assets corresponding to:

study area geometry,

road density raster,

industrial density raster,

digital elevation model (DEM).

An example of the required imports is provided in imports_example.js.



**License**

All data and code in this repository are released under the CC0 1.0 Universal (Public Domain Dedication) license, unless otherwise specified.



**Citation**

If you use this dataset or code, please cite the associated data paper (to be added upon publication).

**Notes**

This dataset is intended to support spatial analyses of atmospheric pollutant distributions at the urban scale and applications in environmental monitoring and cultural heritage studies. Satellite-derived products should be interpreted considering their physical meaning and spatial representativeness.
