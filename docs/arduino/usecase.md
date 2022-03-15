# From constitutive parameter calibration to site response analysis

**Authors, Affiliations**  

Pedro Arduino, University of Washington

A collection of educational notebooks to introduce model paraleter calibration and site response analysis using OpenSees

## Background 

### Citation and Licensing

* Please cite [Arduino, P. et al. (2022)](https://doi.org/10.17603/ds2-3zdj-493) to acknowledge the use of any resources from this use case.

* Please cite [Rathje et al. (2017)](https://doi.org/10.1061/(ASCE)NH.1527-6996.0000246) to acknowledge the use of DesignSafe resources.  

* This software is distributed under the GNU General Public License (https://www.gnu.org/licenses/gpl-3.0.html).  

### Description 

Site response analysis for liquefiable soils is fundamental in the estimation of demands on civil infrastructure including buildings and lifelines. Current state of the art numerical methods require the use of advance constitutive models and fully couple nonlinear finite element (FEM) tools. Advanced constitutive models require calibration of material parameters based on experimental tests. These parameters include uncertainties that in turn propagate to uncertenties in the estimation of demands. The products included in this use-case provide simple examples showing how to achieve this using SimCenter tools and the DesignSafe cyber infrastructure.

![caption](img/SRschematic2.PNG)
> Use case template design

[Link Example - this goes to Google](https://www.google.com)

For this purpose this page presents a suite of Jupyter Notebooks published in DesignSafe that navigate the process of  constitutive model parameter calibration and site response analysis for a simple liquefaction case. Both notebooks leverage existing SimCenter backend functionality (e.g. Dakota, OpenSees, etc) implemented in quoFEM and run locally and in TACC through DesignSafe.

### Parameter Calibration Notebook)
The parameter calibration  notebook is customized for the PM4Sand model and includes the estimation of main parameters that best fit experimental data as well as their uncertainty (IN PROGRESS). 

### Site response Notebook
The site response notebook presents the estimation of the surface response for a site with liquefiable soil using OpenSees and an advanced constitutive model. The soil profile (Figure 1) includes a 5.0m loose sand underlain by a 1.0 dense soil.The loose sand is modeled in OpenSees using and advanced constitutive model for liquefiable soils (PM4Sand). The dense sand is considered linear elastic. The groundwter table is assumed at 2.0m making the bottom 3.0m of the loose sand susceptible to liquefaction. The soil profile is subject to a dynamic excitation at its base. The response includes surface acceleration, profiles of lateral displacement, maximum shear strain, pore water pressure ratio (Ru), and peak ground acceleration (PGA) pore water pressure  and  lat.  

![caption](img/SPschematic.png)
> Use case template design


### Setup agave and start OpenSees job

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
Plot profiles
``` python
from plotProfile import plot_profile
plot_profile()
```
Plot excess pore water pressure
``` python
from plotPorepressure import plot_porepressure
plot_porepressure()
```

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
