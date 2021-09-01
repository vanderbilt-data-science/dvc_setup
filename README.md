# DVC Setup

This repository acts as a tutorial for using data versioning and storage with dvc and GitHub repositories. 

# Installation Steps

1. Install dvc locally. There are multiple ways to install dvc: 
 
  * Install with Homebrew (Recommended for MacOS): run the following code in the command line: ```brew install dvc```
  * Install with pip: run the following code in the command line: ```pip install "dvc[s3/gdrive/azure/gs/etc.]"```
  * Install with Conda: run the following two lines of code in the command line: ```conda install -c conda-forge mamba```, ```mamba install -c conda-forge dvc-s3/gdrive/azure/gs/etc.```

2. Create the project git repository and clone it locally
3. In the command line, change directory (```cd```) to the git repository and run the following command: ```dvc init```
5. Run the following command: ```git commit -m "Initialize DVC"```
6. Add the data to a folder named "data" in the locally cloned repository
7. To track the data directory, run the following command: ```dvc add data```
   The information of the added file or directory will be stored in .dvc file nameddata.dvc . This is a small text file that stores information on how to access the original data but not the original data itself.
9. 
