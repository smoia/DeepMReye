[![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](http://www.gnu.org/licenses/gpl-3.0)
![py38 status](https://img.shields.io/badge/python3.8-supported-green.svg)
![Build Status](https://github.com/DeepMReye/DeepMReye/actions/workflows/main.yml/badge.svg)
[![NatNeuro Paper](https://img.shields.io/badge/DOI-10.1038%2Fs41593--021--00947--w-blue)](https://doi.org/10.1038/s41593-021-00947-w)
![Logo](media/deepmreye_logo.png)

# DeepMReye: magnetic resonance-based eye tracking using deep neural networks
This [Jupyter Notebook](./notebooks/deepmreye_example_usage.ipynb) provides a step-by-step walkthrough of the code. It includes eyeball coregistration, voxel extraction, model training and test as well as basic performance measures. Alternatively, here is a [Colab Notebook](https://colab.research.google.com/drive/1kYVyierbKdNZ3RY4_pbACtdWEw7PKQuz?usp=sharing).

This [Data Repository](https://osf.io/mrhk9/) includes exemplary data for model training and test, source data of all paper figures as well as pre-trained model weights.

Moreover, here are additional [User Recommendations](https://deepmreye.slite.com/p/channel/MUgmvViEbaATSrqt3susLZ/notes/kKdOXmLqe) as well as a [Frequently-Asked-Questions (FAQ)](https://deepmreye.slite.com/p/channel/MUgmvViEbaATSrqt3susLZ/notes/sargIAQ6t) page. If you have other questions, please reach out to us.

![deepMReye video](media/deepMReye_video.gif)

## Installation - Option 1: Pip install

### Pip installation
Install DeepMReye with a CPU/GPU version of [TensorFlow](https://www.tensorflow.org/install/) using the following command.
```
pip install git+https://github.com/DeepMReye/DeepMReye.git
```

### Anaconda / Miniconda installation

To encapsulate DeepMReye in a virtual environment install with the following commands:
```
conda create --name deepmreye python=3.7
conda activate deepmreye
pip install git+https://github.com/DeepMReye/DeepMReye.git
```
The tensorflow version supports both CPU and GPU instructions. Note that you might need to install cudnn first (conda install -c conda-forge cudnn). 
If installation of [ANTsPy](https://github.com/ANTsX/ANTsPy) fails try to manually install it via:
```
git clone https://github.com/ANTsX/ANTsPy
cd ANTsPy
pip install CMake
python3 setup.py install
```

## Installation - Option 2: Colab

We provide a [Colab Notebook](https://colab.research.google.com/drive/1kYVyierbKdNZ3RY4_pbACtdWEw7PKQuz?usp=sharing) showcasing model training and evaluation on a GPU provided by Google Colab. To use your own data, preprocess your data locally and upload only the extracted eyeball voxels. This saves space and avoids data privacy issues. See the [Jupyter Notebook](./notebooks/deepmreye_example_usage.ipynb) for the preprocessing and eyeball-extraction code.

[![Model Training & Evaluation](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1kYVyierbKdNZ3RY4_pbACtdWEw7PKQuz?usp=sharing)

![Colab Walkthrough](media/colab_walkthrough.gif)

### Data formats
The <u>**fMRI data**</u> should be organized in 4D NIFTI files (.nii), containing the realigned 3D images acquired over time. The pipeline then extracts the eyeball voxels automatically and saves them as Python Pickle files, which serve as model input. For model training, you additionally need <u>**training labels**</u>, a numpy array containing 10 gaze coordinates per functional volume. These gaze coordinates can either be camera-based eye-tracking labels or the coordinates of a fixation target, and many file formats can be easily read (e.g. .npy, .npz, .mat, .csv etc.).

Please see our [FAQ](https://deepmreye.slite.com/p/channel/MUgmvViEbaATSrqt3susLZ/notes/sargIAQ6t) page for more details on data formats and preprocessing.

## Hardware requirements

The GPU version of DeepMReye requires a NVIDIA GPU.

## Software requirements
The following python dependencies are being automatically installed when installing DeepMReye (specified in requirements.txt):
```
tensorflow-gpu (2.2.0)
numpy (1.19.1)
pandas (1.0.5)
matplotlib (3.2.2)
scipy (1.5.0)
ipython (7.13.0)
plotly (4.14.3)
```
Version in parentheses indicate the ones used for testing the framework. Its extensively tested on Linux 16.04 but should run on all OS (Windows, Mac, Linux) supporting a Python version >3.6 and pip. It is recommended to install the framework and dependencies in a virtual environment (e.g. conda). 

## Correspondence
If you have questions, comments or inquiries, please check out the online [User documention](https://deepmreye.slite.com/api/s/channel/MUgmvViEbaATSrqt3susLZ/DeepMReye%3A%20Documentation) and reach out to us: markus.frey[at]ntnu.no and matthias.nau[at]ntnu.no