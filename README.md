# Blueberry_Sampling

## Introduction
This archive contains information, including both simple R code and descriptions
of related GIS processing steps  for generating a simple GRTS sampling frame to
study pesticide contamination in groundwater near wild blueberry growing areas
in Maine.

This analysis was produced to assist the Maine Board of Pesticides Control with
ground water pesticide surveillance efforts.  The Board has collected data on
prevalence of pesticides in groundwater near blueberry fields periodically for
many years. This analysis was prepared for proposed 2021 sampling.

Blueberry fields represent a small fraction of the state of Maine, and so 
selecting locations for sampling near blueberry fields is problematic using
simple random sampling schemes.  Most random points drawn would be nowhere near
blueberry growing areas.

The solution is to select sampling locations from locations near blueberry
fields only. GRTS ('Generalized Random Tessellation Stratified') sampling
provides a way to generate spatially balanced samples from complex geographic
areas like this.

To add complexity to the sampling problem, groundwater samples are collected by
sampling domestic wells. Thus we not only need to find locations near blueberry
fields, but also locations near houses near blueberry fields. Even if we sample
near blueberry fields, a high proportion of locations will not be near houses,
and thus will not be able to be sampled.  Thus we need a substantial
"oversample" of candidate points that we can review sequentially to generate a
spatially balanced random sample.

## Process Overview
We generated a GIS map of areas within approximately 1/4 mile of blueberry
fields using GIS.  Original data showing blueberry growing areas was derived 
from the USDA Cropland Data layer

>  USDA National Agricultural Statistics Service Cropland Data Layer. 2019.
   Published crop-specific data layer [Online]. Available at
   https://nassgeodata.gmu.edu/CropScape/ (accessed July 27, 2020). USDA-NASS,
   Washington, DC.
   
We used standard GIS processing to develop an approximate map of areas within
about a quarter mile of those locations.  General details of processing steps 
are provided in a Word document.

We then generated a spatially balanced random sample using the "GRTS" algorithm
and the spsurvey package in R.

>  Kincaid TM, Olsen AR, Weber MH (2020). spsurvey: Spatial Survey Design and
   Analysis. R package version 4.1.4. 

Code for that step is provided in an R markdown document and an output Word
document.

We then use GRTS to draw a random sample within of spatially balanced points
from within that area.

We return to GIS to reproject the spatial random sample to WGS 1984, and produce
a text file containing a list of sampling locations with both UTM and WGS 1984
coordinates.

To save space in the archive, we omit most GIS  files. Any of the geospatial
data is available upon request. The only geospatial data not readily available
from public sources is the data on Maine BPC "Inspector Regions", which plays a
relatively minor role in this analysis.



