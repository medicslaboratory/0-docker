### https://github.com/medicslaboratory/0-docker

# Docker Images for Medics Laboratory
There is 4 ubuntu18 based docker images you can use for medics laboratory

Images:

  - 'medicslaboratory/medicslab:minimal' (504 Mb) - include Python3, CMake and Minctools2
  - 'medicslaboratory/medicslab:matlab' (8.96 Gb) - include Python3, CMake, Minctools2 and MatlabRuntime2019b
  - 'medicslaboratory/medicslab:freesurfer' (11.2 Gb) - include Python3, CMake, Minctools2 and Freesurfer6.
  - 'medicslaboratory/medicslab:full' (19.6 Gb) - include Python3, CMake, Minctools2, MatlabRuntime2019b and Freesurfer6

To Use :

  Getting the docker image container to your computer :
  ```  
  docker pull medicslabratory/medicslab:<desired_version_as_tag>  
  ```
  and running the container :
  ```  
  docker run medicslabratory/medicslab:<desired_version_as_tag>  
  ```
Tip : [If you don’t want to preface the docker command with sudo](https://docs.docker.com/engine/install/linux-postinstall/).

[Content of this page]
1. Basic example use
2. Using matlab runtime
3. Using Freesurfer
4. Getting inside the container with command line interface (CLI)
5. Making the container your own for further development

----------------------

##1. Example use of 'medicslaboratory/medicslab:minimal' (504 Mb) :


