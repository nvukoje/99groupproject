# Week 14 log
Group Assignment Delivery and Final Touches to Current GIS Web App.

# Begin attempting to add to watercourse line layer
Following Shawns advice, I clipped a small portion of the watercourse layer (over 2 million records) and tried to snap the point data stations that have the water quality information to it.
However a lot of the stations have little to no data included into it, so unfortunately the attempt to color code water quality on the watercourse line data will not work (need better data).

# Begin adding to the built website showcasing Web 6 solution
Begin building upon the webpage the Yingjia created and hosted on her github, will start by linking the websites code to my IDE (Git clone).

After the repository was cloned, I began updating some html for a better presentation of our web solutions (changing headers, adding details to the four pages of html).
I also updated the template and added the web map whose current solution is part of our problem statement. I uploaded that photo onto index.html.

The code included:

<!-- <div class="row">
  <div class="main">
    <h2>Ontario Water Quality Map Problem Statement</h2>
    <h3>The Ideal Solution</h3>
    <p>To provide an easy web map solution for the public to view unsafe water quality for multiple use cases within Ontario provincial streams where the web map can dynamically display the data.</p>
    <h3>The Reality</h3>
    <p>Operational layers in the web map format are hard to understand regarding water quality.</p>
    <h3>The Consequences</h3>
    <p>The web map doesn't properly display the data in the context of seeing water quality in a user friendly way. Public users can be confused with what is considered poor water quality</p>
    <h3>Our Proposal</h3>
    <p>Develop a web solution using multiple, web-based data sources to better display water quality features of Ontario streams and lakes to public users.</p>
    <h3>The Technology Explored</h3>
    <p>ArcGIS Developers, Esri Leaflet, ArcGIS Dashboard, ArcGIS Server and ArcGIS Online</p>
  </div>
</div> -->

<!-- <div class="main">
  <h2>Our Methods of Providing a Better Web Map</h2>
  <p>The following methods demonstrated on this page will show our processes and the approaches we took, along with any failings or successes we had towards our solution</p>
  <hr></hr>
  <h2>Acquiring the Data</h2>
  <p>The data was obtained from the ArcGIS REST Endpoint from the Ministry of Environment. This is based off of Land Information Ontario (LIO) where the data containing the water quality, as well as the watercourse and waterstation
    feature classes, are located. This was the primary dataset we used in conjunction with technologies we constructed to provide a solution</p> 
  <p>The map server containing the data can be found by the link <a href="https://ws.lioservices.lrc.gov.on.ca/arcgis2/rest/services/MOE/PWQMN/MapServer">here</a>. It contains three layers and is shown in the image below. The items from these layers 
  were then incorporated into our ArcGIS Online accounts, and more specifically as items within our groups (Web 6) content.</p>
</div>

<img src=ArcGISServer.jpg alt="Server" class="center">

<div class="main">
  <p>The two layers primarily used were the <a href="https://ws.lioservices.lrc.gov.on.ca/arcgis2/rest/services/MOE/PWQMN/MapServer/0">PWQMN Stations - Small</a> layer and the <a href="https://ws.lioservices.lrc.gov.on.ca/arcgis2/rest/services/MOE/PWQMN/MapServer/2">OHN Watercourse</a>
    layer. They were brought over into the ArcGIS Online group content for Web 6 as items to be used in coding web applications using the Javascript API and Esri Leaflet from ArcGIS Developers. Below are snapshots of those feature layers:
</div>

<h3 class="main">This is the watercourse feature layer that is an item in our ArcGIS Online group content.</h3>
<img src=Watercourses.jpg alt="Watercourse" class="center">

<h3 class="main">This is the station feature layer being the second item used from our AGOL account.</h3>
<img src=StationLocations.jpg alt="Stations" class="center">

<div class="main">
  <h2>Constructing a Solution through Esri Leaflet and ArcGIS Developer</h2>
  <p>Using the Javascript API key from an ArcGIS Developers account, A solution was contructed that zoomed in on the watercourses location. Javscript was coded to enable popups on stations that contained
    water quality data on Chlorides, Nitrates and Phosphates, and have these stations point at the rivers in the watercourse where the reading was taken. 
    Through research, the threshold of dangerous levels of these macronutrients was determined, levels which would contribute to algae blooms and unhealthy water quality. The Javascript that was coded also enabled
    queries on the web app, which would allow the user to click on the stations that contained dangerous readings of these macronutrients after choosing through a drop down menu. This code was enabled by the Esri Leaflet plugin.
  </p>
</div>

<h3 class="main">Below shows the API Key generated in ArcGIS Developers along with the HTML, CSS and Javascript code using the Esri Leaflet Plugin for the web solution:</h3>
<img src=APIKey.jpg alt="Key" class="center">
<img src=LeafletScript.jpg alt="Script" class="center">

<br>

<div class="main">
  <h2>Issues with the Solution</h2>
  <p>There were some attempts to improve the solution, primarily to highlight the watercourses themselves and have them be color coded based on the information from the water stations. However, there weren't enough attributes between water stations in enough locations (tied to the watercourse)
    that can enable a consistent symbology within the watercourse. More improvements can be made upon this solution such as imrpoving the topological rules of the watercourse feature layer, and have the popups from the stations contain more information for specific use cases (rather then just
    for algae bloom monitoring).
  </p>
</div> -->

I created more content on the website adding new CSS for the images that I imported into the repository. The new CSS included:

<!-- .center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 30%;
  border: black;
  border-style: solid;
  border-width: 2px;
} -->

<!-- .center1 {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 40%;
  border: black;
  border-style: solid;
  border-width: 2px;
} -->

