# From constitutive parameter calibration to site response analysis

**Authors, Affiliations**  

Pedro Arduino, University of Washington

A collection of educational notebooks to introduce model paraleter calibration and site response analysis using OpenSees in ther DesignSafe-CI

## Background 

### Citation and Licensing

* Please cite [Arduino, P. et al. (2022)](https://doi.org/10.17603/ds2-3zdj-493) to acknowledge the use of any resources from this use case.

* Please cite [Rathje et al. (2017)](https://doi.org/10.1061/(ASCE)NH.1527-6996.0000246) to acknowledge the use of DesignSafe resources.  

* This software is distributed under the GNU General Public License (https://www.gnu.org/licenses/gpl-3.0.html).  

### Description 

Site response analysis for liquefiable soils is fundamental in the estimation of demands on civil infrastructure including buildings and lifelines. Current state of the art in numerical methods require the use of advance constitutive models and fully couple nonlinear finite element (FEM) tools. Advanced constitutive models require calibration of material parameters based on experimental tests. These parameters include uncertainties that in turn propagate to uncertenties in the estimation of demands. The products included in this use-case provide simple examples showing how to achieve site response analysis including parameter identification and uncertainty quantification using SimCenter tools and the DesignSafe cyber infrastructure.

[//]: <![Propagation of vertical waves in site response analysis](img/SRschematic2.PNG){width=50%}>

<p align="center">
<img src="img/SRschematic2.PNG" alt="Propagation of vertical waves in site response analysis" width="600"/>
</p>
<p align="center"> <b>Fig.1 - Site response problem</b> </p>
    
[Link Example - this goes to Google](https://www.google.com)

For this purpose, this document introduces (describes) a suite of Jupyter Notebooks published in DesignSafe that navigate the process of  constitutive model parameter calibration and site response analysis for a simple liquefaction case. They also introduce specific methods useful when using DesignSafe infrastructure in TACC. All notebooks leverage existing SimCenter backend functionality (e.g. Dakota, OpenSees, etc) implemented in quoFEM and run locally and in TACC through DesignSafe. Three notebooks are included for this purpose: 
1. Site response workflow notebook: This notebook introduces typical steps used in any site response workflow taking advantage of the Jupyter lab available in DesignSafe.
2. Parameter calibration notebook: This  notebook is customized for the PM4Sand model and present the estimation of main parameters that best fit experimental data as well as their uncertainty.
3. Propagation of parameter undertainty in site response analysis notebook: This notebook introduces methods to propagate material parameter uncertainties in site reponse analysis.

The current version of this use-case page is a work in progress and presents details on the site response workflow notebook. The parameter calibration and propagation of uncertainties notebooks will be updated in a second version.

### Parameter calibration notebook)
The parameter calibration  notebook is customized for the PM4Sand model and includes the estimation of main parameters that best fit experimental data as well as their uncertainty (IN PROGRESS). 

### Site response workflow notebook
The *site response workflow notebook* presents typical steps used in the evaluation of the surface response for a site with liquefiable soil.
The notebook takes advantage of the site response problem to introduce a general numerical analysis workflow that includes: 

1. running OpenSees using a tapis app, 
2. postprocessing results using python, 
3. generating authomatic reports using pdflatex or rst2pdf, and 
4. taking advantage of visualization widgets. 

A simple example of a liquefiable soil profile is used to demonstrate each step. The soil profile shown in Figure 2 includes a 5.0m loose sand underlain by a 1.0 dense soil.The loose sand is modeled using the PM4Sand constitutive model for liquefiable soils available in OpenSees. The dense sand is considered linear elastic. The groundwter table is assumed at 2.0m making the lower 3.0m of the loose sand susceptible to liquefaction. The soil profile is subject to a dynamic excitation at its base. The site response of interest includes surface acceleration, profiles of lateral displacement, maximum shear strain, pore water pressure ratio (Ru), and peak ground acceleration (PGA).  The model definition, analysis steps, and recorders are all contained in the N10_T3.tcl, and the input signal is in velocity.input. The model can be run using OpenSees in any OS framework and the files are available in this link.

[//]: <![N10_T3 soil profile with liquefiable layer](img/SPschematic.png){width=50%}>
<p align="center">
<img src="img/SPschematic.png" alt="N10_T3 soil profile with liquefiable layer" width="200"/>
</p>
<p align="center"> <b>Fig.2 - N10_T3 soil profile with liquefiable layer</b> </p>


The notebook can be discect into four main components:

<ol type="a">
  <li>Setup tapis/agave app and run OpenSees job</li>
  <li>Post process results</li>
  <li>Generate report</li>
  <li> Generate interactive plots</li>
</ol>

Each component is described below.

### Setup tapis/agave app and run OpenSees job

#### Setup job description

```python
from agavepy.agave import Agave
ag = Agave.restore()
import os

app_name = 'OpenSeesSP'
app_id = 'OpenseesSp-3.3.0u1'
storage_id = 'designsafe.storage.default'
...
...
```

#### Run OpenSees Job
```python
import time
job = ag.jobs.submit(body=job_description)
print(" Job launched. Status provided below")
print(" Can also check in DedignSafe portal under - Workspace > Tools & Application > Job Status")

status = ag.jobs.getStatus(jobId=job["id"])["status"]
while status != "FINISHED":
    status = ag.jobs.getStatus(jobId=job["id"])["status"]
    print(f"Status: {status}")
    time.sleep(60)
```    

### Postprocess Results

#### Identify job, archived location and user

``` python
jobinfo = ag.jobs.get(jobId=job.id)
jobinfo.archivePath
user = jobinfo.archivePath.split('/', 1)[0]

import os
%cd ..
cur_dir_name = cur_dir.split('/').pop() 
os.chdir(jobinfo.archivePath.replace(user,'/home/jupyter/MyData'))
if not os.path.exists(cur_dir_name):
    os.makedirs(cur_dir_name)
os.chdir(cur_dir_name)    
```
#### Plot Results

Plot acceleration time hisotory and response spectra on log-linear scale
``` python
from plotAcc import plot_acc
plot_acc()
```
![Surface acceleration](img/surfaceAccel.png)
![Response spectrum](img/logSpectra.png)


Plot profiles
``` python
from plotProfile import plot_profile
plot_profile()
```
![Profile plots](img/profilePlot.png)


Plot excess pore water pressure
``` python
from plotPorepressure import plot_porepressure
plot_porepressure()
```
![Pore pressure](img/porePressure.png)


#### Generate report (pdflatex, rst2pdf) 

Run rst2pdf, assign to pdf_fn, and  call PDF show function 
``` python
import sys
!{sys.executable} -m pip install rst2pdf
os.system('rst2pdf ShortReport.rst ShortReport.pdf')

pdf_fn = jobinfo.archivePath.replace(user, '/user/' + user + '/files/MyData')
pdf_fn += '/'
pdf_fn += cur_dir.split('/')[-1]
pdf_fn += '/ShortReport.pdf'
print pdf_fn

PDF(pdf_fn , (750,600))
```

PDF function 
``` python
class PDF(object):
  def __init__(self, pdf, size=(200,200)):
    self.pdf = pdf
    self.size = size

  def _repr_html_(self):
    return '<iframe src={0} width={1[0]} height={1[1]}></iframe>'.format(self.pdf, self.size)

  def _repr_latex_(self):
    return r'\includegraphics[width=1.0\textwidth]{{{0}}}'.format(self.pdf)
```

#### Create Interactive Plots

Pore water pressure
``` python
rom interactiveplot import createpwpplot, createDispplot
createpwpplot()
```
Displacement 
``` python
createDispplot()
```

## Header 2  -- END OF PAGE

### 2.1 - Notebooks published in DesignSafe
A suite of Jupyter Notebooks published in DesignSafe navigates the process of  constitutive model parameter calibration and site response analysis for a simple liquefaction case. Both notebooks leverage existing SimCenter backend functionality (e.g. Dakota, OpenSees, etc) implemented in quoFEM and run locally and in TACC through DesignSafe. (IN PROGRESS)
 
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
