Project Roadmap
---------------
This page outlines the major projects and products created by Kyle O'Neil from the August 2013 through December 2016 for the Conte Ecology Research Group. A brief description of each project is listed below in the Overview. The Roadmap section provides a brief description of each project and links to the relevant scripts and data. 
<br><br>


## Overview
Basin Characteristics <br>
Climate Projections Database <br>
Culvert Delineation <br>
Daymet Data <br>
Impoundments Impact Layer <br>
NHD High Resolution Delineation - Version 2 <br>
Network Analysis (Trout GRF) <br>
Tidal Influence Layer <br>
Visualization Maps 
<br><br>



To be written up:
Fish Sites Snapping
HUC/Catchment Assignment


## Roadmap

### Basin Characteristics
All of the catchment attributes on the [Ecosheds website](http://ecosheds.org/) or used in any of the models are generated in the Basin Characteristics repository. This includes the riparian buffer statistics.

Links:
 - [GitHub Repository](https://github.com/Conte-Ecology/shedsGisData/tree/master/basinCharacteristics)
 - [Project Page](http://conte-ecology.github.io/shedsGisData/)
 - Local Directory: C:\KPONEIL\SHEDS\basinCharacteristics
 - Backup Directory: \\IGSAGBEBWS-MJO7\projects\dataIn\environmental\basinCharacteristics
<br><br>


### Climate Projections Database
Raw downscaled climate projection NetCDFs are reformatted and lodaded into the `nasa` postgres database on osensei. Climate records are linked to catchment IDs from the [NHDHRDV2](http://conte-ecology.github.io/shedsGisData/) dataset based on spatial overlap. The method may serve as guidance for similar NetCDF processing and spatial assignment, though the specific nature of NetCDF makes the usage of these scripts with other datasets unlikely.

Links: 
 - [GitHub Repository](https://github.com/Conte-Ecology/nasaProjections)
 - Local Directory: C:\KPONEIL\climate\nasaProjections
<br><br>


### Culvert Delineation
Culvert and stream gage locations in the Deerfield watershed are delineated creating polygons of the contributing drainage area to each site. Select basin attributes are calculated for each of the sites. The GIS processing utilizes the existing [NHDHRDV2](http://conte-ecology.github.io/shedsGisData/) layers and may serve as a template for future work on point delineation. This work was completed as a part of a hydrologic assessment completed by Gordon Clark (geclark330@gmail.com) through UMass Amherst and the MassDOT. 

Links:
 - [GitHub Repository](https://github.com/Conte-Ecology/culvertDelineation_MassDOT)
 - [Project Page](http://conte-ecology.github.io/culvertDelineation_MassDOT/)
 - Local Directory: C:\KPONEIL\culvertDelineation_MassDOT
<br><br>


### Daymet Data
The raw [Daymet](https://daymet.ornl.gov/) gridded observed climate data is assigned to the NHDHRDV2 catchments and uploaded to the `sheds` Postgres database. This process is completed using the custom `zonalDaymet` R package along with a series of shell scripts. The `zonalDaymet` package has functions to download and process the raw climate NetCDFs, assign climate records to catchment featureids, and save to a SQLite database. The SQLite databases are then uploaded to for upload to osensei. 

Links:
 - [Daymet Workflow Repository](https://github.com/Conte-Ecology/shedsGisData/tree/master/daymet)
 - [Project Page](http://conte-ecology.github.io/shedsGisData/)
 - [zonalDaymet Package Repository](https://github.com/Conte-Ecology/zonalDaymet)
 - Data Directory: \\IGSAGBEBWS-MJO7\projects\dataIn\environmental\climate\daymet
 - Local zonalDaymet Directory: C:\KPONEIL\GitHub\packages\zonalDaymet
<br><br>


### Hydrography Crosswalk
The NHDHRDV2 dataset is derived from source data that differs from the Watershed Boundary Dataset (WBD), which is traditionally used to define HUC boundaries. This work attempts to map the catchments to the HUC12s from the WBD more accurately than with a basic spatial overlay. 

Links:
 - [GitHub Repository](https://github.com/Conte-Ecology/hydrographyCrosswalk/tree/master/huc_to_catchments)
<br><br>


### Impoundments Impact Layer
The impoundments impact layer represents the area downstream of an impoundment that is thermally impacted by the impoundment with regards to observed stream temperature collection. The generated layer is a polyline that gets uploaded to the sheds database. The spatial range matches that of the TNC Dams layer and is used in QAQC of observed stream temperature sites for modeling purposes. A shell script is run to identify temperature sites impacted by impoundments.
  
  - [GitHub Repository](https://github.com/Conte-Ecology/shedsGisData/tree/master/impoundments)
  - [Project Page](http://conte-ecology.github.io/shedsGisData/)
  - Local Directory: C:\KPONEIL\SHEDS\impoundments
  - Backup Directory: \\IGSAGBEBWS-MJO7\projects\dataIn\environmental\connectivity\impoundments
<br><br>


### NHD High Resolution Delineation - Version 2
The NHDHRDV2 dataset includes the catchments and flowlines used on the [Ecosheds website](http://ecosheds.org/). An in depth product description with links to layer and documentation downloads is available in the SHEDS GIS Data Project Page.

Links:
 - [GitHub Repository](https://github.com/Conte-Ecology/shedsGisData/tree/master/NHDHRDV2)
 - [Project Page](http://conte-ecology.github.io/shedsGisData/)
 - Local Directory: C:\KPONEIL\HRD\V2
<br><br>


### Network Analysis (Trout GRF)
This project creates the spatial data in support of a Dan Hocking's Gaussian Random Fields in a Dendritic Network work. A project specific table is created relating sample locations and stream segments to each other in a network format.

Links:
 - [GitHub Repository](https://github.com/djhocking/Trout_GRF/tree/master/Code/createNetwork)
<br><br>


### PostGIS Tools
Two PostGIS tools exist currently. One tool queries the Daymet climate data in the sheds database based on a user-provided list of lat/lon coordinates. The other tool uses a raster-based method for performing zonal statistics on value rasters. The rasters may also be provided by the user.

Links:
 - [GitHub Repository](https://github.com/Conte-Ecology/postgisTools)
 - Local Directory: C:\KPONEIL\postgisTools
<br><br>


### Tidal Influence Layer
The tidal influence spatial polygon represents the waterbodies that are considered tidal in some capacitry. The spatial range matches that of the NHDHRDV2 and is used in QAQC of observed stream temperature sites for modeling purposes. A shell script is run to identify tidally influenced temperature sites.

Links:
 - [GitHub Repository](https://github.com/Conte-Ecology/shedsGisData/tree/master/tidalLayer)
 - [Project Page](http://conte-ecology.github.io/shedsGisData/)
 - Local Directory: C:\KPONEIL\SHEDS\tidalFilter
 - Backup Directory: \\IGSAGBEBWS-MJO7\projects\dataIn\environmental\streamStructure\tidalFilter
<br><br>
  
 
### Visualization Maps
Spatial data that support the fish movement visualization maps are generated. Raw data from the `westbrook` database on Osensei, first-hand knowledge of the sites, and existing hydrography data are combined to create the stream maps. A combination of site-specific and general processing scripts are used to produce both section center and stream boundary locations.

Links:
 - [GitHub Repository](https://github.com/Conte-Ecology/visualizationMaps)
 - Local Directory: C:\KPONEIL\visualizationMaps
<br><br>


## Contact Info 
Kyle O'Neil <br>
koneil@usgs.gov