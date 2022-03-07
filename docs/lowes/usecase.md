# Modeling Reinforced Concrete Walls with Shell Elements to Simulate Through Opensees and Using Jupyter to Post Process Results

**Josh Stokley and Laura Lowes, University of Washington**  

The purpose of this use case is to be able to model, simulate, and post process multiple reinforced concrete walls at once. This use case uses jupyter notebooks to model these walls with shell elements and uses OpenSeesMP on DesignSafe to simulate the models. The documentation of this use case will use a single wall, RW1, as an example to understand the workflow and objectives of this use case. The following DesignSafe resources are used:  
(jupyter notebook link)  
(opensees link) 


<!--- this is a comment --->    
<!--- this is a comment --->  
<!--- this is a comment --->  
<!--- this is a comment --->  
<!--- this is a comment --->  

### Citation and Licensing

* Please cite [Shegay et al. (2021)](https://doi.org/10.17603/ds2-r12q-t415) to acknowledge the use of any data from this use case.

* Please cite [Lu XZ et al. (2015)](http://www.luxinzheng.net/download/OpenSEES/En_THUShell_OpenSEES.htm ) to acknowledge the use of the modeling strategy from this use case.

* Please cite [Rathje et al. (2017)](https://doi.org/10.1061/(ASCE)NH.1527-6996.0000246) to acknowledge the use of DesignSafe resources.  

* This software is distributed under the GNU General Public License (https://www.gnu.org/licenses/gpl-3.0.html).  

## Background  

### Data  

The walls that are modeled are defined in a database provided by Alex Shegay. The database is a MATLAB variable of type 'structure'. The tree-like structure of the variable consists of several levels. Each level consists of several varaiables, each being a 1x142 dimension array. Each entry within the array corresponds to a separate wall specimen. The order of these entries is consistent throughout the database and reflects the order of walls as appearing in the 'UniqueID' array.  
His work can be found here: (ALEX MATLAB LINK) 

### Modeling

The modeling techniques are inspired by the work of Lu XZ.
The modeling of these walls make use of the MITC4 shell element. This element smears concrete and steel in multiple layers through the thickness of the element. Figure 1 demonstrates this.  Within the shell element, only the transverse steel is smeared with the concrete. The shell elements are modeled to be square or close to square for best accuracy, an assumption that follows this is that cover concrete on the ends of the wall are not taken into account as it would produce skinny elements that would cause the wall to fail prematurely. The vertical steel bars are modeled as trusses up the wall to better simulate the stress of those bars.  The opensees material models that are used are:  

* PlaneStressUserMaterial- Utilizes damage mechanisms and smeared crack model to defin a multi-dimensional concrete model  
    * Variables include: compressive strength, tensile strength, crushing strength, strain at maximum and crushing strengths, ultimate tensile strain, and shear retention factor
    * Model can be found following the previous link under Lu XZs work
 
* Steel02- Uniaxial steel material model with isotropic strain hardening
    * Variables include: yield strength, initial elastic tangent, and strain hardening ratio  
    * Model can be found here: [Steel02 OpenSees](https://opensees.berkeley.edu/wiki/index.php/Steel02_Material_--_Giuffr%C3%A9-Menegotto-Pinto_Model_with_Isotropic_Strain_Hardening)  

![SchematicView](img/ShellEle.JPG)  
Figure 1: Smeared shell element representation  

## Example Description 

RW1 is modeled from the database to produce a tcl file that represents the geometry, material, and simulation history of the wall. The wall is 144 inches high, 47.25 inches long, and 4 inches thick. It consists of 1241 amount of nodes, 1152 amount of shell elements, and 863 amount of steel truss elements. MITC4 shell elements are used to smear the concrete and transverse steel into the thickness while the vertical reinforce bars are modeled as truss elements. RW1 had a compression buckling failure mode in the lab. More information on RW1 and its experimental results can be found here: (RW1 LINK)  
 
(Model picture of RW1 goes here)  

The use case workflow involves the following steps:

* Using Jupyter notebook modeling script to create input file for OpenSees
* Running input file through HPC on DesignSafe
* Using Jupyter notebook post processing scripts to evaulate model


## Create Input File using Modeling Script

The jupyter notebook that creates the OpenSees input file can be found here: (LINK TO FILE).

### Reinforced Concrete Wall Database   



RW1 is wall 33 in the database and that number will be the single input to the modeling script.



### Modeling Script 

The modeling script imports the variables from the database necassary to build a continuum model for a wall.  
* Section 1: Initializion of the model. The degrees of fredom are defined and the variables that carry uncertainty are also defined.  
<!--- for each section I will have a side by side comaparison of code to RW1 tcl file---> 
* Section 2: Defines nodal Locations.
* Section 3: Defines material models and their variables.
* Section 4: Defines the continuum shell model and the thicknesses of transverse steel and concrete.
* Section 5: Defines the eleemnts acrosss the width and height. Also adds vertical truss bars up the height.
* Section 6: Defines constraints
* Section 7: Defines recorders
* Section 8: Defines and applies the gravity load of the wall.
* Section 9: Defines the cyclic anaylsis of the wall.


## Running Opensees File through HPC

(Script needs to be established on design safe. I have a working notebook, just need to connect it with modeling script)


## Post Processing

After the script is finished running through OpenSees, there are multiple post-processing scripts that can be used to analyize the simulation and compare it to the experimental numbers.

### Load-Displacment Graph

The Load-Displacement script compares the experimental cyclic load history to the simulated cyclic load output. This Script can be found here:  
(insert RW1 load-displacement graph here)

### Cross Sectional Analysis of Concrete and Steel

The cross sectional script shows stress and strain output across the cross section of the first level for the concrete and steel at various points on the displacement history. This script can be found here:  
(insert RW1 anaylsis graphs here)

### Stress and Strain Profile Movies

The Stress/Strain profile movie script utilizes plotly to create an interactive animation of stresses and strains on the wall throughout the load history. The stress animations are vertical stress, shear stress, and maximum and minimum principal stress. The strain animations are vertical strain, shear strain, and maximum and minimum principal strain. This script can be found here:
(Insert snapshots of RW1 here)

### Crack Angle of Quadrature Points

The crack angle script will show at what angle each quadrature point cracks. This script can be found here:  
(insert crack graph)







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
