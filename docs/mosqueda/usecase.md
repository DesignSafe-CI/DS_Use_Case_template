# Integrated Workflow of Experiments using Jupyter Notebooks: From Experimental Design to Publication

**Wendy Miao, Zane Schemmer, Enrique Simbort, Gilberto Mosqueda, University of California, San Diego**  

Jupyter Notebooks can provide fully integrated workflows of experiments from documentation of experimental design through analysis and publishing of data using the DesignSafe cyberinfrastructure. A series of Notebooks are being developed to demonstrate their use in the experimental workflow including notebooks showing how to view and analyzed past published data and data from testing of a reconfigurable, modular test bed building planned to be tested on the NHERI@UC San Diego Experimental Facility. The Python-based code is implemented in a modular fashion so that components can be used as desired in other experiments and are transferable to other experimental facilities. In the examples provided, the Notebook can be used to evaluate shake table performance as well as dynamic properties of the structure. A key functionality is to increase the integration and collaboration between researchers at local or remote sites to view and analyze the experimental data during and after testing including after the data is published. As Notebooks are developed to view experimental data by the research team, they can also be published with the data allowing other researchers to quickly view the data for promoting data reuse. Examples are providing for viewing data from past shake table experiments including NEES and more current NHERI data repositories.

### Citation and Licensing

