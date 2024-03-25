---
title: 'Sat R-day!: Spatial Statistics and Geostatistics with R'
summary: Tutorial#1 - Importing data and visualization with mapview package 
subtitle: ''
date: "2024-03-16T11:06:00Z"
# Placement options: 1 = Full column width, 2 = Out-set, 3 = Screen-width
# Focal point options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
image:
  placement: 1
  caption: 
  focal_point: ""
  preview_only: true
authors:
  - admin
tags:
  - R 
  - mapview
categories:
  - tutorials
share: false
---



## Importing data and visualization with mapview package

The interactive map below has been derived from the `Scotland Temperature.csv` file used within the scope of the gstlearn program developed by the [Geostatistics Team](https://www.geosciences.minesparis.psl.eu/en/presentation/geostatistics/) at the [Geosciences Research Center](https://www.geosciences.minesparis.psl.eu) from Mines Paris - PSL University.




<iframe seamless src="https://yunus.hacettepe.edu.tr/~gertunc/scot.html" width="100%" height="500"></iframe>

The gstlearn R package is a cross-platform tool that integrates the gstlearn C++ Library, providing R users access to a comprehensive suite of well-known geostatistical methodologies developed and/or pioneered by the Geostatistics Team.

Cite as:

```
gstlearn
Geostatistics and Machine Learning toolbox
Copyright © MINES Paris - PSL University
Free download from https://gstlearn.org
```

Useful links:

* [gstlearn](https://gstlearn.org)
* Data: https://soft.mines-paristech.fr/gstlearn/data/Scotland/Scotland Temperatures.csv

## Tutorial - SIC97 data 

The famous observed rainfall data contains 100 daily rainfall measurements made in Switzerland on the May 8, 1986 which were randomly extracted from a data set of 467 measurements. The repository of the data can be found in <https://wiki.52north.org/AI_GEOSTATS/AI_GEOSTATSData>. 


Four R packages are used for interactive map visualization: ```rnaturalearth, sp, sf, and mapview```. Summaries of these packages are provided as comments below.


```r
#Required packages
library(rnaturalearth) # working with global geographic data
library(sp)            # spatial data object tools
library(sf)            # spatial data vectoring tools
library(mapview)       # interactive map visualization
```

In order to add detail to the visualization, the boundary of Switzerland where the data set is located is imported into R using the ```ne_countries()``` function. ```read.table()``` function is utilized to import the rainfall data set.


```r
#Switzerland administrative boundary
CH = ne_countries(type = "countries", country = "Switzerland",
                  scale = "medium", returnclass = "sf")

# Reading SIC97 data
swissRain = read.table(("sic_obs.dat"), sep=',',col.names=c('ID','x','y','rain'))
```

...And some coordinate conversions.


```r
#Coordinate conversion
swissRain$x = swissRain$x - 17791.29 + 2672591
swissRain$y = swissRain$y - 13224.66 + 1200225
swissRain$rain = swissRain$rain / 10
coordinates(swissRain) <- c("x", "y")
swissRain@proj4string <- CRS("+init=epsg:2056")
swissRain <- spTransform(swissRain, CRS("+init=epsg:4326"))
swissRain <- data.frame(coordinates(swissRain),swissRain$rain)
colnames(swissRain)<-c("lon", "lat","Rainfall")
swissRain <- st_as_sf(swissRain, coords = c("lon", "lat"))

#Convert values to mm (Rainfall in original data is given in 1/10th of mm)
swissRain$Rainfall <- swissRain$Rainfall/10
```

The final step involves creating a variable (size) in data frame for proportional visualization of sample points. Then, the boundary and data points are plotted using the ```mapview()``` function.


```r
#Set bubble size
swissRain$size <- 2.5*(swissRain$Rainfall/max(swissRain$Rainfall))

output<-mapview(CH, alpha.regions = 0, 
                legend = FALSE,label = FALSE,
                color = "red", lwd = 3,
                layer.name = 'Swiss boundary') +
        mapview(swissRain, zcol = "Rainfall",
                cex = "size",
                layer.name = 'Rainfall (mm)')
```



<iframe seamless src="https://yunus.hacettepe.edu.tr/~gertunc/out.html" width="100%" height="500"></iframe>

Next Sat R-day!'s tutorial will be about exploratory data analysis.

Good luck!
