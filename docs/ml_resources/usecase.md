# An Example-Based Introduction to Common Machine Learning Approaches

**Joseph P. Vantassel, Texas Advanced Computing Center - The University of Texas at Austin**  
**Wenyang Zhang, Texas Advanced Computing Center - The University of Texas at Austin**  

With the increasing acquisition and sharing of data in the natural hazards community, solutions from 
data science, in particular machine learning, are increasingly being applied to natural hazard problems.
To better equip the natural hazards community to understand
and utilize these solution this use case presents an example-based introduction to common machine
learning approaches. This use case is not intended to be exhaustive in its coverage
of machine learning approaches (as there are many), nor in its coverage of the selected approaches
(as they are more complex than can be effectively communicated here), rather, this use case is
intended to provide a high-level overview of different approaches to using machine learning to
solve data-related problems.

## Overview

This use case is example-based meaning that its contents have been organized into self-contained examples.
These self-contained example are organized by machine learning algorithm. Importantly, the machine learning
algorithm applied to the specific example provided here are not the only (or even necessarily the optimal)
algorithm for that particular (or related) problem, instead the datasets considered are used merely for example
and teh algorithm applied is but one of the potentially many reasonable alternatives one could use to solve
that particular problem. The focus of these examples is to demonstrate the general procedure for applying that
particular machine learning algorithm and does not necessarily indicate that this is the correct or optimal
solution.

### Linear Regression - (Vantassel)

Linear regression seeks to find linear relationships between features in a dataset and an associated set of labels
(i.e., real values to be predicted). Linear regression is one of the simplest machine learning algorithms and
likely one that many natural hazards researchers will already be familiar with from undergraduate mathematics
coursework (e.g., statistics, linear algebra). The example for linear regression presented in this use case shows
the process of attempting to predict housing prices from house and neighborhood characteristics. The notebooks cover
how to perform basic linear regression using the raw features, combine those features (also called feature crosses) to
produce better predictions, use regularization to reduce overfitting, and use learning curves as a diagnostic tool for
machine learning problems.

[Link to Linear Regression Example](TODO)

### Random Forest - (Zhang)

### Neural Networks - (Zhang)

### Convolutional Neural Networks - (Vantassel)

Convolutional neural networks fall under the deep learning subset of machine learning and are an effective
tool for processing and understanding image-like data. The convolutional neural network example will show an
image classification algorithm for automatically reading hand-written digits. The network will be provided
an image of a hand-written digit and predict a label classifying it as a number between 0 and 9. The notebooks
will show how to install Keras/TensorFlow, load a standard dataset, pre-process the data for acceptance by the
network, design and train a convolutional neural network using Keras/TensorFlow, and visualize output correct and
incorrect output predictions.

[Link to Convolutional Neural Network Example](TODO)


## Citation and Licensing

<!-- * Please cite [AUTHORS et al. (20xx) - example of published project]() to acknowledge the use of any resources from this use case. -->

* Please cite [Rathje et al. (2017)](https://doi.org/10.1061/(ASCE)NH.1527-6996.0000246) to acknowledge the use of DesignSafe resources.  

* This software is distributed under the GNU General Public License (https://www.gnu.org/licenses/gpl-3.0.html).
