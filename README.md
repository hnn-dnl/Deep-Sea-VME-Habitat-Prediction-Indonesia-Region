# Indonesia Deep-Sea VME Prediction with Species Distribution Model (SDM)

Predicting the likelihood of **Vulnerable Marine Ecosystem (VME)** indicator species across Indonesian deep-sea regions (>200 m depth) using species distribution modelling and machine learning.

## Overview

VMEs are groups of species, communities or habitats that may be vulnerable to impacts from fishing activities. The vulnerability of an ecosystem is related to the vulnerability of its population, communities or habitats.

An indicator species is a species whose presence, absence, or abundance reflects specific environmental conditions or ecosystem characteristics. In marine ecology, they act as biological signs of certain habitat types.

When indicator species are observed in a location, their presence suggests that the underlying habitat conditions suitable for VMEs may exist there. However, biodiversity data is harder to find compared to environmental data, so by analysing the environmental data in places of indicator species sightings, VMEs can be predicted in locations with similar environmental data.

Six machine learning models are trained, evaluated, and combined into an ensemble prediction map to predict potential VMEs in Indonesia deep-sea region. 

**Key steps:**
- Biodiversity occurrence data sourced from [OBIS](https://obis.org/) and labelled using FAO VME taxonomy criteria via the WoRMS API
- Environmental data sourced from [Bio-ORACLE](https://www.bio-oracle.org/)
- Bathymetry data sourced from [The GEBCO Grid](https://www.gebco.net/)
- Six models compared: GLM, GAM, Decision Tree, Random Forest, XGBoost, MaxEnt
- Final ensemble prediction mapped interactively across the Indonesian region

## Output
Run the notebook to get `vme_prediction_map.html`. 

Open in any browser to view the interactive VME prediction map. Hover over any point on map to see per-model VME probability, overall probability and certainty score.

Google Drive link to download VME prediction map .html output is also available [here.](https://drive.google.com/file/d/1FnBgrdCffGcGafe8_Bkr8qysgEQV2KTV/view?usp=sharing)

## Requirements
Open in prompt and run:
```bash
conda install -c conda-forge netcdf4 dask scikit-learn
pip install pandas numpy xarray pygam xgboost elapid plotly pyobis requests
```

## Data

Most environmental data is downloaded automatically when running the notebook.

One file must be downloaded manually:
- **GEBCO bathymetry**: `gebco_2025_n7.0_s-12.0_w100.0_e145.0.nc`
  - Open The GEBCO Grid (https://download.gebco.net/)
  - Select
    -  Data: GEBCO 2025 - Global
    -  Bounding box: N 7°, S -12°, W 100°, E 145°
      -  Subset options
        -  Layers: Bathymetry
        -  Formats: NetCDF (Data)           
  - Download data in basket
  - Place it in the same directory as the notebook before running

## How to Run

1. Download the GEBCO file (see above)
2. Install dependencies (see Requirements)
3. Open `VMEPrediction.ipynb` and run all cells top to bottom

## Acknowledgements

- Biodiversity data: [OBIS](https://obis.org/)
- Environmental layers: [Bio-ORACLE](https://www.bio-oracle.org/)
- Bathymetry: [The GEBCO Grid](https://www.gebco.net/) — GEBCO Compilation Group (2025)
