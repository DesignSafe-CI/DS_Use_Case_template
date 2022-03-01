# Modeling Reinforced Concrete Walls with Continuum Elements to Simulate Through Opensees and Using Jupyter to Post Process Results

**Josh Stokley and Laura Lowes, University of Washington**  

This use case example demonstrates how to use Jupyter notebook on design safe to model out multiple reinforced concrete walls and run them through (openseesMP??). 
Post processing scripts are also avaliable and able to run through designsafe, allowing for a steady flow and less steps for the user.  The example makes use of the following DesignSafe resources:

(jupyter notebook)
(opensees)

## Background 

### Citation and Licensing

* Please cite Alex Shegay ... (link) to acknowledge the use of any data from this use case.

* Please cite [AUTHORS et al. (20xx) - example of published project](https://doi.org/10.17603/ds2-3zdj-493) to acknowledge the use of any resources from this use case.

* Please cite [Rathje et al. (2017)](https://doi.org/10.1061/(ASCE)NH.1527-6996.0000246) to acknowledge the use of DesignSafe resources.  

* This software is distributed under the GNU General Public License (https://www.gnu.org/licenses/gpl-3.0.html).  

### Description 

RW1 is modeled  from the (ALEX MATLAB LINK) database to produce a tcl file that represents the geometry, material, and simulation history of the wall. The wall is y high, x long, and z thick. It consists of x amount of nodes, y amount of continuum shell elements, and z amount of steel truss elements. MITC4 shell elements are used to smear the concrete and transverse steel into the thickness while the vertical reinforce bars are modeled as truss elements. More information on RW1 and its expermintal results can be found in (RW1 LINK)

(SHELL ELEMENT PIC)
(RW1 MODEL PIC)

The use case workflow involves the following steps:

* Using Jupyter notebook modeling script to create input file for OpenSees
* Running input file through HPC on TACC
* Using Jupyter notebook post processing scripts to evaulate model


## Create Input File using Modeling Script

The jupyter notebook that creates the OpenSees input file can be found here: (LINK TO FILE).

### Reinforced Concrete Wall Database

(text here)

### Modeling Script 

(text here)


## Running Opensees File through HPC

(text here)


## Post Processing

(text here)

### Displacment Graph

(text here)

### Stress and Strain Profile Movies

(text here)

### Cross Sectional Analysis of Concrete and Steel

(text here)

### Crack Angle of Quadrature Points

(text here)







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
