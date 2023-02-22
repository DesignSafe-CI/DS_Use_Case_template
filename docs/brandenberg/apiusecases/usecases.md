# Design Safe Use Cases- Using USGS API to map earthquakes on world map 

**Brandenberg, S.J. - UCLA**<br/>

**Kota, M - UCLA**<br/>


The example makes use of the following DesignSafe resource:

[Jupyter notebooks on DS Juypterhub](https://www.designsafe-ci.org/rw/workspace/#!/Jupyter::Analysis){target=_blank}<br/>

The example also makes use of the following outside resources. 
[USGS ](https://www.usgs.gov/products/web-tools/apis){target=_blank}<br/>

## Background
### Citations and Licensing


* Please cite [Rathje et al. (2017)](https://doi.org/10.1061/(ASCE)NH.1527-6996.0000246){target=_blank} to acknowledge the use of DesignSafe resources.  

* This software is distributed under the [GNU General Public License](https://www.gnu.org/licenses/gpl-3.0.html){target=_blank}.  


### Description  
Welcome! This Jupyter notebook will walk through how to access a specific API (Application Programming interaface) that is available through USGS. This API collates all of the earthquakes over a certain magntiude that occured within a specific time period. An API is a way to expose information over a network, like the internet. The content is usually available in a convenient computer readable format rather than a human readable format. Various online databases have a usable API, that one can easily query. 

## Goal of this use case 

Goal of this notebook is to take the USGS hourly/weekly/monthly earthquake RSS feed ( https://earthquake.usgs.gov/earthquakes/feed/) and plot the earthquakes and their relevant magnitudes using a Python Package called Folium (https://python-visualization.github.io/folium/)

## Purpose of API and converting it to a usable source 

API's essentially allow for a two-way data stream, and allows end-users like us to access more usable data. Therefore, understanding how to use and query an API can be a powerful way process a significant amount of real-time data. Additionally, calling the API directly can be helpful as the URL is constantly updated and will provide the most up to date information. This example references the earthquake RSS feed for earthquake events that occured in the last month with a Magnitude over 2.5. We use 
"requests" to pull the information from the API, and then convert it into a data parseable form, JSON (JavaScript Object Notation). 

## Understanding JSON Keys

The USGS is able to store relevant data in GEOJSON format. More information can be found here (https://earthquake.usgs.gov/earthquakes/feed/v1.0/geojson.php). Now that we have the data in the JSON format, we need to identify what data we need from the output to map the data. JSON "keys" are found on the left side of the colons, such as "geometry" and "features". Values for the keys are found on the right side of the colons and give details about those keys. To build a map of the earthquakes, we will pull the coordinate information from the "geometry" key, as well as the title of the earthquake from the "properties key". However if there are  additional information from the GEOJSON that you would like to use in your analysis, you can call any variation of keys. 

## Converting JSON to a dataframe and plotting the results
Using Python's Pandas package we are able to easily convert our JSOn into a dataframe. From there we can use Folium, an envelope for Leaflet. Mapping the data can visually help you understand the extent of your data and is a powerful way to showcase everything you have queried from the API. 

Below is an example of how to create a Folium map. Additional information can be found in the Folium Documentation (https://python-visualization.github.io/folium/)

```
for index, location_info in df.iterrows():
    my_map=folium.Map(locations=[location_info["latitude"],location_info["longitude"]],zoom_start=10, control_scale=True,tiles= 'https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}',
                        attr='ESRI')
my_map
```