1. [Rathje et al. (2020)](https://doi.org/10.3389/fbuil.2020.547706) “Enhancing research in natural hazard engineering through the DesignSafe cyberinfrastructure”. Frontiers in Built Environment, 6:213.
2. [Van Den Einde et al (2020)](https://doi.org/10.3389/fbuil.2020.580333) “NHERI@ UC San Diego 6-DOF Large High-Performance Outdoor Shake Table Facility.” Frontiers in Built Environment, 6:181.
3. Morano M., Liu J., Hutchinson T. C., and Pantelides C.P. (2021), “Design and Analysis of a Modular Test Building for the 6-DOF Large High-Performace Outdoor Shake Table”, 17th World Conference on Earthquake Engineering, Japan.
4. [Vega et al. (2018)](https://doi.org/10.17603/DS2C687) "Five story building with tunned mass damper", in NHERI UCSD Hybrid Simulation Commissioning. DesignSafe-CI.
5. [Masroor et al. (2010)](https://doi.org/10.4231/D3HH6C57D) "Limit State Behavior of Base Isolated Structures: Fixed Base Moment Frame", DesignSafe-CI.
6. Vega et al (2020), “Implementation of real-time hybrid shake table testing using the UCSD large high-performance outdoor shake table”. Int. J. Lifecycle Performance Engineering, Vol. 4, p.80-102.
7. [Brandenberg, S., J., & Yang, Y. (2021)](https://doi.org/10.5281/zenodo.5621169) "ucla_geotech_tools: A set of Python packages developed by the UCLA geotechnical group" (Version 1.0.2) [Computer software].
8. [Mosqueda et al. (2017)](https://www.buffalo.edu/mceer/catalog.host.html/content/shared/www/mceer/publications/MCEER-13-0003.detail.html) “Seismic Response of Base Isolated Buildings Considering Pounding to Moat Walls”. Technical report MCEER-13-0003.
9. [Virtanen et al (2020)](https://doi.org/10.1038/s41592-019-0686-2) “SciPy 1.0: Fundamental Algorithms for Scientific Computing in Python”. Nature Methods, 17, 261–272.
10. Chopra A. K., Dynamics of Structures. Harlow: Pearson Education, 2012. 
11. [Rathje et al. (2017)](https://doi.org/10.1061/(ASCE)NH.1527-6996.0000246) DesignSafe: New Cyberinfrastructure for Natural Hazards Engineering. ASCE J.Struct. Eng., Vol. 18, Issue 3.
12. This software is distributed under the GNU General Public License (https://www.gnu.org/licenses/gpl-3.0.html).

## Introduction

As the cyberinfrastructure for The Natural Hazard Engineering Research Infrastructure (NHERI), DesignSafe [1] provides a collaborative workspace for cloud-based data analysis, data sharing, curation and publication of models and data. Within this workspace, Jupyter Notebooks can be applied to perform data analysis in an interactive environment with access to published data.  A rich set of data from natural hazard experiments and field studies is available from NHERI projects and its predecessor the Network for Earthquake Engineering Simulation (NEES). Since one of the major goals of DesignSafe is to provide a collaborative workspace by means of data sharing and access for data reuses, the main objective of this document is to demonstrate the use of Jupyter Notebook for viewing and analyzing published data using cloud-based tools.

This use case includes a series of Jupiter Notebooks aimed to serve as a learning tool for viewing and analyzing data from shake table experiments including:
1.	The first module examines the performance of Hybrid Simulation Experiments conducted on the 1D Large High Performance Outdoor Shake table at UC San Diego with the data published in DesignSafe [4]. This module focuses on the response of the shake table including tools to compare different signals. Data extraction and processing of measured sensor data includes comparison of time history signals, comparison of signals in the frequency domain using FFT and comparison of response spectra showing for example target and measured table response.  
2.	The second module examines the use of Jupyter Notebooks including Python libraries for structural response and system identification. In this case data from a past NEES experiment [8] of three-story moment frame structure is examined. The data published in DataDepot under as a NEES project. Using selected sensors at each story of the structure and white noise excitation, the frequencies and mode shapes of the structure are identified. The processing tools rely on existing libraries in Python demonstrating the wealth of access to subroutine that can be applied for analysis.
3.	The third module is a Jupyter notebook for viewing and analyzing data from tests on a 3-story steel Modular Testbed Building (MTB2) conducted on the recently upgrades 6DOF shake table at the UC San Diego NHEIR Experimental Facilty [2]. These tests will examine the shake table performance and structural response for the 3D structure.  These tests are currently in progress and this notebook is being updated.

## Jupyter Notebooks for Experimental Data
Jupyter Notebooks work as an interactive development environment to code and view data in a report format. Within the notebook, the combination of cells enables formatted text and interactive plotting for viewing and analyzing data.  Users can select data files and data channels for viewing and processing. with the ability to view and print complete reports. Jupyter Notebooks are accessible in DesignSafe through the workspace analysis tools and can access private or public data in Data Depot. Sample modules are presented here that have been developed using published data in Data Depot including [4] and [5]. These modules will be configured and applied within the workflow of the MTB2 during shakedown testing.

### [Case 1. Shake table performance](https://www.designsafe-ci.org/data/browser/projects/954727520918105625-242ac11c-0001-012/Jupyter_Notebook_Code_documents/Jupyter_Notebook_Project)
A set of modules have been developed to evaluate the performance of the shake table using data from past experiments conducted to demonstrate the hybrid testing capabilities of LHPOST [6]. For these hybrid tests, separate Jupyter Notebooks have been developed to consider the various sources of generated data including i) Shake Table Controller, ii) the primary Data Acquisition System (DAQ), and iii) additional computational sources for hybrid testing. In a typical shake table test, the first two sources of data would be included plus any other user specified data acquisition system.  
Data collected by the shake table controller is expected to be standard across most tests and useful to verify the performance of the shake table in reproducing the ground motions. Here, data from the shake table controller [4] is used to compare reference command and measured feedback data to evaluate the fidelity of the shake table in reproducing the desired ground motions. The Jupyter notebook functionality includes interactive plotters for viewing either a single channel or multiple channels to compare the reference input and feedback, for example, by viewing the time history, Fourier Transform or Response Spectra (Fig 1). The shake table controller sampling rate was set to a frequency of 2048 [Hz] for this test.  Initial implementation of the code required about 3.5 minutes to run. To improve the run-time, various options were explored including down sampling and use of tools such as those being developed by Brandenberg and Yang [7] to calculate the spectral acceleration. By using these tools, the run time was reduced to approximately 10 s. The module was implemented for the previous 1-D capability of LHPOST but can be easily extended for its newly upgraded 6DOF capabilities.

![caption](img/Fig.2.png)

Figure 1. Evaluation of shake table performance through comparison of command reference and feedback including a) Fourier Transform and b) response spectra .

### [Case 4. Module for Structural Response and System Identification](https://www.designsafe-ci.org/data/browser/projects/954727520918105625-242ac11c-0001-012/Jupyter_Notebook_Code_documents/Jupyter_Notebook_Project)
The primary goal of the structural response module is to quickly and accurately analyze experimental data.  For development and testing of available algorithms, experimental data from a previous dynamic experiment involving a ¼ scale three-story steel moment frame structure were used [5, 8]. A cross spectral density function (CSD) is applied to compare the white noise acceleration input at the platen to the acceleration at each floor. To improve code clarity and compatibility for future investigators, the CSD function from the SciPy signal package [9] is implemented, which is well documented. The CSD for each floor is plotted using the matplotlib library. The resulting CSD plots are shown up to 20 Hz in Fig. 3 and identify the natural frequencies of the structure. 
Modal displacements can also be calculated directly from the CSD function outputs. This is accomplished by using the frequency-power relation between acceleration spectral density functions and displacement spectral density functions [10]. The modal displacements for each story occur at frequencies where the CSD has a local maximum. To obtain these values for the test data of the three-story structure, the frequencies of the first three local maxima were recorded. For future use of this code, the desired number of mode shapes can be scaled by adding or removing local maxima terms at the start of the mode shapes code section. Using the CSD function does not take into account the sign of the modal displacement, however, since these functions are strictly positive over their domain. To account for this, the output of the CSD function at the local maxima frequencies is reexamined without considering the absolute values of its components to identify if the parameters yield a negative number at the corresponding frequency. The rough shape of the modal displacements is plotted as shown in Fig. 4. Future work for this notebook includes generating a smoothing function for the mode shapes and comparison of data from different tests to identify changes in dynamic properties through the testing series that could be indicative of damage.


![caption](img/Fig.3.png)

Figure 3. System identification of three story moment frame [5] subjected to white noise from CSD function outputs.


![caption](img/Fig.4.png)

Figure 4. Mode shapes estimation from 3-story building subjected to white noise on shake table.

### [Case 3. Integrateion of Notebooks in Experimental Workflow](https://www.designsafe-ci.org/data/browser/projects/954727520918105625-242ac11c-0001-012/Jupyter_Notebook_Code_documents/Jupyter_Notebook_Project)
The primary goal of this module is to develop the Jupyter Notebooks through the experimental program.  The experiments are in planning and thus, this module would be programmed based on draft instrumentation plans. This module will plot the primary structural response such as story accelerations and drifts as well as employ system identification routines available in Python and previously demonstrated.  Current work is exploring use of machine learning libraries for applications to these modules.  
The Modular Testbed Building (MTB2) [3] is designed to be a shared-use, reconfigurable experimental structure. The standard 3-story building can simulate braced frame and moment frame behavior through replaceable fuse type components including buckling restrained braced frames and Durafuse shear plate connections, respectively. The unique connection scheme allows for yielded fuse type members to be easily replaced to restore the structure to its original condition. The MTB2 can be constructed in various configurations with three examples shown in Fig 1. The lateral framing system in the 2-bay direction can be modeled as moment frames or braced frames. The single bay direction has a span of 20 feet and is a braced frame. Each span in the double bay direction is 16 feet. The story height for all floors is 12 feet with columns that extend 4 feet above the top floor.  The Special Moment Frame (SMF) configuration utilizes replaceable shear fuse plates while the braced frame utilizes Buckling-Restrained Braces.

![caption](img/Fig.1.png)

Figure 5.   MTB2 building: a) SMF configuration (left), b) BRB-1 configuration (center), and c) BRB-2 configuration (right).

## Conclusions
The Jupyter Notebooks developed for use through DesignSafe will facilitate the viewing and analysis of data sharing with collaborators from testing through data publication. A key advantage is the cloud-based approach that facilitates interactive data viewing and analysis in a report format without having to download large datasets. These tools are intended to make data more readily accessible and promote data reuse. The Jupiter Notebook presented here includes routines to evaluate the performance of the shake table and carry out system identification of structural models. 

## Annex 1
### [Fragment of System Identification Routine](https://www.designsafe-ci.org/data/browser/projects/954727520918105625-242ac11c-0001-012/Jupyter_Notebook_Code_documents/Jupyter_Notebook_Project)

### Cell 2
``` python
from IPython.utils import io

import numpy as np
import pandas as pd
import linecache
pd.set_option('display.max_rows', None)

#path=fc.selected
path='/home/jupyter/NEES/NEES-2008-0571.groups/Experiment-8/Trial-12/Rep-1/Unprocessed_Data/fbgm152s3.asc'
data_open = open(path) # open data and store data
print(data_open)
data = np.loadtxt(path,skiprows=6,unpack=True) # convert to readable data
n,c = data.shape
print('n=',n)
print('c=',c)
n_channels=len(data)
print(n_channels)
info_head=[]
for i in range(0,n_channels):
    info_head.append("CHAN_"+str(i+1))#create the names of the channels

data1 = pd.read_table(path,delimiter='\s+',nrows=6,skiprows=4,names=info_head)
print(data1)
DESC_CHAN=[]
UNITS_CHAN =[]

for k in range(0,n_channels):
    DESC_CHAN.append((data1.loc[0, info_head[k]]))
    UNITS_CHAN.append((data1.loc[1, info_head[k]]))  
    
tab=pd.DataFrame(list(zip(DESC_CHAN,UNITS_CHAN)), columns = ['Description','Units'])
display(tab)
```
### Description of cell 2

To begin processing data, python libraries will be utilized to form the basis of the module; this includes NumPy, pandas, and linecache. NumPy will take multiple data points about a single variable represented in arrays to compute various forms of numerical representation such as means, standard deviations, variance, and medium. For a graphical representation, pandas will allow users to manipulate datasets with various variables to produce two-dimensional tables and other graphical visualizations - displaying trends amongst the data. As the basis of the python is developed, linecache will allow users to easily search lines and trace back written codes to identify things like syntax errors.

With the basis of the module set up, the data set is now ready to be uploaded into the module. Users can begin by searching and locating the corresponding file with raw data on their local harddrive. Once the file has been located and selected, the program will then work to extract the data and replicate it onto the module. The imported data will then be examined by the module to establish a new system of organization based upon the number of variables and the number of datapoints - establishing dimension and arrays of the data set.

More specifically, the module will first identify the number of elements and its corresponding name in the table. Once the general parameters are set, the module works to transcribe the data from the original file located in the local harddrive - displaying 6 rows and skipping the 4th row. The resulting product will provide users with 2 columns, Description and Units with corresponding data points representing various measurements taken throughout the experiment.

