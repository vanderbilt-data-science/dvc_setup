# DVC Setup

This repository acts as a tutorial for using data versioning and storage with dvc and GitHub repositories. 

# Installation Steps

1. Install dvc locally. There are multiple ways to install dvc: 
 
  * Install with Homebrew (Recommended for MacOS): run the following code in the command line: ```brew install dvc```
  * Install with pip: run the following code in the command line: ```pip install "dvc[s3/gdrive/azure/gs/etc.]"```
  * Install with Conda: run the following two lines of code in the command line: ```conda install -c conda-forge mamba; mamba install -c conda-forge dvc-s3/gdrive/azure/gs/etc.```

2. Create the project git repository and clone it locally
3. In the command line, change directory (```cd```) to the git repository and run the following command: ```dvc init```
5. Run the following command: ```git commit -m "Initialize DVC"```
6. Add the data to a folder named "data" in the locally cloned repository
7. To track the data directory, run the following command: ```dvc add data```
   The information of the added file or directory will be stored in a .dvc file named data.dvc . This is a small text file that stores information on how to access the original data but not the original data itself.
9. Make sure to add data to .gitignore beforehand to avoid committing the data. Add the line "data/" to the .gitignore file in the repository. 
10. Now simply commit the dvc file as you would with source code using the following two commands: ```git add data.dvc```, ```git commit -m "add data"```

Now, let's store the data remotely. For the purposes of this tutorial, we will set up the remote data storage with Google Drive. 

11. Create a folder on Google Drive where the data will be stored. Copy the unique URL code to this folder. The URL will look something like ```https://drive.google.com/drive/folders/1ynNBbT-4J0ida0eKYQqZZbC93juUUbVH```. Copy only the code at the end of the URL. 
12. Simply add that link to DVC to store the location of the remote storage. Run the following code in the command line: ```dvc remote add -d remote gdrive://1ynNBbT-4J0ida0eKYQqZZbC93juUUbVH```
13. Now simply commit the config file: ```git commit .dvc/config -m "Configure remote storage"```
14. Now push the file to github: ```dvc push```
15. That’s it! Now all of the data is pushed to Google Drive. Now push the changes to the remote repository: ```git push origin <branch>```
16. To retrieve the data, simply type ```dvc pull```
17. To make changes, use the following commands: 
  * ```dvc add data```
  * ```git add data.dvc```
  * ```git commit data.dvc -m 'Data updates'```
  * ```dvc push```
  * ```git push origin <branch>```

To pull data in if cloning a repository with dvc already set up, follow the steps below:

1. In command line, change directory to the repository, then run the following command ```dvc pull```
2. You will be asked to copy a link. This will take you to an authentication page. Log in with the Google account associated with the data directory you have access to and give all permissions. 
3. Paste the verification code provided after authentication into the command line
4. You now have the data downloaded locally in the ```data``` folder. 
