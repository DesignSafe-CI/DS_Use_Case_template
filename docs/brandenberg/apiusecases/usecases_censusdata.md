# Design Safe Use Cases- US Census API Jupyter Integration

**Brandenberg, S.J. - UCLA**<br/>

**Kota, M - UCLA**<br/>


The example makes use of the following DesignSafe resource:

[Jupyter notebooks on DS Juypterhub](https://www.designsafe-ci.org/rw/workspace/#!/Jupyter::Analysis){:target="_blank"}<br/>

The example also makes use of the following outside resources. 
[USGS ](https://www.usgs.gov/products/web-tools/apis){:target="_blank"}<br/>

## Background
### Citations and Licensing


* Please cite [Rathje et al. (2017)](https://doi.org/10.1061/(ASCE)NH.1527-6996.0000246){target=_blank} to acknowledge the use of DesignSafe resources.  

* This software is distributed under the [GNU General Public License](https://www.gnu.org/licenses/gpl-3.0.html){target=_blank}.  


### Description  
Welcome! This Jupyter notebook will walk through how to access an Application Programming Interface (API) that is available through the US Census Bureau. This API collates census data, including but not limited to total state populations, and population in poverty for example. 

### What is an API?
An API is a program that enables communication between two software components. In this case, the US Census Bureau maintains a database on their servers, and they make data available to users through requests in the format of Uniform Resource Locators (URLs). The content can be returned in various formats like html, xml, and json. Various online databases have API's that enable users to query data. 

## Authentication, Authorization, and API Keys
Authentication verifies the identity of a user, generally by entering a username and password, and sometimes through additional measures like multi-factor authentication. Authorization determines the access rights extended to a user. API's are often stateless, meaning that the server does not store any information about the client session on the server-side. Authorization of an API request is therefore handled using keys or tokens that are passed from the client to the server as part of the API request. Generally an API key or token is only provided to authenticated users.

The US Census Bureau API requires users to have an API Key. To use this use case, you will first need to create your own unique US Census API Key, and will be prompted below to input it. More information can be found here: https://api.census.gov/data/key_signup.html
 
## Purpose of API and converting it to a usable source 

API's essentially allow for a two-way data stream, and allows end-users like us to access more usable data. Therefore, understanding how to use and query an API can be a powerful way process a significant amount of real-time data. Additionally, calling the API directly can be helpful as the URL is constantly updated and will provide the most up to date information. This example references the API that contains the details for the PGA contours for a specific earthquake event. We use 
"requests" to pull the information from the API, and then convert it into a data parseable form, JSON (JavaScript Object Notation). 

## Using the Census API

 We will now to set up our URL request from the US Census API. More general information can be found here: https://www.census.gov/data/developers/guidance/api-user-guide.html. Generally we are extracting data from the American Community Survey (https://www.census.gov/programs-surveys/acs), which is a survey conducted by the US Census which details housing and population counts for the nation.There are three key inputs before we make our request and that includes setting a variable, the year we would like our data to be from, and then our individual census API Key. 

 For the variables, it dictates the exact information we would like to extract from our query. The variable can be changed to pull different population groups, that differ on age, sex, and race. A table of the available variables are found here: https://api.census.gov/data/2019/acs/acs1/variables.html. For this intial example, we are looking at total population which is the variable 'B01001_001E'. Additionally we are looking at data from 20202. This information along with our Census API key will allow us to extract relevant data. Once you have determiend your Census Key, you should input it when prompted below. Do not share your key with any other individuals. 

## Temporary storage 
Once we're able to download the data, we can plot it in a way that is easy to translate. To do this, we can download the shape files for the various states as presecribed by the Census. To do this we temporarily download the shape files to the users device, and read it for our use. The file and its corresponding directory will thereafter be deleted. Sample code snippet is shown below. 
```` from tempfile import TemporaryDirectory

import geopandas as gpd

with TemporaryDirectory() as temp_dir:
    with open(f"{temp_dir}/states.zip", "wb") as zip_file:
        zip_file.write(shape_zip)
    
    with open(f"{temp_dir}/states.zip", "rb") as zip_file:
        states_gdf = gpd.read_file(zip_file)
````

## Create a Map of the Census data 
Once we have the relevant data downloaded (information from the census, and relevant shape files), we can create a map to represent our data. 

Below is an example of how to create a Folium map. Additional information can be found in the Folium Documentation (https://python-visualization.github.io/folium/). In this example we utilize the chrorpleth function in folium, that allows one to create a heat map. 

```
my_map = folium.Map(locations=[35.74785,-86.69235], zoom_start=5, tiles= 'Stamen Terrain',control_scale=True)

cp = folium.Choropleth(
    geo_data=states_json,
    name="choropleth",
    data=df_join,
    columns=["state", "total_population"],
    key_on="feature.properties.GEOID",
    fill_color="YlGn",
    fill_opacity=0.7,
    line_opacity=0.2,
    legend_name=f"Total Population By State, {year}",
).add_to(my_map)

for index, location_info in df_join.iterrows():
    folium.Marker([location_info["Latitude"], location_info["Longitude"]],popup=location_info["NAME"], color ='purple').add_to(my_map)
    folium.Marker([location_info["Latitude"], location_info["Longitude"]],popup=location_info["total_population"], color ='purple').add_to(my_map)

my_map
```


