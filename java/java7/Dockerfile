FROM java:7
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
RUN echo "vsoservice\nvsoservice\n\n\n\n\n\n\n" | adduser vsoservice
RUN su vsoservice
###########################################################
#  Install the agent
###########################################################
RUN mkdir /opt/vsoagent 
RUN mkdir /opt/vsoagent/_work
WORKDIR /opt/vsoagent
RUN vsoagent-installer
WORKDIR /opt/vsoagent/agent
COPY agent.config /opt/vsoagent/agent/.agent
RUN chown -R vsoservice /opt/vsoagent

###########################################################
#  Optional - install Team Explorer Everywhere 2013
#  * This is being built using Docker within a Boot2Docker
#    instance.  The path being used for the TEE files can be
#    changed to match the directory structure you wish to use.
###########################################################


#COPY tee /opt/tee
#ENV PATH $PATH:/opt/tee

USER vsoservice
ENTRYPOINT /bin/bash


