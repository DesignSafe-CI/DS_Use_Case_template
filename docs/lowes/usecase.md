# Modeling Reinforced Concrete Walls with Continuum Elements to Simulate Through Opensees and Using Jupyter to Post Process Results

**Josh Stokley and Laura Lowes, University of Washington**  

This use case example demonstrates how to use Jupyter notebook on design safe to model out reinforced concrete walls and run them through OpenSeesMP on DesignSafe. 
Post processing scripts are also avaliable and able to run through designsafe, allowing for a steady flow and less steps for the user.  The purpose of this use case is to be able to model, simulate, and post process multiple walls at once.  This documentation will provide an example of one wall so the user may understand the steps in the workflow.  This use case makes use of the following DesignSafe resources:

(jupyter notebook link)  
(opensees link)  

<!--- this is a comment --->  
<!--- this is a comment --->  
<!--- this is a comment --->  
<!--- this is a comment --->  
<!--- this is a comment --->  



## Background 

### Citation and Licensing

* Please cite Alex Shegay ... (link) to acknowledge the use of any data from this use case.

* Please cite ....Mitc4 docu.... to acknowledge the use of the modeling strategy from this use case.

* Please cite [AUTHORS et al. (20xx) - example of published project](https://doi.org/10.17603/ds2-3zdj-493) to acknowledge the use of any resources from this use case.

* Please cite [Rathje et al. (2017)](https://doi.org/10.1061/(ASCE)NH.1527-6996.0000246) to acknowledge the use of DesignSafe resources.  

* This software is distributed under the GNU General Public License (https://www.gnu.org/licenses/gpl-3.0.html).  

### Description 

RW1 is modeled  from the database to produce a tcl file that represents the geometry, material, and simulation history of the wall. The wall is y high, x long, and z thick. It consists of x amount of nodes, y amount of continuum shell elements, and z amount of steel truss elements. MITC4 shell elements are used to smear the concrete and transverse steel into the thickness while the vertical reinforce bars are modeled as truss elements. RW1 had a compression buckling failure mode in the lab. The variables that carry uncertainty will be the shear retention factor and the ratio of unconfined crushing energy to confined crushing energy. More information on RW1 and its expirmental results can be found in (RW1 LINK)

![SchematicView](img/ShellEle.JPG)  
Smeared shell element representation  

(Model picture of RW1 goes here)  

The use case workflow involves the following steps:

* Using Jupyter notebook modeling script to create input file for OpenSees
* Running input file through HPC on TACC
* Using Jupyter notebook post processing scripts to evaulate model


## Create Input File using Modeling Script

The jupyter notebook that creates the OpenSees input file can be found here: (LINK TO FILE).

### Reinforced Concrete Wall Database

The walls that are modeled are defined in a database provided by Alex Shegay.  His work can be found here: (ALEX MATLAB LINK)  

The database is a MATLAB variable of type 'structure'. The tree-like structure of the variable consists of several levels. Each level consists of several varaiables, each being a 1x142 dimension array. Each entry within the array corresponds to a separate wall specimen. The order of these entries is consistent throughout the database and reflects the order of walls as appearing in the 'UniqueID' array.



### Modeling Script 

The modeling script imports the variables from the database necassary to build a continuum model for a wall. The first section of the script initializes the model. The degrees of fredom are defined and the variables that carry uncertainty are also defined.  The second section determines locations of the nodes.


## Running Opensees File through HPC

(Script needs to be established on design safe. I have a working notebook, just need to connect it with modeling script)


## Post Processing

(text here)

### Displacment Graph

(text here)

### Cross Sectional Analysis of Concrete and Steel

(text here)

### Stress and Strain Profile Movies

(text here)

### Crack Angle of Quadrature Points

(text here)







## Example Markdown Notation  

[Link Example - this goes to Google](https://www.google.com)

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
