# Integrated Workflow of Experiments using Jupyter Notebooks: From Experimental Design to Publication

**Wendy Miao, Zane Schemmer, Enrique Simbort, Gilberto Mosqueda, University of California, San Diego**  

Jupyter Notebooks can provide fully integrated workflows of experiments from documentation of experimental design through analysis and publishing of data using the DesignSafe cyberinfrastructure. A serires of Notebooks are being developed to demonstrate their use in the experimental workflow including recent testing of a reconfigurable, modular test bed building planned for testing on the NHERI@UC San Diego Experimental Facility. The Python-based code is being implemented in a modular fashion so that components can be used as desired in other experiments and is transferable to other experimental facilities.  The Notebook can be used to evaluate shake table performance as well as dynamic properties of the structure. A key functionality is to increase the integration and collaboration between researchers at local or remote sites to view and analyze the experimental data during and after testing including once the data is published. Additional Notebooks are available using for viewing data from past shake table experiments including NEES and NHERI funded experiments.

## HYBRID SHAKE TABLE FORMULATION 

### Citation and Licensing

* [Brandenberg, S., J., & Yang, Y. (2021)](https://doi.org/10.5281/zenodo.5621169) "ucla_geotech_tools: A set of Python packages developed by the UCLA geotechnical group" (Version 1.0.2) [Computer software].
* Morano M., Liu J., Hutchinson T. C., and Pantelides C.P. (2021), “Design and Analysis of a Modular Test Building for the 6-DOF Large High-Performace Outdoor Shake Table”, 17th World Conference on Earthquake Engineering, Japan.
* [Rathje et al. (2020)](https://doi.org/10.3389/fbuil.2020.547706) “Enhancing research in natural hazard engineering through the DesignSafe cyberinfrastructure”. Frontiers in Built Environment, 6:213.
*  [Van Den Einde et al (2020)](https://doi.org/10.3389/fbuil.2020.580333) “NHERI@ UC San Diego 6-DOF Large High-Performance Outdoor Shake Table Facility.” Frontiers in Built Environment, 6:181.
* Vega et al (2020), “Implementation of real-time hybrid shake table testing using the UCSD large high-performance outdoor shake table”. Int. J. Lifecycle Performance Engineering, Vol. 4, p.80-102.
* [Virtanen et al (2020)](https://doi.org/10.1038/s41592-019-0686-2) “SciPy 1.0: Fundamental Algorithms for Scientific Computing in Python”. Nature Methods, 17, 261–272.
* [Mosqueda et al. (2017)](https://www.buffalo.edu/mceer/catalog.host.html/content/shared/www/mceer/publications/MCEER-13-0003.detail.html) “Seismic Response of Base Isolated Buildings Considering Pounding to Moat Walls”. Technical report MCEER-13-0003.
* [Rathje et al. (2017)](https://doi.org/10.1061/(ASCE)NH.1527-6996.0000246) DesignSafe: New Cyberinfrastructure for Natural Hazards Engineering. ASCE J.Struct. Eng., 
Vol. 18, Issue 3.
* [Vega et al. (2018)](https://doi.org/10.17603/DS2C687) "Five story building with tunned mass damper", in NHERI UCSD Hybrid Simulation Commissioning. DesignSafe-CI.
* Chopra A. K., Dynamics of Structures. Harlow: Pearson Education, 2012. 
* [Masroor et al. (2010)](https://doi.org/10.4231/D3HH6C57D) "Limit State Behavior of Base Isolated Structures: Fixed Base Moment Frame", DesignSafe-CI.
* This software is distributed under the GNU General Public License (https://www.gnu.org/licenses/gpl-3.0.html).






### Introduction
The Natural Hazard Engineering Research Infrastructure (NHERI) DesignSafe [1] cyberinfrastructure provides a collaborative Workspace for cloud-based data analysis and the Data Depot for publishing curated data. Jupyter Notebooks can function across these tools to provide an interactive programable environment in Python for data viewing and analysis. Research teams can initially share and view data in a private collaborative environment while they conduct their analysis then publish the Notebook and curated data for simplified viewing by other researchers interested in data reuse.  A significant advantage is the cloud-based approach that allows for thorough exploration of the data without requiring downloading of potentially large data sets. 
To demonstrate the use of Jupyter Notebook within the experimental workflow, an application is being explored for use with the first experiment to be conducted following the upgrade to 6DOF of the Large High Performance Shake Table (LHPOST6) at the NHERI@UC San Diego Experimental Facility [2].  The first test to be conducted will involve the shakedown of a Modular Tested Building (MTB2) planned for early 2022 [3]. The MTB2 consists of a two-bay by one-bay, 3-story steel building that will be available for future use on the LHPOST6 to examine the behavior of the building itself under 3-D shaking or examine the behavior of other systems such as protective systems and nonstructural systems that can be installed within the MTB2. The initial testing of the MTB2, thus provides an ideal application for the Jupyter Notebook that will allow for simplified viewing of data generated from these tests that will be of interest to future users of the MTB2. The development of the Jupyter Notebooks is being deployed for use while conducting the experiments and for publication with the data after testing. The modules for analysis are being developed using shake table test data from past experiments. Modules and functionality developed to date are presented here. The full application of the Jupyter notebook will be undertaken in conjunction with the shake down experiments.

### Modular Testbed Building
The Modular Testbed Building (MTB2) is designed to be a shared-use, reconfigurable experimental structure. The standard 3-story building can simulate braced frame and moment frame behavior through replaceable fuse type components including buckling restrained braced frames and Durafuse shear plate connections, respectively. The unique connection scheme allows for yielded fuse type members to be easily replaced to restore the structure to its original condition. The MTB2 can be constructed in various configurations with three examples shown in Fig 1. The lateral framing system in the 2-bay direction can be modeled as moment frames or braced frames. The single bay direction has a span of 20 feet and is a braced frame. Each span in the double bay direction is 16 feet. The story height for all floors is 12 feet with columns that extend 4 feet above the top floor.  The Special Moment Frame (SMF) configuration utilizes replaceable shear fuse plates while the braced frame utilizes Buckling-Restrained Braces. 


### Development of Jupyter Notebooks for Experimental Workflow
Jupyter Notebooks work as an interactive development environment to code and view data in a report format. Within the notebook, the combination of cells enables formatted text and interactive plotting for viewing and analyzing data.  Users can select data files and data channels for viewing and processing. with the ability to view and print complete reports. Jupyter Notebooks are accessible in DesignSafe through the workspace analysis tools and can access private or public data in Data Depot. Sample modules are presented here that have been developed using published data in Data Depot including [4] and [5]. These modules will be configured and applied within the workflow of the MTB2 during shakedown testing.

### Shake table performance
A set of modules have been developed to evaluate the performance of the shake table using data from past experiments conducted to demonstrate the hybrid testing capabilities of LHPOST [6]. For these hybrid tests, separate Jupyter Notebooks have been developed to consider the various sources of generated data including i) Shake Table Controller, ii) the primary Data Acquisition System (DAQ), and iii) additional computational sources for hybrid testing. In a typical shake table test, the first two sources of data would be included plus any other user specified data acquisition system.  
Data collected by the shake table controller is expected to be standard across most tests and useful to verify the performance of the shake table in reproducing the ground motions. Here, data from the shake table controller [4] is used to compare reference command and measured feedback data to evaluate the fidelity of the shake table in reproducing the desired ground motions. The Jupyter notebook functionality includes interactive plotters for viewing either a single channel or multiple channels to compare the reference input and feedback, for example, by viewing the time history, Fourier Transform or Response Spectra (Fig 2). The shake table controller sampling rate was set to a frequency of 2048 [Hz] for this test.  Initial implementation of the code required about 3.5 minutes to run. To improve the run-time, various options were explored including down sampling and use of tools such as those being developed by Brandenberg and Yang [7] to calculate the spectral acceleration. By using these tools, the run time was reduced to approximately 10 s. The module was implemented for the previous 1-D capability of LHPOST but can be easily extended for its newly upgraded 6DOF capabilities.


### Module for Structural Response and System Identification
The primary goal of the structural response module is to quickly and accurately analyze experimental data. As such, this module would be constructed based on draft instrumentation plans for the MTB2. This Data module will plot the primary structural response such as story accelerations and drifts as well as employ system identification routines available in Python.  Current work is exploring use of machine learning libraries for applications to these modules.  For development and testing of these algorithms, test data from a previous dynamic experiment involving a ¼ scale three-story steel moment frame structure were used [5, 8] and demonstrated here. A cross spectral density function (CSD) is applied to compare the white noise acceleration input at the platen to the acceleration at each floor. To improve code clarity and compatibility for future investigators, the CSD function from the SciPy signal package [9] is implemented, which is well documented. The CSD for each floor is plotted using the matplotlib library. The resulting CSD plots are shown up to 20 Hz in Fig. 3 and identify the natural frequencies of the structure. The developed module can be adjusted to accommodate different experimental requirements and will be adopted for the MTB2 experiments.
Modal displacements can also be calculated directly from the CSD function outputs. This is accomplished by using the frequency-power relation between acceleration spectral density functions and displacement spectral density functions [10]. The modal displacements for each story occur at frequencies where the CSD has a local maximum. To obtain these values for the test data of the three-story structure, the frequencies of the first three local maxima were recorded. For future investigators wishing to use this code for smaller or larger versions of the MTB2, the desired number of mode shapes can be scaled by adding or removing local maxima terms at the start of the mode shapes code section. Using the CSD function does not take into account the sign of the modal displacement, however, since these functions are strictly positive over their domain. To account for this, the output of the CSD function at the local maxima frequencies is reexamined without considering the absolute values of its components to identify if the parameters yield a negative number at the corresponding frequency. The rough shape of the modal displacements is plotted as shown in Fig. 4. Future work for this notebook includes generating a smoothing function for the mode shapes and comparison of data from different tests to identify changes in dynamic properties through the testing series that could be indicative of damage.

### Conclusions
The Jupyter Notebooks developed for use through DesignSafe will facilitate the viewing and analysis of data sharing with collaborators from testing through data publication. A key advantage is the cloud-based approach that facilitates interactive data viewing and analysis in a report format without having to download large datasets. Jupyter Notebooks are being developed for the first structural model to be tested on LHPOST6. in a modular fashion to allow flexibility in use of components and simplify the application for other experiments. The modules presented here include tools to evaluate the performance of the shake table and system identification of the structural models and can be readily extended to include other features. Current work for further development includes exploring applications of machine learning libraries for system identification and improving plotting capabilities.








### Description 

The main objective of the present Jupiter Notebook is to develop an interactive computing platform able to perform system identification procedures of a three degree of freedom system based on real test results, as well as offer all the potential users a tool to start learning system identification on a simple structure.

[Link Example - this goes to Google](https://www.google.com)

## Analysis Cases

The system identification of the structure is carried out for three analysis cases:
1.	White noise signal
2.	Dynamic elastic/inelastic response of the structure
3.	Impact loads coming from for base isolated building pounding a moat wall-the superstructure response.


### System Identification

In all these cases system identification analysis is implemented based on the estimation of the cross power spectral density of the structural response. However, one of the goals that is pursued with the implementation of this notebook is the application of Machine Learning as a tool to obtained important dynamic characteristic of the structures, estimate the uncertainty of common applied procedures as well as to show a “new” alternative solution based on both computational mechanics and deep learning algorithms.
The system identification analysis is performed on experimental data published in the Technical Report MCEER-13-0003. This report describes both the analytical and experimental procedures to assess the dynamic response of a base isolated structure when it is subject to impact force. This data is subsequently used to validate the numerical models of structural pounding. In addition to generating unique data on structural pounding, the behavior of a base isolated building impacting different types of moat wall installed at different gap distance was also of investigated.
The abstract of the Jupiter notebook describes the experimental program designed to capture the structural response of base isolated building when it impacts against a surrounding moat wall under extreme ground motions.


*Add images to the folder img and use relative path to specify the location of the image.*   

![caption](img/Fig.1.png)
> Use case template design


## About Technical Report MCEER-13-0003

The results that are used in the system identification analysis are obtained from a test program consisting of shake table testing of a quarter-scale model representative of the three-story IMRF at the Structural Engineering and Earthquake Simulation Laboratory (SEESL) at the University at Buffalo.
The base isolated IMRF model was selected for the experimental program due to availability of scaled members and simplicity in fabrication. However, both base isolated buildings including the IMRF and OCBF are used in numerical simulations presented latter in this report. The principal objective of these experiments was to generate experimental data for base isolated building pounding a moat wall, specifically the impact force and the superstructure response. This data is subsequently used to validate the numerical models of structural pounding. In addition to generating unique data on structural pounding, the behavior of a base isolated building impacting different types of moat wall installed at different gap distance was also of investigated. [extract from Technical Report MCEER-13-0003.]
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

``` python
from IPython.utils import io

def myfunc():
    # Install a pip package in the current Jupyter kernel
    import sys
    !{sys.executable} -m pip install --user ipyfilechooser
with io.capture_output() as captured:
    myfunc()
    
from ipyfilechooser import FileChooser

# Create and display a FileChooser widget
fc = FileChooser('/home/jupyter/NEES/NEES-2008-0571.groups/Experiment-8')
#display(fc)
```
Description of cell 1

Description of what is excecuted in this cell 1.
Why do we need to install a pip package in the current Jupyter kernel? What does FileChooser execute?

``` python
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
Description of cell 2

Description of what is excecuted in this cell 2
Main steps of uploading, reading data, and getting ready to process it.

``` python
import matplotlib.pyplot as plt
from matplotlib import animation

time=data[0]
print(time.shape)
A1=data[25]
A2=data[26]
cc = np.array([ A1, A2 ])
print(cc.shape)
av=np.mean( np.array([ A1, A2 ]), axis=0 )
print(A1.shape)
print(A2.shape)
print(av.shape)

story_1=np.mean( np.array([ data[30], data[31] ]), axis=0 )
story_2=np.mean( np.array([ data[32], data[33] ]), axis=0 )
story_3=np.mean( np.array([ data[34], data[35] ]), axis=0 )

fig, ax=plt.subplots(1, figsize=(9.5,5))
ax.plot(time,A1, label='A1')
ax.plot(time,A2, label='A2')
ax.plot(time,av, label='Average')
ax.set_xlabel('Time [seconds]')
ax.set_ylabel('Acceleration [g]')
ax.set_title('Base Plate')
ax.legend()

plt.show()

fig, ax1=plt.subplots(1, figsize=(9.5,5))
ax1.plot(time,data[30], label='A6')
ax1.plot(time,data[31], label='A7')
ax1.plot(time,story_1, label='Average')
ax1.set_xlabel('Time [seconds]')
ax1.set_ylabel('Acceleration [g]')
ax1.set_title('Level 1')
ax1.legend()

plt.show()

fig, ax2=plt.subplots(1, figsize=(9.5,5))
ax2.plot(time,data[32], label='A8')
ax2.plot(time,data[33], label='A9')
ax2.plot(time,story_2, label='Average')
ax2.set_xlabel('Time [seconds]')
ax2.set_ylabel('Acceleration [g]')
ax2.set_title('Level 2')
ax2.legend()

plt.show()

fig, ax3=plt.subplots(1, figsize=(9.5,5))
ax3.plot(time,data[34], label='A10')
ax3.plot(time,data[35], label='A11')
ax3.plot(time,story_3, label='Average')
ax3.set_xlabel('Time [seconds]')
ax3.set_ylabel('Acceleration [g]')
ax3.set_title('Level 3')
ax3.legend()

plt.show()
```

Description of cell 3

Description of what is excecuted in this cell 3
Brief analysis of shown figures.

``` python
# Transfer Function:

from scipy import signal
import math

fs = len(time)/time[len(time)-1] # sampling frequency
print(fs)
nfft = len(time) # length of the FFT used

fxx, Sxx = signal.csd(av, av, fs, 'hann', None, None, nfft)

# 3rd Floor

fyy3, Syy3 = signal.csd(story_3, story_3, fs, 'hann', None, None, nfft)
fxy3, Sxy3 = signal.csd(av, story_3, fs, 'hann', None, None, nfft)

H1_abs3 = abs(Sxy3/Sxx)
H2_abs3 = abs(Syy3/Sxy3)

Hv_abs_nfcn3 = H1_abs3*H2_abs3

fig, ax=plt.subplots(1, figsize=(9.5,5))
ax.plot(fxy3, Hv_abs_nfcn3)
plt.show()

# 2nd Floor

fyy2, Syy2 = signal.csd(story_2, story_2, fs, 'hann', None, None, nfft)
fxy2, Sxy2 = signal.csd(av, story_2, fs, 'hann', None, None, nfft)

H1_abs2 = abs(Sxy2/Sxx)
H2_abs2 = abs(Syy2/Sxy2)

Hv_abs_nfcn2 = H1_abs2*H2_abs2

fig, ax=plt.subplots(1, figsize=(9.5,5))
ax.plot(fxy2, Hv_abs_nfcn2)
plt.show()

# 1st Floor

fyy1, Syy1 = signal.csd(story_1, story_1, fs, 'hann', None, None, nfft)
fxy1, Sxy1 = signal.csd(av, story_1, fs, 'hann', None, None, nfft)

H1_abs1 = abs(Sxy1/Sxx)
H2_abs1 = abs(Syy1/Sxy1)

Hv_abs_nfcn1 = H1_abs1*H2_abs1

fig, ax=plt.subplots(1, figsize=(9.5,5))
ax.plot(fxy1, Hv_abs_nfcn1)
plt.show()

```
Description of cell 4

Description of what is excecuted in this cell 4
Description of system Identification process. What does signal.csd implement? Regression analyisis - Supervised ML

``` phyton
# CSD Outputs

font = {'family' : 'normal',
        'weight' : 'normal',
        'size'   : 22}

plt.rc('font', **font)

fig, ax=plt.subplots(1, figsize=(9.5,5))
ax.plot(fxy3[0:2000:1], Hv_abs_nfcn3[0:2000:1])
ax.set_xlabel('Frequency (Hz)')
ax.set_ylabel('Acceleration (g^2/Hz)')
ax.set_title('Third Story CSD')
plt.show()

fig, ax=plt.subplots(1, figsize=(9.5,5))
ax.plot(fxy3[0:2000:1], Hv_abs_nfcn2[0:2000:1])
ax.set_xlabel('Frequency (Hz)')
ax.set_ylabel('Acceleration (g^2/Hz)')
ax.set_title('Second Story CSD')
plt.show()

fig, ax=plt.subplots(1, figsize=(9.5,5))
ax.plot(fxy3[0:2000:1], Hv_abs_nfcn1[0:2000:1])
ax.set_xlabel('Frequency (Hz)')
ax.set_ylabel('Acceleration (g^2/Hz)')
ax.set_title('First Story CSD')
plt.show()
```
Description of cell 5

Description of what is excecuted in this cell 5
Analysis of obtained results.

``` python
from scipy.signal import argrelextrema
from scipy import interpolate

# update if structure has more than 3 stories

max3index = argrelextrema(Hv_abs_nfcn3[0:2000:1], np.greater)
max2index = argrelextrema(Hv_abs_nfcn2[0:2000:1], np.greater)
max1index = argrelextrema(Hv_abs_nfcn1[0:2000:1], np.greater)

floor1disp = [0,0,0]
floor2disp = [0,0,0]
floor3disp = [0,0,0]

for i in [0,1,2]:
    if Sxy1[max1index[0][i]]/Sxx[max1index[0][i]] < 0 or Syy1[max1index[0][i]]/Sxy1[max1index[0][i]] < 0:
        floor1disp[i] = -Hv_abs_nfcn1[max1index[0][i]]/fxy1[max1index[0][i]]**4
    else:
        floor1disp[i] = Hv_abs_nfcn1[max1index[0][i]]/fxy1[max1index[0][i]]**4
        
    if Sxy2[max2index[0][i]]/Sxx[max2index[0][i]] < 0 or Syy2[max2index[0][i]]/Sxy2[max2index[0][i]] < 0:
        floor2disp[i] = -Hv_abs_nfcn2[max2index[0][i]]/fxy2[max2index[0][i]]**4
    else:
        floor2disp[i] = Hv_abs_nfcn2[max2index[0][i]]//fxy2[max2index[0][i]]**4
        
    if Sxy3[max3index[0][i]]/Sxx[max3index[0][i]] < 0 or Syy3[max3index[0][i]]/Sxy3[max3index[0][i]] < 0:
        floor3disp[i] = -Hv_abs_nfcn3[max3index[0][i]]/fxy3[max3index[0][i]]**4
    else:
        floor3disp[i] = Hv_abs_nfcn3[max3index[0][i]]/fxy3[max3index[0][i]]**4

mode1 = [0,floor1disp[0],floor2disp[0],floor3disp[0]]/max([abs(floor1disp[0]),abs(floor2disp[0]),abs(floor3disp[0])])
mode2 = [0,floor1disp[1],floor2disp[1],floor3disp[1]]/max([abs(floor1disp[1]),abs(floor2disp[1]),abs(floor3disp[1])])
mode3 = [0,floor1disp[2],floor2disp[2],floor3disp[2]]/max([abs(floor1disp[2]),abs(floor2disp[2]),abs(floor3disp[2])])
story = [0,1,2,3]

story_spline = np.linspace(0, 3, 300)
m1_Spline = interpolate.make_interp_spline(story, mode1)
mode1_spline = m1_Spline(story_spline)
m2_Spline = interpolate.make_interp_spline(story, mode2)
mode2_spline = m2_Spline(story_spline)
m3_Spline = interpolate.make_interp_spline(story, mode3)
mode3_spline = m3_Spline(story_spline)

fig, ax=plt.subplots(1, figsize=(3,5))
ax.plot(mode1, story)
ax.set_xlabel('Modal Displacement')
ax.set_ylabel('Story')
ax.set_title('Mode 1 Shape')
plt.show()

fig, ax=plt.subplots(1, figsize=(3,5))
ax.plot(mode2, story)
ax.set_xlabel('Modal Displacement')
ax.set_ylabel('Story')
ax.set_title('Mode 2 Shape')
plt.show()

fig, ax=plt.subplots(1, figsize=(3,5))
ax.plot(mode3, story)
ax.set_xlabel('Modal Displacement')
ax.set_ylabel('Story')
ax.set_title('Mode 3 Shape')
plt.show()

fig, ax=plt.subplots(1, figsize=(8,10))
ax.plot(mode1, story, mode2, story, mode3, story)
ax.set_xlabel('Modal Displacement')
ax.set_ylabel('Story')
ax.set_title('Modal Shapes')
ax.legend(['Mode 1', 'Mode 2', 'Mode 3'])
plt.show()
```
Description of cell 6

Description of what is excecuted in this cell 6
Description of general procedure for n dofs. So far, the program is written to compute vibration modes for 3 dofs. This function needs to be generalized.
