FROM ubuntu:latest

MAINTAINER Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>

# Install Utilities
RUN apt-get update -y --fix-missing
RUN apt-get install -y vim nano git cron openssl zip curl wget apt-utils

# Install NodeJS and NPM
RUN curl -sL https://deb.nodesource.com/setup_8.x -o nodesource_setup.sh && bash nodesource_setup.sh
RUN apt-get update -y
RUN apt-get install -y nodejs build-essential 

# Check the current version of NodeJS and NPM
RUN nodejs -v
RUN npm -v

# Install Ionic CLI and Cordova
RUN npm install -g ionic cordova