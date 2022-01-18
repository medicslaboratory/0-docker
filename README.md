### https://github.com/medicslaboratory/0-docker [last update 2022-01-17]

# Docker Images for Medics Laboratory
There is 4 ubuntu18 based docker images you can use for medics laboratory

Images:

  - 'medicslaboratory/medicslab:minimal' (964 Mb) - include **Python3.8**, **CMake3.10** and **Minctools2.3**
  - 'medicslaboratory/medicslab:matlab' (8.96 Gb) - include **Python3.8**, **CMake3.10**, **Minctools2.3** and **MatlabRuntime2019b**
  - 'medicslaboratory/medicslab:freesurfer' (11.2 Gb) - include **Python3.8**, **CMake3.10**, **Minctools2.3** and **Freesurfer6**.
  - 'medicslaboratory/medicslab:full' (19.6 Gb) - include **Python3.8**, **CMake3.10**, **Minctools2.3**, **MatlabRuntime2019b** and **Freesurfer6**

To Use:

  Getting the docker image container to your computer:
  ```  
  docker pull medicslabratory/medicslab:<desired_version_as_tag>  
  ```
  and running the container:
  ```  
  docker run medicslabratory/medicslab:<desired_version_as_tag>  
  ```
<!-- Tip: [If you don’t want to preface the docker command with sudo](https://docs.docker.com/engine/install/linux-postinstall/). -->
---------------------------
#### [*Content of this page*]
1. Basic example use
2. Using matlab runtime
3. Using Freesurfer
4. Getting inside the container with command line interface (CLI)
5. Making the container your own for further development

----------------------


## 1. Basic example use (with all 4 images):
**IMPORTANT**: To use your local files inside the docker image, you must use the 'docker run' option VOLUME (-v) (shared filesystems). You can use multiple shared filesystems. https://docs.docker.com/storage/volumes/

Note that the 'user' folder inside the docker images is '/root/' with the usual user's folders you can use; Documents, Downloads, Pictures, Public, Templates and Videos.
```
docker run -v '/absolute_path_to_your_Documents_folder_as_example/Documents':'/root/Documents' medicslaboratory/medicslab:minimal mincinfo '/root/Documents/more_path_now_shared_with_container/t1w.mnc' 
```
Now the containt of your local folder 'Documents' is mounted inside the container in '/root/Documents'. In the example, we used the Minctools command 'mincinfo' on a local minc image, now "inside" the container. 


## 2. Using matlab runtime (with images tagged as :matlab or :full):

testing


## 3. Using Freesurfer (with images tagged as :freesurfer or :full):

The Freesurfer subjects folder inside the containers is: SUBJECTS_DIR=/usr/local/freesurfer/subjects. You will have to shared filesystems (-v) consequently.

```
testing
```

## 4. Getting inside the container with command line interface (CLI) (with all 4 images):
*Warning: All modifications inside the docker image will be lost after you exit the container. See [docker commit](https://docs.docker.com/engine/reference/commandline/commit/) to work around this.*

To enter inside the container image, use 'docker run' in this form:
```
docker run -it medicslabratory/medicslab:<desired_version_as_tag> /bin/bash
```

## 5. Making the container your own for further development (with all 4 images):
Simply start your dockerfile with:
```
FROM medicslabratory/medicslab:<desired_version_as_tag>
```

--------------------
<!-- louis.dieumegarde@cervo.ulaval.ca -->
