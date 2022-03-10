# Next Generation Liuqefaction (NGL) Database Jupyter Notebooks

**Brandenberg, S.J., UCLA, Ulmer, K.J., Southwest Research Institute, and Zimmaro, P., University of Calabria**  

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

The NGL database is populated through a web GUI at www.nextgenerationliquefaction.org/. The web interface 
provides limited capabilities for users to interact with data. Users are able to view and download data, 
but they cannot use the GUI to develop an end-to-end workflow to make scientific inferences and draw conclusions 
from the data. To facilitate end-to-end workflows, the NGL database is replicated daily to [DesignSafe](https://www.designsafe-ci.org), where 
users can interact with it using Jupyter notebooks.

## Citation and Licensing

* Please cite [Zimmaro, P., et al. (2019)](https://doi.org/10.21222/C2J040) to acknowledge the use of the NGL Database. Data in the NGL database has been gathered from [these](https://nextgenerationliquefaction.org/citations.php) published sources. If you use specific data in the database, please cite the original source.

* Please cite [Rathje et al. (2017)](https://doi.org/10.1061/(ASCE)NH.1527-6996.0000246) to acknowledge the use of DesignSafe resources.  

* This software is distributed under the GNU General Public License (https://www.gnu.org/licenses/gpl-3.0.html).  


## Installing Database Connection Script
 
Connecting to a relational database requires credentials, like username, password, database name, and hostname. 
Rather than requiring users to know these credentials, we have created a Python package that allows users to 
connect to the database. This code installs the package containing the database connection script for NGL:

```python
!pip install designsafe_db
```

## Querying the Database

This section illustrates how to query the NGL database, and the example queries are contained in a [Jupyter Notebook on DesignSafe](https://jupyter.designsafe-ci.org/user/name/tree/CommunityData/NGL/ExampleQueries.ipynb).

### Query contents of SITE table

The lines of code below first imports the ngl_db Python package, then creates a query to read all data from the SITE table, then creates a Pandas dataframe by executing the read_sql command that is part of the designsafe_db.ngl_db package.

```python
import designsafe_db.ngl_db as ngl
sql = "SELECT * FROM SITE"
df = ngl.read_sql(sql)
```

The output from the command is illustrated in the figure below. When this query was written, there were a total of 333 sites in 
the NGL database. The SITE_ID field is not contiguous because sites are sometimes deleted from the database, and the 
SITE_ID field is never re-used. The Pandas dataframe is broken between SITE_ID 151 and 677 for ease of displaying 
information in the output window. Many rows of data are not displayed in Figure 1 as a result.

![Screenshot of result of query of SITE table data.](img/SiteTableQuery.png)

**Figure 1.** Results of query of SITE table data.

### Query Wildlife liquefaction array data

This cell queries event information from the EVNT table and surface evidence of liquefaction information from the FLDM table at the Wildlife Array site. The definition of each table and site is below. The query utilizes an INNER JOIN statement to combine tables based on shared keys, and will return all values that have matching keys in both tables. For more details, see <https://www.w3schools.com/sql/sql_join_inner.asp>

**Table 1.** List of tables utilized in Wildlife liquefaction array queries.

| Table	| Description |
| ----- | ----------- |
| EVNT	| 	Earthquake event information |
| FLDM	| 	Field evidence of liquefaction information at a point within a site |
| FLDO	| 	Field evidence of liquefaction information at a site |
| SITE	| 	A site is the highest level organizational structure for information in the database |

**Table 2.** List of fields utilized in Wildlife liquefaction array queries.

| Field	| Description |
| ----- | ----------- |
| EVNT_MAG | 	Earthquake magnitude |
| EVNT_NM | 	  Event name |
| EVNT_YR | 	  Event year |
| FLDM_LAT | 	Latitude of manifestation observation |
| FLDM_LON | 	Longitude of manifestation observation |
| FLDM_SFEV | 	Indication of whether surface manifestation occurred (0 = no, 1 = yes) |
| FLDM_DESC | 	Description of liquefaction manifestation |
| FLDO_ID |    Primary key in FLDO table, and foreign key in FLDM table |
| EVNT_ID |    Primary key in EVNT table, and foreign key in FLDO table |
| SITE_ID |    Primary key in SITE table, and foreign key in FLDO table |
| SITE_NAME |  Site name |

```python
import designsafe_db.ngl_db as ngl

sql = 'SELECT EVNT.EVNT_MAG, EVNT.EVNT_NM, EVNT.EVNT_YR, FLDM.FLDM_LAT, FLDM.FLDM_LON, FLDM.FLDM_SFEV, FLDM.FLDM_DESC '
sql += 'FROM FLDO INNER JOIN FLDM on FLDO.FLDO_ID = FLDM.FLDO_ID '
sql += 'INNER JOIN EVNT ON EVNT.EVNT_ID = FLDO.EVNT_ID '
sql += 'INNER JOIN SITE ON FLDO.SITE_ID = SITE.SITE_ID '
sql += 'WHERE SITE_NAME = "Wildlife Array"'

df = ngl.read_sql_query(sql)
pd.set_option('display.max_colwidth', 100)
df
```

![Screenshot of result of query of Wildlife liquefaction array query of event information and field observations.](img/WildlifeQuery1.png)
  

**Figure 2.** Screenshot of result of query of Wildlife liquefaction array query of event information and field observations.

### Header2 Subheading

In aliquam sem fringilla ut morbi. Interdum varius sit amet mattis vulputate enim nulla aliquet. Sit amet mattis vulputate enim nulla.  In egestas erat imperdiet sed euismod nisi porta lorem. Eget nulla facilisi etiam dignissim diam.  Facilisi cras fermentum odio eu feugiat. Velit aliquet sagittis id consectetur. Vel quam elementum pulvinar etiam.  Ut diam quam nulla porttitor massa id neque aliquam. Sodales ut etiam sit amet nisl.  Scelerisque varius morbi enim nunc faucibus a. Sit amet volutpat consequat mauris nunc. Et leo duis ut diam.

*Add images to the folder img and use relative path to specify the location of the image.*   

![caption](img/mkdocs-template.png)
> Use case template design


## Header3

Morbi tristique senectus et netus et. Tristique senectus et netus et malesuada fames.  Eu mi bibendum neque egestas congue quisque. Id consectetur purus ut faucibus pulvinar elementum integer enim. Nunc consequat interdum varius sit amet mattis vulputate enim nulla.  Porta nibh venenatis cras sed felis eget. Dui id ornare arcu odio ut sem nulla pharetra diam. Pellentesque habitant morbi tristique senectus et netus et. Commodo nulla facilisi nullam vehicula ipsum a arcu. Nisi porta lorem mollis aliquam ut porttitor leo.

Numbered list 

1. [numbered linked item](https://maps.google.com)
2. second item
3. third item

### Header3 subheading

Ac feugiat sed lectus vestibulum mattis ullamcorper. Et egestas quis ipsum suspendisse ultrices gravida dictum fusce ut. Scelerisque eu ultrices vitae auctor eu augue ut lectus arcu.  Imperdiet proin fermentum leo vel orci porta non pulvinar. Dictumst quisque sagittis purus sit amet. Aliquam purus sit amet luctus. Aliquet bibendum enim facilisis gravida neque convallis a cras. Orci porta non pulvinar neque laoreet suspendisse. Urna neque viverra justo nec ultrices dui.

**Example Table**

| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Stampede2| CPU      | 2017     |     
| Frontera | CPU & GPU| 2019     |     

Or use markdown table generator: [https://www.tablesgenerator.com/markdown_tables](https://www.tablesgenerator.com/markdown_tables)


### Math

To generate math equations in markdown.

For inline mode formulas: $`a^2+b^2=c^2`$.

For display mode formulas which appear on a separate line
```math
f(x) = \int_{-\infty}^\infty
\hat f(\xi)\,e^{2 \pi i \xi x}
\,d\xi
```

### Code

``` python
import tensorflow as tf
```

Highlight specific lines of the code

``` python hl_lines="3 4"
""" Bubble sort """
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```
