# Next Generation Liquefaction (NGL) Database Jupyter Notebooks

**Brandenberg, S.J. - UCLA**<br/>
**Ulmer, K.J. - Southwest Research Institute**<br/>
**Zimmaro, P. - University of Calabria**  

The example makes use of the following DesignSafe resources:

<table>
  <tr>
    <th>Notebook</th>
    <th>Link</th>
  </tr>
  <tr>
    <td>
      Example Queries
    </td>
    <td>
      <a href="https://jupyter.designsafe-ci.org/hub/user-redirect/lab/tree/CommunityData/NGL/ExampleQueries.ipynb" target="_blank"><img src="https://raw.githubusercontent.com/geoelements/LearnMPM/main/DesignSafe-Badge.svg"></a>
    </td>
  </tr>
  <tr>
    <td>
      Cone Penetration Test Viewer
    </td>
    <td>
      <a href="https://jupyter.designsafe-ci.org/hub/user-redirect/lab/tree/CommunityData/NGL/CPT_viewer.ipynb" target="_blank"><img src="https://raw.githubusercontent.com/geoelements/LearnMPM/main/DesignSafe-Badge.svg"></a>
    </td>
  </tr>
  <tr>
    <td>
      V<sub>S</sub> (Invasive) Test Viewer
    </td>
    <td>
      <a href="https://jupyter.designsafe-ci.org/hub/user-redirect/lab/tree/CommunityData/NGL/VS_Invasive_viewer.ipynb" target="_blank"><img src="https://raw.githubusercontent.com/geoelements/LearnMPM/main/DesignSafe-Badge.svg"></a>
    </td>
  </tr>
  <tr>
    <td>
      October 2021 DesignSafe Webinar
    </td>
    <td>
      <a href="https://jupyter.designsafe-ci.org/hub/user-redirect/lab/tree/CommunityData/NGL/DesignSafe_Webinar_Oct2021.ipynb" target="_blank"><img src="https://raw.githubusercontent.com/geoelements/LearnMPM/main/DesignSafe-Badge.svg"></a>
    </td>
  </tr>
  <tr>
    <td>
      Direct Simple Shear Viewer
    </td>
    <td>
      <a href="https://jupyter.designsafe-ci.org/hub/user-redirect/lab/tree/CommunityData/NGL/DSS_Viewer.ipynb" target="_blank"><img src="https://raw.githubusercontent.com/geoelements/LearnMPM/main/DesignSafe-Badge.svg"></a>
    </td>
  </tr>
</table>

The NGL database can be accessed at <a href="https://www.nextgenerationliquefaction.org/" target="_blank">https://www.nextgenerationliquefaction.org/</a>

## Background
### Citations and Licensing

