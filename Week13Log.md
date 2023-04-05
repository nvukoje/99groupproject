# Week 13 Log

 Using Leaflet after Week 12 when I incorporated two feature items from the map server from LIO Ontario.

One item contained the waterstations that included the data of three macronutrients for plant growth, an indicator of algae blooms and overall health of the stream.
This was obtained from the map server url: "https://ws.lioservices.lrc.gov.on.ca/arcgis2/rest/services/MOE/PWQMN/MapServer/0".
The second item contained the watercourses from the same server with a different url: "https://ws.lioservices.lrc.gov.on.ca/arcgis2/rest/services/MOE/PWQMN/MapServer/2".

Using the html page I made on github, I incorporated these feature layers into the vector basemap using Leaflet:

const waterstations = L.esri.featureLayer({
        url: "https://ws.lioservices.lrc.gov.on.ca/arcgis2/rest/services/MOE/PWQMN/MapServer/0"
      }).addTo(map); 

const watercourse = L.esri.featureLayer({
        url: "https://ws.lioservices.lrc.gov.on.ca/arcgis2/rest/services/MOE/PWQMN/MapServer/2"
      }).addTo(map);

This includes the javascript libraries that enable these items to be displayed, along with my API key from ArcGIS Developers and displaying a vector base map.
The intracacies of incorporating the vector base map variable along with using the API Key can be found in this url: https://developers.arcgis.com/esri-leaflet/maps/display-a-map/

# For this week, I will attempt to conslidate the data from these servers so that the watercourses are shown, but once clicked on, they display the data for health.

Following last weeks discussion with Shawn, I updated the base map variable to zoom in on an area. This was done in the following:

const map = L.map("map", {
        minZoom: 2
      }).setView([25, -30], 2);

This changed to:

const map = L.map("map", {
        minZoom: 2
      }).setView([43.8180, -79.5915], 15);