## ewsdocker/debian-eclipse-cpp  

**Eclipse IDE for C++ Development Tools (CDT) in a Debian-based Docker image.**  

Now with support branches for **Eclipse IDE Photon** and **Eclipse IDE Oxygen** versions.

____  

**A Docker pre-built image is available from [ewsdocker/debian-eclipse-cpp](https://hub.docker.com/r/ewsdocker/debian-eclipse-cpp).**  

____  

**NOTE**  
**ewsdocker/debian-eclipse-cpp** is designed to be used on a Linux system configured to support **Docker user namespaces** .  Refer to [ewsdocker Containers and Docker User Namespaces](https://github.com/ewsdocker/ewsdocker.github.io/wiki/UserNS-Overview) for an overview and information on running **ewsdocker/debian-eclipse-cpp** on a system not configured for **Docker user namespaces**.
____  

**Visit the [ewsdocker/debian-eclipse-cpp Wiki](https://github.com/ewsdocker/debian-eclipse-cpp/wiki/QuickStart) for complete documentation of this docker image.**  

____  

**Installing ewsdocker/debian-eclipse-cpp**  

The following scripts will download the the selected **ewsdocker/debian-eclipse-cpp** image, create a container, setup and populate the directory structures, create the run-time scripts, and install the application's desktop file(s).  

The _default_ values will install all directories and contents in the **docker host** user's home directory (refer to [Mapping docker host resources to the docker container](https://github.com/ewsdocker/debian-eclipse-cpp/wiki/QuickStart#mapping)),  

**ewsdocker/debian-eclipse-cpp:photon-9.5.0**  
  
    docker run --rm \
               -v ${HOME}/bin:/userbin \
               -v ${HOME}/.local:/usrlocal \
               -e LMS_BASE="${HOME}/.local" \
               -v ${HOME}/.config/docker:/conf \
               -v ${HOME}/.config/docker/debian-eclipse-cpp-photon-9.5.0:/root \
               --name=debian-eclipse-cpp-photon-9.5.0 \
           ewsdocker/debian-eclipse-cpp:photon-9.5.0 lms-setup  

____  
  
**ewsdocker/debian-eclipse-cpp:oxygen-9.5.0**  
  
    docker run --rm \
               -v ${HOME}/bin:/userbin \
               -v ${HOME}/.local:/usrlocal \
               -e LMS_BASE="${HOME}/.local" \
               -v ${HOME}/.config/docker:/conf \
               -v ${HOME}/.config/docker/debian-eclipse-cpp-oxygen-9.5.0:/root \
               --name=debian-eclipse-cpp-oxygen-9.5.0 \
           ewsdocker/debian-eclipse-cpp:oxygen-9.5.0 lms-setup  

____  

Refer to [Mapping docker host resources to the docker container](https://github.com/ewsdocker/debian-eclipse-cpp/wiki/QuickStart#mapping) for a discussion of **lms-setup** and what it does.  

____  

**Running the installed scripts**

After running the above command script, and using the settings indicated, the docker host directories, mapped as shown in the above tables, will be configured as follows:

+ the executable scripts have been copied to **~/bin**;  
+ the application desktop file(s) have been copied to **~/.local/share/applications**, and are availablie in any _task bar_ menu;  
+ the associated **debian-eclipse-cpp-"branch"-"version"** executable script (shown below) will be found in **~/.local/bin**, and _should_ be customized with proper local volume names;  

____  

**Executable scripts**  

**ewsdocker/debian-eclipse-cpp:photon-9.5.0**
  
    docker run -e DISPLAY=unix${DISPLAY} \
               -v /tmp/.X11-unix:/tmp/.X11-unix \
               -v ${HOME}/.Xauthority:${HOME}/.Xauthority \
               -v /etc/localtime:/etc/localtime:ro \
               -v ${HOME}/source:/source \
               -v ${HOME}/workspace:/workspace \
               -v ${HOME}/git/ewsdocker:/project \
               -v ${HOME}/.config/docker/debian-eclipse-cpp-photon-9.5.0:/root \
               --name=debian-eclipse-cpp-photon-9.5.0 \
          ewsdocker/debian-eclipse-cpp:photon-9.5.0  

**ewsdocker/debian-eclipse-cpp:oxygen-9.5.0**
  
    docker run -e DISPLAY=unix${DISPLAY} \
               -v /tmp/.X11-unix:/tmp/.X11-unix \
               -v ${HOME}/.Xauthority:${HOME}/.Xauthority \
               -v /etc/localtime:/etc/localtime:ro \
               -v ${HOME}/source:/source \
               -v ${HOME}/workspace:/workspace \
               -v ${HOME}/git/ewsdocker:/project \
               -v ${HOME}/.config/docker/debian-eclipse-cpp-oxygen-9.5.0:/root \
               --name=debian-eclipse-cpp-oxygen-9.5.0 \
           ewsdocker/debian-eclipse-cpp:oxygen-9.5.0  

____  
Refer to [Mapping docker host resources to the docker container](https://github.com/ewsdocker/debian-eclipse-cpp/wiki/QuickStart#mapping) for a discussion of customizing the executable scripts..  

____  

**Regarding photon-edge and oxygen-edge**  

For the very brave, if an _edge_ tag is available, these instructions will download, rename and install the _edge_ version.  Good luck.  

**ewsdocker/debian-eclipse-cpp:photon-edge**  

**photon-edge** is the development tag for the **9.5.1** release tag.

    docker pull ewsdocker/debian-eclipse-cpp:photon-edge
    docker tag ewsdocker/debian-eclipse-cpp:photon-edge ewsdocker/debian-eclipse-cpp:photon-9.5.1
    docker run --rm \
               -v ${HOME}/bin:/userbin \
               -v ${HOME}/.local:/usrlocal \
               -e LMS_BASE="${HOME}/.local" \
               -v ${HOME}/.config/docker:/conf \
               -v ${HOME}/.config/docker/debian-eclipse-cpp-photon-9.5.1:/root \
               --name=debian-eclipse-cpp-photon-9.5.1 \
           ewsdocker/debian-eclipse-cpp:photon-9.5.1 lms-setup  

optional step:

    docker rmi ewsdocker/debian-eclipse-cpp:photon-edge  

To create and run the container, run **Eclipse CDT photon-9.5.1** from the _Programming_ category of any desktop menu, or from the command-line, the following should work:

    ~/.local/bin/docker-deb-start-0.0.2 debian-eclipse-cpp:photon-9.5.1  

____  

**ewsdocker/debian-eclipse-cpp:oxygen-edge**  

**oxygen-edge** is the development tag for the **9.5.1** release tag.

    docker pull ewsdocker/debian-eclipse-cpp:oxygen-edge
    docker tag ewsdocker/debian-eclipse-cpp:oxygen-edge ewsdocker/debian-eclipse-cpp:oxygen-9.5.1
    docker run --rm \
               -v ${HOME}/bin:/userbin \
               -v ${HOME}/.local:/usrlocal \
               -e LMS_BASE="${HOME}/.local" \
               -v ${HOME}/.config/docker:/conf \
               -v ${HOME}/.config/docker/debian-eclipse-cpp-oxygen-9.5.1:/root \
               --name=debian-eclipse-cpp-oxygen-9.5.1 \
           ewsdocker/debian-eclipse-cpp:oxygen-9.5.1 lms-setup  


optional step:

    docker rmi ewsdocker/debian-eclipse-cpp:oxygen-edge  
  

To create and run the container, run **Eclipse CDT oxygen-9.5.1** from the _Programming_ category of any desktop menu, or from the command-line, the following should work:

    ~/.local/bin/docker-deb-start-0.0.2 debian-eclipse-cpp:oxygen-9.5.1  

____  

**Persistence**  
In order to persist the Eclipse application state, a location on the docker _host_ must be provided to store the necessary information.  This can be accomplished with the following volume option in the run command:

    -v ${HOME}/.config/docker/debian-eclipse-cpp-"branch"-"version":/root  

Since the information is stored in the docker _container_ **/root** directory, this statement maps the user's **~/.config/docker/debian-eclipse-cpp-"branch"-"version"** docker _host_ directory to the **/root** directory in the docker _container_.  
____  
**Timestamps**  
It is important to keep the time and date on docker _host_ files that have been created and/or modified by the docker _containter_ synchronized with the docker _host_'s settings. This can be accomplished as follows:

    -v /etc/localtime:/etc/localtime:ro  

____  
**About the X11 Server / GUI Stack**  
The **ewsdocker/debian-eclipse-cpp** image is built on the [ewsdocker/debian-openjre](https://github.com/ewsdocker/debian-openjre/wiki) docker image, which is built on the [ewsdocker/debian-base-gui](https://github.com/ewsdocker/debian-base-gui/wiki) docker image. These two docker images provide the **X11-Server** stack and several **GUI** system elements.  The **X11-Server** stack is configured in the _docker run_ command as follows:

    docker run -e DISPLAY=unix${DISPLAY} \
               -v /tmp/.X11-unix:/tmp/.X11-unix \
               -v ${HOME}/.Xauthority:${HOME}/.Xauthority \

Since these options are _the same for all gui containers_, they should probably be the first options in the docker run command.  

____  

**Copyright © 2018. EarthWalk Software.**  
**Licensed under the GNU General Public License, GPL-3.0-or-later.**  

This file is part of **ewsdocker/debian-eclipse-cpp**.  

**ewsdocker/debian-eclipse-cpp** is free software: you can redistribute 
it and/or modify it under the terms of the GNU General Public License 
as published by the Free Software Foundation, either version 3 of the 
License, or (at your option) any later version.  

**ewsdocker/debian-eclipse-cpp** is distributed in the hope that it will 
be useful, but WITHOUT ANY WARRANTY; without even the implied warranty 
of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.  

You should have received a copy of the GNU General Public License
along with **ewsdocker/debian-eclipse-cpp**.  If not, see 
<http://www.gnu.org/licenses/>.  

