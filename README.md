# ECE/MAE 148 Team 7 Machine Learning Notebooks

The repo consists of the Jupyter notebooks we used to train our pedestrian intention AI, more in this [repo](https://github.com/buzzcrackle/ece148-team7) and this [wiki](https://guitar.ucsd.edu/maeece148/index.php/2021SpringTeam7).

## Instructions for Notebooks
#### live_demo.ipynb
 Notebook to view live demo of pose estimation with an NVidia Jetson and camera. Also collects pose estimation training data. Based on [TRT_pose live demo](https://github.com/NVIDIA-AI-IOT/trt_pose).

##### Instructions
* Follow instructions at this [repo](https://github.com/NVIDIA-AI-IOT/trt_pose) to install dependencies
* Remember to download resnet18_baseline_att_224x224 and place into repo directory.
* Run notebook!

##### How to save time!
The notebook will optimize for Jetson by converting the model into a TRT model, this may take up to 20 minutes in my experience. When it finishes optimizing, it will save the TRT model and you can then comment out sections that load the original model.

##### Data collection
For our pedestrian intention AI, we take the detected points from pose estimation to train another model. I included code to easily collect and store these pose estimation points into files. Follow the instructions within the notebook. The code records data whenever a set of pose estimation points is detected and saves it to a CSV file that contains that specific set of points. For example, if only the head is detected, then that data is put into file with only data points of the head.
#### pose_est_dl.ipynb
Fairly self explanatory notebook. Uses deep learning to train classificaiton model. Uses data collected by the previous notebook.
#### pose_est_svm.ipynb
Proven to be less effective, but has interesting concept.

SVM implementation of classification. Trains multiple models on all data collected in live_demo.ipynb. Not all points are captured at every pose estimation frame. This notebook trains a classification model for all collected data. For example, if a dataset only contains arm data, it will train on only that data. Better than the deep learning model in some ways since it is lower resource and can predict on any set of data.