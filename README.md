# MW_algorithm_py
Python code for the retrievals of SPM and its associated uncertainties.
This module provides notebooks with functions to derived SPM and associated uncertianties from satellite imagery of remote sensing reflectance at any spectral resolution or sensor, nevertheless, default configuration is set for Sentinel-3 OLCI. This is likely not the fastest implementation possible for the MW algorithm. However, it is easy to use and handles the processing of either multispectral and hyperspectral remote sensing reflectance data.

# Setting the input data
The input to use this version of the algorithm must be satellite images of water bodies in NetCDF format (.nc) containing atmospherically corrected bands in remote sensing reflectance (rrs).

You can run the notebooks in either a local Jupyter Lab environment or on Google Colab. For a local setup, the most reliable method is to create a Conda environment using the provided environment.yml file, which installs all necessary dependencies. If using Google Colab, the notebook contains cells to install the required libraries directly. For Colab, you must also mount your Google Drive and ensure your satellite image files (.nc) are stored in a folder within your Drive to be accessible by the notebook.

To facilitate understanding of the algorithm, a sample of two Sentinel-3 OLCI satellite images with remote sensing reflectance (rrs) bands is included in the SAMPLE_DATA folder.

In sequence the inputs necessary for for the main function are the ranges of shape parameters (S and Y) and the mass-specific coefficientes (a_nap at 443 nm, a_nap at 750 nm, and b_bp at 700 nm), and the saturation threshold (Q_filter). 

This version calls temperature data from two possible data sources: the Google Earth Engine collection GCOM-C/SGLI L3 Sea Surface Temperature (V3) https://developers.google.com/earth-engine/datasets/catalog/JAXA_GCOM-C_L3_OCEAN_SST_V3 or the Copernicus DataSpace Ecosystem collection Sentinel-3 SLSTR L1B collection https://documentation.dataspace.copernicus.eu/APIs/SentinelHub/Data/S3SLSTR.html. To access these data sources, it is required to hold either a Google Earth Engine account with a cloud project, or a Copernicus Dataspace Ecosystem with OpenEO access.

The 'MW_algorithm' function will run in two steps: the first step estimating SPM and uncertaintyes and the second step constraining shape parameter and mass-specific coefficients.

This project provides two versions of the algorithm, each optimized for different hardware:

GPU Version (MW_algorithm_py_GPU.ipynb): ⚡ This version is significantly faster but requires a system with a dedicated GPU and consumes more RAM resources.

Memory Mapping Version (MW_algorithm_py.ipynb): 💾 This version uses memory mapping to conserve system resources, making it suitable for computers without a GPU. However, it takes significantly longer to process the data.

# Questions and Suggestions
For questions regarding the script implementation or to suggest changes to improve its functionality, please contact Sergio Carenas at sergio.molano@ufrgs.br
