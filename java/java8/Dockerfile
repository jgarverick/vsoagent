FROM java:8
MAINTAINER Josh Garverick <josh.garverick@gmail.com>

###########################################################
#  Set up backports for wheezy, leads to node.js install
###########################################################

RUN echo "deb http://ftp.us.debian.org/debian wheezy-backports main" >> /etc/apt/sources.list
RUN apt-get update
RUN apt-get install -y nodejs-legacy git cmake
RUN curl -L --insecure https://www.npmjs.org/install.sh | bash

###########################################################
#  Install node.js and npm dependencies (grunt, bower, vsoagent-installer)
#  and some additional nice-to-haves (jake, yeoman, gulp)
###########################################################

RUN npm install -g vsoagent-installer grunt bower grunt-cli jake yo gulp grunt-cli


###########################################################
#  Create a service user as root access throws an error
###########################################################
RUN adduser --disabled-password vsoservice
RUN echo "vsoservice:vsoservice" | chpasswd
RUN su vsoservice
###########################################################
#  Install the agent
###########################################################
RUN /usr/bin/vsoagent-installer
WORKDIR /opt/vsoagent/agent

###########################################################
#  Optional - install Team Explorer Everywhere 2013
#  * This is being built using Docker within a Boot2Docker
#    instance.  The path being used for the TEE files can be
#    changed to match the directory structure you wish to use.
###########################################################

# RUN mkdir /opt/vsoagent 
# WORKDIR /opt/vsoagent
#COPY tee /opt/tee
#ENV PATH $PATH:/opt/tee
RUN node config
ENTRYPOINT node host