* Please cite [Zimmaro, P., et al. (2019)](https://doi.org/10.21222/C2J040) to acknowledge the use of the NGL Database. Data in the NGL database has been gathered from [these](https://nextgenerationliquefaction.org/citations.php) published sources. If you use specific data in the database, please cite the original source.

* Please cite [Rathje et al. (2017)](https://doi.org/10.1061/(ASCE)NH.1527-6996.0000246) to acknowledge the use of DesignSafe resources.  

* This software is distributed under the [GNU General Public License](https://www.gnu.org/licenses/gpl-3.0.html).  


### Description  
The Next Generation Liquefaction (NGL) Project is advancing the state of the art in liquefaction research 
and working toward providing end users with a consensus approach to assess liquefaction potential within 
a probabilistic and risk-informed framework. Specifically, NGL’s goal is to first collect and organize 
liquefaction information in a common and comprehensive database to provide all researchers with a 
substantially larger, more consistent, and more reliable source of liquefaction data than existed previously. 
Based on this database, we will create probabilistic models that provide hazard- and risk-consistent bases 
for assessing liquefaction susceptibility, the potential for liquefaction to be triggered in susceptible soils, 
and the likely consequences. NGL is committed to an open and objective evaluation and integration of data, 
models and methods, as recommended in a 2016 National Academies [report](https://www.nap.edu/catalog/23474/state-of-the-art-and-practice-in-the-assessment-of-earthquake-induced-soil-liquefaction-and-its-consequences). 

The evaluation and integration of the data into new models and methods will be clear and transparent. Following these principles will ensure 
that the resulting liquefaction susceptibility, triggering, and consequence models are reliable, robust and 
vetted by the scientific community, providing a solid foundation for designing, constructing and overseeing 
critical infrastructure projects.

The NGL database is populated through a web interface at www.nextgenerationliquefaction.org/. The web interface 
provides limited capabilities for users to interact with data. Users are able to view and download data, 
but they cannot use the GUI to develop an end-to-end workflow to make scientific inferences and draw conclusions 
from the data. To facilitate end-to-end workflows, the NGL database is replicated daily to [DesignSafe](https://www.designsafe-ci.org), where 
users can interact with it using Jupyter notebooks.

## Understanding the Database Schema

The NGL database is organized into tables that are related to each other via keys. To query the database, 
you will need to understand the organizational structure of the database, called the schema. The database 
schema is documented at the following URL:

[https://nextgenerationliquefaction.org/schema/index.html](https://nextgenerationliquefaction.org/schema/index.html)
  
## Querying Data via Jupyter Notebooks

Jupyter notebooks provide the capability to query NGL data, and subsequently process, visualize, and learn from the data in an end-to-end workflow. Jupyter notebooks run in the cloud on DesignSafe, and provide a number of benefits compared with a more traditional local mode of operation:

1. The NGL database contains many GB of data, and interating with it in the cloud does not require downloading these data files to a local file system.
2. Users can collaborate in the cloud by creating DesignSafe projects where they can share processing scripts.
3. The NGL database is constantly changing as new data is added. Working in the cloud means that the data will always be up-to-date.
4. Querying the MySQL database is faster than opening individual text files to extract data.

This documentation first demonstrates how to install the database connection script, followed by several example scripts intended to serve as starting points for users who wish to develop their own tools.

## Installing Database Connection Script
 
Connecting to a relational database requires credentials, like username, password, database name, and hostname. 
Rather than requiring users to know these credentials and create their own database connections, we have created a Python package that allows users to
query the database. This code installs the package containing the database connection script for NGL:

```python
!pip install git+https://github.com/sjbrandenberg/designsafe_db
```

## Example Queries

This notebook contains example queries to illustrate how to extract data from the NGL database into Pandas dataframe objects using Python scripts in Jupyter notebooks. The notebook contains cells that perform the following operations:

1. Query contents of the SITE table
2. Query event information and associated field observations at the Wildlife liquefaction array
3. Query cone penetration test data at Wildlife liquefaction array
4. Query a list of tables in the NGL database
5. Query information about BORH table
6. Query counts of cone penetration test data, boreholes, surface wave measurements, invasive shear wave velocity measurements, liquefaction observations, and non-liquefaction observations

<a href="https://jupyter.designsafe-ci.org/hub/user-redirect/lab/tree/CommunityData/NGL/ExampleQueries.ipynb" target="_blank"><img src="https://raw.githubusercontent.com/geoelements/LearnMPM/main/DesignSafe-Badge.svg"></a>

## Cone Penetration Test Viewer

The cone penetration test viewer demonstrates the following:

1. Connecting to NGL database in DesignSafe
2. Querying data from SITE, TEST, SCPG, and SCPT tables into Pandas dataframes
3. Creating dropdown widgets using the ipywidgets package to allow users to select site and test data
4. Creating HTML widget for displaying metadata after a user select a test
5. Using the ipywidgets "observe" feature to call functions when users select a widget value
6. Plotting data from the selected cone penetration test using matplotlib

Cone penetration test data plotted in the notebook include tip resistance, sleeve friction, and pore pressure. In some cases, sleeve friction and pore pressure are not measured, in which case the plots are empty.

<a href="https://jupyter.designsafe-ci.org/hub/user-redirect/lab/tree/CommunityData/NGL/CPT_viewer.ipynb" target="_blank"><img src="https://raw.githubusercontent.com/geoelements/LearnMPM/main/DesignSafe-Badge.svg"></a>


## V<sub>S</sub> (Invasive) Test Viewer

The V<sub>s</sub> (Invasive) Test Viewer demonstrates the following:

1. Connecting to NGL database in DesignSafe
2. Querying data from SITE, TEST, GINV, and GIND tables into Pandas dataframes
3. Creating dropdown widgets using the ipywidgets package to allow users to select site and test data
4. Creating HTML widget for displaying metadata after a user selects a test
5. Using the ipywidgets "observe" feature to call functions when users select a widget value
6. Plotting data from the selected invasive geophysical test using matplotlib

<a href="https://jupyter.designsafe-ci.org/hub/user-redirect/lab/tree/CommunityData/NGL/VS_Invasive_viewer.ipynb" target="_blank"><img src="https://raw.githubusercontent.com/geoelements/LearnMPM/main/DesignSafe-Badge.svg"></a>


## October 2021 DesignSafe Webinar

The DesignSafe_Webinar_Oct2021 notebook was created during a webinar/workshop hosted by DesignSafe and the Pacific Earthquake Engineering Research (PEER) center.

The notebook demonstrates the following:

1. Connecting to NGL database in DesignSafe
2. Querying data from SITE, TEST, SCPG, and SCPT tables into Pandas dataframes
3. Plotting data from the selected test using matplotlib

Cone penetration test data plotted in the notebook include tip resistance, sleeve friction, and pore pressure. In some cases, sleeve friction and pore pressure are not measured, in which case the plots are empty.

<a href="https://jupyter.designsafe-ci.org/hub/user-redirect/lab/tree/CommunityData/NGL/DesignSafe_Webinar_Oct2021.ipynb" target="_blank"><img src="https://raw.githubusercontent.com/geoelements/LearnMPM/main/DesignSafe-Badge.svg"></a>

[DesignSafe Webinar YouTube video](https://youtu.be/TNOPOU4lx5w)

[DesignSafe Workshop YouTube video](https://youtu.be/_nKpSqa1rso)

## Direct Simple Shear Laboratory Test Viewer

The Direct Simple Shear Laboratory Test Viewer is a graphical interface that plots direct simple shear tests in the NGL database. It demonstrates the following:

1. Connecting to NGL database in DesignSafe
2. Querying data from LAB, LAB_PROGRAM, SAMP, SPEC, DSSG, and DSSS tables into Pandas dataframes
3. Creating dropdown widgets using the ipywidgets package to allow users to select lab, sample, specimen, and test data
4. Creating javascript for downloading the selected direct simple shear test to a local computer
5. Plotting data from the selected direct simple shear test using matplotlib

Direct simple shear data plotted in the notebook include shear stress, shear strain, vertical stress, and vertical strain time series in the first plot. The second plot displays shear strain and void ratio versus vertical stress and void ratio, shear stress, and vertical stress ratio versus shear strain.

<a href="https://jupyter.designsafe-ci.org/hub/user-redirect/lab/tree/CommunityData/NGL/DSS_Viewer.ipynb" target="_blank"><img src="https://raw.githubusercontent.com/geoelements/LearnMPM/main/DesignSafe-Badge.svg"></a>
