### https://github.com/medicslaboratory/0-docker [last update 2022-09-21]

# Docker Images for Medics Laboratory
There is 3 ubuntu based docker images provided by the medics laboratory

Images:

  - 'medicslaboratory/medicslab:minimal' (2 Gb) - include **Python3.8** and **CMake3.10**
  - 'medicslaboratory/medicslab:minc' (3 Gb) - include **Python3.8**, **CMake3.10** and **Minctools2.3**
  - 'medicslaboratory/medicslab:freesurfer' (7 Gb) - include **Python3.8**, **CMake3.10**, **Minctools2.3** and **Freesurfer6**.

To Use (Using a terminal or a command windows:

  Getting the docker image container to your computer:
  ```  
  docker pull medicslaboratory/medicslab:<desired_version_as_tag>  
  ```
  and running the container:
  ```  
  docker run medicslaboratory/medicslab:<desired_version_as_tag> --help 
  ```
<!-- Tip: [If you don’t want to preface the docker command with sudo](https://docs.docker.com/engine/install/linux-postinstall/). -->
---------------------------
#### [*Content of this page*]
1. Basic example use
2. Using Freesurfer
3. Getting inside the container with command line interface (CLI)

----------------------


## 1. Basic example use :
**IMPORTANT**: To use your local files inside the docker image, you must use the 'docker run' option VOLUME (-v) (shared filesystems). You can use multiple shared filesystems. https://docs.docker.com/storage/volumes/

Note that the 'user' folder inside the docker images is '/root/' with the usual user's folders you can use; Documents, Downloads, Pictures, Public, Templates and Videos.

Example 1:
```
docker run -v '/absolute_path_to_your_User_folder/Documents':'/root/Documents' medicslaboratory/medicslab:minimal python /root/Documents/MyPythonScript.py' 
```
Now the contents of your local folder 'Documents' is mounted inside the container in '/root/Documents'. In this example, we run a Python script that is inside your Documents folder on your local computer. Note that if you use other files or folders inside your Python script, the paths should reflect that you are inside the docker container (ex.: df = pandas.read_csv('/root/Documents/MyCSV.csv') ). 

Example 2:
```
docker run -v '/absolute_path_to_your_User_folder/Documents':'/root/Documents' medicslaboratory/medicslab:minc mincinfo '/root/Documents/t1w.mnc' 
```
Now the contents of your local folder 'Documents' is mounted inside the container in '/root/Documents'. In this example, we used the Minctools command 'mincinfo' on a local minc image, now accessible "inside" the container. 

## 2. Using Freesurfer (with image tagged as :freesurfer):
See [Freesurfer Input](https://surfer.nmr.mgh.harvard.edu/fswiki/ReconAllOutputFiles#A001.mgz) on how to organize your data for Freesurfer analyses.

The Freesurfer subjects folder inside the containers is: SUBJECTS_DIR=/root/FS_subjects. You will have to shared your local filesystems (-v) accordingly.

```
docker run -v '/absolute_path_to_your_local_SUBJECTS_DIR_equivalent':'/root/FS_subjects' medicslaboratory/medicslab:freesurfer recon-all -all -s <your_subject_folder>
```
This will output the Freesurfer analyse results in '/absolute_path_to_your_local_SUBJECTS_DIR_equivalent'/<your_subject_folder>

## 3. Getting inside the container with command line interface (CLI):
*Warning: All modifications inside the docker image will be lost after you exit the container. See [docker commit](https://docs.docker.com/engine/reference/commandline/commit/) to work around this.*

To enter inside the container image, use 'docker run' in this form:
```
docker run -it medicslaboratory/medicslab:<desired_version_as_tag> /bin/bash
```


--------------------
<!-- louis.dieumegarde@cervo.ulaval.ca -->
