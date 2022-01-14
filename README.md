### https://github.com/medicslaboratory/0-docker

# Docker Images for Medics Laboratory
There is 4 ubuntu18 based docker images you can use for medics laboratory

Images:

  - 'medicslaboratory/medicslab:minimal' (504 Mb) - include Python3, CMake and Minctools2
  - 'medicslaboratory/medicslab:matlab' (8.96 Gb) - include Python3, CMake, Minctools2 and MatlabRuntime2019b
  - 'medicslaboratory/medicslab:freesurfer' (11.2 Gb) - include Python3, CMake, Minctools2 and Freesurfer6.
  - 'medicslaboratory/medicslab:full' (19.6 Gb) - include Python3, CMake, Minctools2, MatlabRuntime2019b and Freesurfer6

To Use :
  ```
  docker pull medicslabratory/medicslab:<desired_version_as_tag>
  ```
  and
  ```
  docker run medicslabratory/medicslab:<desired_version_as_tag>
  ```

## more...
