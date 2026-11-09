# Lale Califano GIS Portfolio

## About

Welcome to my GIS portfolio! I am an Environmental Geology student at Florida Gulf Coast University. This portfolio presents independent GIS projects with interests in hydrologic, terrain, and risk analysis.

## Featured Projects

### Terrain-Based Wetness Analysis Using 1 m LiDAR: FGCU Food Forest
Published: 11/5/2026

![FGCU Food Forest Location Map](site_map_forest.png)
Location map of the FGCU Food Forest. Basemap: Google.

### Tools
QGIS; SAGA/GRASS.

### Question
Within the FGCU Food Forest, do walking paths have higher relative topographic wetness than raised beds, based on TWI?

### Elevation Data
USGS 3D Elevation Program (3DEP) 1 m bare-earth DEM.

### Soil Data & Limitations
SSURGO data mapped the site as a single Hydrologic Soil Group unit at the map scale. The soil is classified as Hydrologic Soil Group A/B, meaning it behaves as group A (high infiltration and low runoff) where undisturbed and group B (moderate infiltration and runoff) where altered. 
For this phase of the project, I focused strictly on terrain-based analysis. A more extensive evaluation of infiltration potential would require integrating detailed soil data such as bulk density and hydraulic conductivity.

### Site Design & Procedure
The FGCU Food Forest was established in 2013 using permaculture design principles. I became interested in this site after observing that the food forest sits at a higher elevation than its immediate surroundings and is bounded by a subsurface  drainage system and retention basins.

![FGCU Food Forest Drainage Context](drain_example.jpg)
Image showing an example of the French drainage systems surrounding the site.

Because of this elevated setting, the food forest has a highly limited upstream topographic catchment area, meaning standard watershed delineation tools fail. To analyze this landscape, I utilized the Topographic Wetness Index (TWI). TWI is a steady-state hydrological index that quantifies how topographically flat areas with large upslope contributing zones tend to accumulate water, whereas steep areas drain.

To evaluate the TWI for the FGCU Food Forest, I downloaded a 1-meter USGS 3DEP bare-earth LiDAR Digital Elevation Model (DEM) and reprojected the raster to the EPSG:26917 UTM Zone 17N coordinate system. I created a polygon around the food forest perimeter and generated a 50-meter buffer around it to establish a comparative area with mixed land use. 

Using this clipped DEM, I generated a slope map using the SAGA Slope, Aspect, Curvature tool to calculate the terrain gradients in radians.
 
![Site Terrain Slope and Hillshade Map](slope_map.png)
Slope + hillshade map.

Next, I calculated the TWI by combining the slope derivative with a SAGA Flow Accumulation raster. I noticed the adjacent parking lot, building roof, and water body had high wetness indices due to their flat slopes. Because these surfaces are impervious and block infiltration regardless of slope, I created a spatial mask to isolate these features.

### Methodology Note (No Sink Filling):
Hydrological workflows often require "filling sinks" to ensure continuous flow accumulation. However, because the FGCU Food Forest is situated in flat Florida karst terrain with intentional microtopography (raised beds and paths), filling sinks flattened the DEM and erased the features I needed to analyze. Therefore, I bypassed the sink-filling step to preserve the microtopographic variations.

![Baseline Topographic Wetness Index Map](twi_map_1.png)
Initial Topographic Wetness Index map.

![Topographic Wetness Index Masked for Impervious Surfaces](twi_map_2.png)
Topographic Wetness Index map after masking impervious surfaces. 

### Field Validation & Infrastructure Integration

**Ground-truthing** After a storm, I conducted field validation to check whether areas with high TWI values corresponded with physical evidence of wetness. I observed that the soil had a spongier texture, stronger smell, and visibly higher saturation in many of the areas the TWI map identified as high-value areas.

**Results & Challenges**
While the TWI map successfully identified generally saturated zones, the results did not definitively separate paths from raised beds. Important scale limitations include the fact that a 1-meter pixel is too coarse to differentiate certain microtopographic features. Also, TWI is designed for large catchments so applying it to microtopography means flow accumulation can be skewed.

**Application**  
This type of limited, terrain-only analysis serves as a preliminary visual tool to understand how small site features, like footpaths or raised beds, might influence surface drainage and wetness patterns. 

### Future Projects
My next project will focus on extracting and digitizing core locations from historical marine maps of the Santa Monica Basin turbidites. Following projects will explore the automation of repetitive geospatial tasks using Python. 

## Portfolio Note

This portfolio is a collection of GIS projects demonstrating my interest in environmental geospatial analysis. I am actively building my skills and looking for internship opportunities where I can contribute to environmental work. 

### Relevant Coursework

- Introductory ArcGIS
- Hydrogeology
- Introductory Hydrology
- Soil and Water Science
- Coastal & Watershed Geology

## Contact

Email: tcalifano8127@eagle.fgcu.edu  
GitHub: https://laira-gis.github.io/portfolio/
