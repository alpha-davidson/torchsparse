# 3D Sparse Convolution with Minkowski Architecture Model in TorchSparse

## Contents

In this directory, there are three folders:

alpha/

├── notebooks/

├── python/

└── shell/


The **notebooks** folder contains a notebook that visualizes the Mg22 data.

The **python** folder contains the python scripts needed for data proccessing and model training and evaluation, as well as plot generation. 

The **shell** folder contains shell scripts that run the data and training pipelines.

## Usage

The data processing and training pipelines are very straightforward to use. Before running any code, however, ensure the data is on your local system. The data the scripts use is Mg22 + α reaction simulated data. For details on how to get the data on your local system, contact Dr. Kuchera or Dr. Ramanujan.

This code is only to be used with simulated data.

`data_processing.sh` takes the .h5 file and converts it into numpy arrays for model training. It is important to understand what the data looks like, so I recommend using the notebook to visualize the structure of the data in order to make changes to the data processing scripts where needed.

`training.sh` is a collection of several Python scripts that carry out the training pipeline, starting from model training, to loss curve plotting, model evaluation, and confusion matrix creation. When the code is run, there will be a new folder, training, created that will store all the training plots and statistics.

## Further Objectives and Implementation

### Checkpoint Loading
As of writing, there is no implementation for loading the checkpoints to resume training. I have implemented a proccess to save model checkpoints, but not yet a way to utilize them. It should not be difficult to do, as it would just need to involve the creation of new shell and python scripts that will load in the data.

### Point Classification to Event Classification
Currently, the model is for point classification. I believe that the MinkUNet Model needs to be modified as well as the upsampling layers should actually be removed, but this is not high priority. The next main project will be the implementation of event-wise classification for track counting. The current architecture is for point classification, so there will need to be changes with how the data and model architecture is structured. Essentially, it will be a completely new separate implementation of the TorchSparse package.