# Mapping_Earthquakes

## Overview
Utilize GeoJSON, Leaflet, JavaScript and HTML to create an interactive multiple-layer worldmap, displaying earthquake and tectonic plates data. 

## Project Objective
To illustrate the severity of the earthquakes in relation to the tectonic plates, make API calls to the earthquake and tectonic plate data using `d3.json()`, and then add the data as an overlay to the map using the `L.geoJSON()` layer. Add three map styles. All map styles must be added to the base layer so that the selection option show up on the map to allow the user to change which layers are visible. 


## Resoureces
*Data source*
- [Earthquake data for past 7 days (GeoJSON)](https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/all_week.geojson)
- [Tectonic Plates boundary data (GeoJSON)](https://raw.githubusercontent.com/fraxen/tectonicplates/master/GeoJSON/PB2002_boundaries.json)

*Software*
- Mapbox API, Leaflet, JavaScript, GeoJSON, d3.js, CSS, HTML

## Final Project Preview
![website_preview](https://github.com/jjin92/Mapping_Earthquakes/blob/master/Earthquake_Challenge/preview.png)

## Solution
*1. JavaScript*
- Create street map layer according to Mapbox API documentation, and use map `street-v11`. Set max zoom to 18. Follow the same method, create satelliteStreets layer using map `satellite-streets-v11` and create light layer using map `light-v10`.
- Set `baseMaps` variable and include all three map layers. This will allow the user to select the map style of his/her choice.
- Create two new overlay variables for `earthquakes` and `tectonicplates`. Include these two into the variable `overlays`. User can choose whether to display the data or not. 
- Create the map object with center coordinate, zoom level and default layer as street.
- Pass our map layers into our layers control and add the layers control to the map.
`L.control.layers(baseMaps, overlays).addTo(map);`.
- Get the GeoJSON api call urls (for earthquakes and tetonic plates) and assign an variable to each.
- Create the earthquake overlay
    - Retrieve data from GeoJSON
    - For each coordinate point with earthquake record, make a circle marker
    - Style the circle marker
        - The circle radius is proportionate with the earthquake magnitude
        - The color of the circle indicates the earthquake magnitude
    - For each marker, add a popup showing magnitude and location information
    - Add this overlay to the map object
    - Create a legent to show the relationship between circle color and magnitude
- Create the tectonic plates overlay
    - Retrieve data from GeoJSON
    - Style the polyline to make it standout in both dark and light map layer
    - Add the tectonic plates overlay to the map object

*2. HTML*
- In the `<head />` section
    - Make sure in link the leaflet stylesheet
    - Add the d3.js and our own CSS style sheet
- In the `<body />` section
    - Create a `<div />` placeholder to link to the map. Assign id as `mapid` so our javascript file can refer to this placeholder
    - Add the leaflet javascript link
    - Link to our javascript file

*3. CSS*
- Style the `mapid <div />` with 100% height and width
- Style the legend with some padding and color specifications

