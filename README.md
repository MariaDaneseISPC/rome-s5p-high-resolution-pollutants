# Rome S5P High-Resolution Pollutants Dataset

This repository contains code, input data references, and final datasets associated with a reproducible workflow for generating high-resolution, spatially continuous atmospheric pollutant data derived from Sentinel-5P (TROPOMI) over the Rome metropolitan area.

The workflow relies exclusively on open-access satellite, climatic, and ancillary datasets and is implemented primarily in Google Earth Engine (GEE).

---

## Repository structure

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
└── scripts/

---

## Data description
## Data format and spatial reference

All datasets used as predictors and generated through the presented workflow are provided in **GeoTIFF format**, projected in the **World Geodetic System 1984 (EPSG:4326)**.

### `data/input_static/`
This folder contains static spatial layers used as ancillary predictors in the workflow:
- **study_area/**: area of interest (Rome metropolitan area)
- **dem/**: Digital Elevation Model (TINITALY)
- **road_density/**: road network density derived from OpenStreetMap
- **industrial_density/**: industrial buildings and areas derived from OpenStreetMap

---

### `data/environmental_variables/`
This folder contains environmental and meteorological variables (e.g. ERA5-Land, CHIRPS, NDVI) used as predictors.

### `data/pollutants/`
This folder contains Sentinel-5P atmospheric pollutant data (e.g. NO₂, SO₂, CO).

Data are provided as **daily compressed archives**, each including both raw and downscaled products for the same acquisition date.

## Daily data organisation

Data are organised as **daily compressed ZIP archives**, each corresponding to a single date of acquisition or reference day.

Each daily archive may contain:

- daily atmospheric pollutant maps for **NO₂, SO₂, and CO** over the Rome metropolitan area at the native Sentinel-5P spatial resolution (approximately **3.5 × 7 km**);
- daily atmospheric pollutant maps for **NO₂, SO₂, and CO** at **500 m spatial resolution**, spatially continuous and gap-filled;
- ancillary explanatory variables (meteorological, morphological, and anthropogenic), provided as **multiband rasters** at their original resolution and harmonised and regridded to the same spatial scale used for pollutant data manipulation.

---

## Scripts

### `scripts/`
## Scripts

The downscaling of meteorological variables and the gap-filling and spatial downscaling of atmospheric pollutant data were performed using **Google Earth Engine (GEE) (JavaScript API)**.

The scripts implementing these processes for **SO₂, NO₂, and CO** are available in the `scripts/` directory of this repository. These scripts handle data acquisition, preprocessing, gap-filling, spatial downscaling, and export of the final products.

In addition, the repository includes a dedicated script used to identify the optimal **Sentinel-5P overpass time** over the study area. This script selects the raster acquisition with the highest number of valid (non-NoData) pixels and provides the corresponding time window to be used as input in the main processing workflow. The same script also returns the total number of valid pixels within the selected area of interest.

---

## License

This repository is released under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.  
See the `LICENSE` file for details.

---

## Citation

If you use this dataset or the associated code, please cite the related data paper:

> *[Citation will be added upon publication]*

---

## Notes

This dataset is intended to support spatial analyses of atmospheric pollutant distributions at the urban scale and applications in environmental monitoring and cultural heritage studies. Satellite-derived products should be interpreted considering their physical meaning and spatial representativeness.
