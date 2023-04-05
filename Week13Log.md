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
      }).setView([43.7981, -79.5912], 14);

Added the pop-up display for the phosphorus, nitrates and chloride found at the stations for each river using hte following code:

waterstations.bindPopup(function (layer) {

        return L.Util.template("<b>{CHLORIDE}</b><br>{NITRATES}</br><b>{PHOSPHORUS}</b>", layer.feature.properties);

      });

This succesfully created the popups, but I now see that information of water quality is missing in the part of the map I zoomed into.

Decided to input a query with the popups into the display to show macronutrient levels that are hazardous, which are:

Nitrates are dangerous when > 10 mg/L
Phosphates are dangerous when > 10 mg/L
Chlorides are dangerous when > 250 mg/L 

Used the template from https://developers.arcgis.com/esri-leaflet/query-and-edit/query-a-feature-layer-sql/#whats-next and substituted the feature layer along with tweaking some variable names and popup displays:

L.Control.QueryControl = L.Control.extend({
        onAdd: function (map) {
          const whereClauses = [
            "Choose a WHERE clause...",
            "CHLORIDE > 250",
            "NITRATES > 10",
            "PHOSPHORUS > 10"
          ];

          const select = L.DomUtil.create("select", "");
          select.setAttribute("id", "whereClauseSelect");
          select.setAttribute("style", "font-size: 16px;padding:4px 8px;");
          whereClauses.forEach(function (whereClause) {
            let option = L.DomUtil.create("option");
            option.innerHTML = whereClause;
            select.appendChild(option);
          });
          return select;

        },

        onRemove: function (map) {
          // Nothing to do here
        }
      });

      L.control.queryControl = function (opts) {
        return new L.Control.QueryControl(opts);
      };

      L.control
        .queryControl({
          position: "topright"
        })
        .addTo(map);

      const waterstations = L.esri
        .featureLayer({
          url: "https://ws.lioservices.lrc.gov.on.ca/arcgis2/rest/services/MOE/PWQMN/MapServer/0",
          simplifyFactor: 0.5,
          precision: 4,

          where: "1 = 0"

        })
        .addTo(map);

      const select = document.getElementById("whereClauseSelect");
      select.addEventListener("change", () => {
        if (select.value !== "") {
          waterstations.setWhere(select.value);
        }
      });

      waterstations.bindPopup(function (layer) {
          return L.Util.template("<b>Chloride Danger Threshsold > 250 mg/L</b> Current Level: {CHLORIDE} mg/L<br><b>Nitrate Danger Threshold > 10 mg/L</b> Current Level: {NITRATES} mg/L</br><b>Phosphate Danger Threshold > 10 mg/L</b> Current Level: {PHOSPHORUS} mg/L", layer.feature.properties);
      })

