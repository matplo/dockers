# our base image
# FROM ubuntu:20.04
FROM rootproject/root:6.24.06-ubuntu20.04

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && apt-get -y install apt-utils
# RUN apt-get -y install
# this is from https://root.cern/install/dependencies/
# changed python to python3
RUN apt-get -y install dpkg-dev cmake g++ gcc binutils libx11-dev libxpm-dev libxft-dev libxext-dev python3 libssl-dev \
	gfortran libpcre3-dev xlibmesa-glu-dev libglew1.5-dev libftgl-dev libmysqlclient-dev libfftw3-dev libcfitsio-dev graphviz-dev libavahi-compat-libdnssd-dev libldap2-dev python3-dev libxml2-dev libkrb5-dev libgsl0-dev

# added by MP - failed build of boost/latest - Jan 27 2022
RUN apt-get -y install pip swig rsync curl python-is-python3 software-properties-common build-essential emacs vim nano openssh-server sudo git environment-modules

ENV LANG en_US.utf8
ENV PS1 "(o2dock)\e[32;1m[\u\e[31;1m@\h\e[32;1m]\e[34;1m\w\e[0m\n> "
ENV color_prompt yes

SHELL ["/bin/bash", "-c"]

# know the root pass
RUN echo 'root:root!' | chpasswd
WORKDIR /root
RUN mkdir -p /usr/local/bin && mkdir -p /usr/local/docker/fromhost
# COPY bash_aliases /usr/local/docker/.bash_aliases
# COPY in_docker_exec.sh /usr/local/docker/
# COPY util.sh /usr/local/docker/
# RUN chmod +x /usr/local/docker/in_docker_exec.sh

EXPOSE 22
EXPOSE 8080

ENTRYPOINT [ "/usr/local/docker/fromhost/in_docker_exec.sh" ]
