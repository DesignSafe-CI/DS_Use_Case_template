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
Welcome! This Jupyter notebook will walk through how to access a specific API (Application Programming interaface) that is available through USGS. This API collates the information to build a Shakemap for a specific earthquake event- more specifically the PGA contours. An API is a way to expose information over a network, like the internet. The content is usually available in a convenient computer readable format rather than a human readable format. Various online databases have a usable API, that one can easily query. 

## Goal of this use case 

Goal of this notebook is to take a specific earthquake event (Mw= 4.2 off Malibu in January 2023, https://earthquake.usgs.gov/earthquakes/eventpage/ci40161279/executive), and create PGA contour ShakeMap(  https://earthquake.usgs.gov/data/shakemap/). We also provide code to show how to plot the ShakeMap using a Python Package called Folium (https://python-visualization.github.io/folium/)

## Purpose of API and converting it to a usable source 

API's essentially allow for a two-way data stream, and allows end-users like us to access more usable data. Therefore, understanding how to use and query an API can be a powerful way process a significant amount of real-time data. Additionally, calling the API directly can be helpful as the URL is constantly updated and will provide the most up to date information. This example references the API that contains the details for the PGA contours for a specific earthquake event. We use 
"requests" to pull the information from the API, and then convert it into a data parseable form, JSON (JavaScript Object Notation). 

## Understanding JSON Keys

The USGS is able to store relevant data in GEOJSON format. More information can be found here (https://earthquake.usgs.gov/earthquakes/feed/v1.0/geojson.php). Now that we have the data in the JSON format, we need to identify what data we need from the output to map the data. JSON "keys" are found on the left side of the colons, such as "geometry" and "features". Values for the keys are found on the right side of the colons and give details about those keys. For our case, we are looking at Peak Ground Intensity contours, under each feature. It can understoof that each "feature" is for a different PGA interval. The interval is indicated in the "value" and is a nested key under features. Within the "features" there are also coordinates for the pga contours that we will use to recreate the shake map.

## Converting JSON to a dataframe
A url request is made to the USGS website, to download shakemap contours. Users can navigate to any specific event of their liking and use the url in the "Download data" section of the event. For this example, we will be looking at the Mw=4.2 earthquake off the coast of Malibu (https://earthquake.usgs.gov/earthquakes/eventpage/ci40161279/executive). "Get requests" is used to pull the url information, and is then saved into a variable with a JSON Format. 
## Create a ShakeMap
To create a map, we will utilize a for loop within Folium. We first initialize our map, m with a general latitude and longitude. We also use the tile "Stamen Terrain" as our base layer for our map. We loop through the json_data via the different features, and plot the differnet PGA contours. We need to flip the coordinates, to ensure the values are plotted correctly, and the "polyline" function is used to connect the contours. Lasktly a marker is added to each polyline to denote the PGA value. 

Below is an example of how to create a Folium map. Additional information can be found in the Folium Documentation (https://python-visualization.github.io/folium/)

```
from folium.features import DivIcon

m=folium.Map(locations=[40.525,-124.423],zoom_start=25,control_scale=True,tiles= 'Stamen Terrain',
                        attr='ESRI')


for feature in json_data['features']:
   
    pga = feature['properties']['value']

    for shape_data in feature['geometry']['coordinates']:
        shape = np.flip(np.array(shape_data).reshape(-1, 2), (0, 1))
        folium.PolyLine(shape,color='#E97025',weight=5, opacity=0.8).add_to(m)
        
        first_point = shape[0]
        
        folium.map.Marker(first_point,
          icon=DivIcon(
              icon_size=(30,30),
              icon_anchor=(5,14),
              html=f'<div style="font-size: 14pt">%s</div>' % str(pga),
          )
         ).add_to(m)
   

m
```


