# From constitutive parameter calibration to site response analysis

**Authors, Affiliations**  

Pedro Arduino, University of Washington

A collection of educational notebooks to introduce model paraleter calibration and site response analysis using OpenSees

## Background 

### Citation and Licensing

* Please cite [AUTHORS et al. (20xx) - example of published project](https://doi.org/10.17603/ds2-3zdj-493) to acknowledge the use of any resources from this use case.

* Please cite [Rathje et al. (2017)](https://doi.org/10.1061/(ASCE)NH.1527-6996.0000246) to acknowledge the use of DesignSafe resources.  

* This software is distributed under the GNU General Public License (https://www.gnu.org/licenses/gpl-3.0.html).  

### Description 

Site response analysis for liquefiable soils is fundamental in the estimation of demands on civil infrastructure including buildings and lifelines. Current state of the art numerical methods require the use of advance constitutive models and fully couple nonlinear finite element (FEM) tools. Advanced constitutive models require the calibration of material parameters based on experimental tests. These parameters include uncertainties that in turn propagate to uncertenties in the estimation of demands. These use-case products provide simple examples showing how to achieve this using SimCenter tools and the DesignSafe cyber infrastructure. 

[Link Example - this goes to Google](https://www.google.com)

## Header 2

### 2.1 - Notebooks published in DesignSafe
A suite of Jupyter Notebooks published in DesignSafe navigates the process of  constitutive model parameter calibration and site response analysis for a simple liquefaction case. Both notebooks leverage existing SimCenter backend functionality (e.g. Dakota, OpenSees, etc) implemented in quoFEM and run locally and in TACC through DesignSafe.
 
### 2.2 - Understanding the OpenSees simulation schema
* Understanding single element using OpenSees. 
* Understanding multiple single element analysis using OpenSeesMP.
* Understanding site response analysis using TAPIS OpenSees API in DesignSafe

*Add images to the folder img and use relative path to specify the location of the image.*   

![caption](img/mkdocs-template.png)
> Use case template design

## Header3 - Use case Jupyter Notebooks

### 3.1 - Parameter Calibration Notebook)
The parameter calibration  notebook is customized for the PM4Sand model and includes the estimation of main parameters that best fit experimental data as well as their uncertainty. 

### 3.2- Site response Notebook
The site response notebook includes the uncertainties evaluated in the parameter calibration phase for the estimation of surface response for a site with liquefiable soil. This includes surface acceleration and  lateral spreading. The notebooks expand the applicability of quoFEM adding flexibility to its existing capabilities. quoFEM projects will run smoothly in these notebooks. 

Numbered list 

1. [numbered linked item](https://maps.google.com)
2. second item
3. third item


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
