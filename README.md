
# WSIGN406 Violation Analyzer

A geospatial analysis tool to detect and resolve **false positive WSIGN406 violations** by evaluating motorway sign data in relation to pedestrian-assigned roads. Developed for the HERE Chicago Hackathon by Team **ChicagoFast**.

## Problem

**WSIGN406** is triggered when motorway signs are detected within 20 meters of roads flagged as `Pedestrian = TRUE`. However, these can be false positives caused by:

- Topological misassignments
- Misaligned sign data
- Outdated or missing road access specifiers

## Solution Overview

The system uses multi-layered validation with geospatial and semantic filtering. Four key scenarios are considered:

### Scenario 1: Sign May Not Exist Anymore  
Uses the **existence score** from sign metadata.  
- If score < 0.7 → likely outdated → filter out.

### Scenario 2: Incorrect Road Matching  
- Segments topological data by motorway/pedestrian flags.  
- Calculates perpendicular distance to roads in tile bounds.  
- Reassigns signs to nearest valid motorway segment.

### Scenario 3: Incorrect Access Specifier  
- Performs **average speed analysis**.  
- If speed is too high for pedestrians → set `Pedestrian = FALSE`.

### Scenario 4: Genuine Exception  
- Flags legitimate violations for exclusion from future WSIGN406 checks.

---

## Features

- Geospatial filtering using GeoPandas and Shapely  
- Confidence score parsing from sign data  
- Distance calculation between signs and roads  
- Optional clustering and segmentation logic  
- Modular structure for testing and debugging

---

## ▶️ How to Run

1. Unzip the data files:
   ```bash
   unzip data.zip
   ```
   
2. Download all files (all the .geojason and .csv files) and keep it in the working directory:


3. Install required packages:
   ```bash
   pip install pandas geopandas shapely matplotlib seaborn scikit-learn
   ```

4. Open and run `final.ipynb` in a Jupyter environment.

---

## Team

- Shobhit Sinha
- Keisha Kaba
- Rishit Chatterjee 

