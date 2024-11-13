# Overview

This project enables launching and managing a Docker-based Unifi Network Server instance on Synology's [Container Manager](https://www.synology.com/en-global/dsm/packages/ContainerManager). The Docker Compose file (`compose.yaml`) will create two containers, one for the Unifi Network Server and one for MongoDB. The Mongo instance uses the initialization script (`init-mongo.js`) to create the credentials used by Unifi. 

# Install

1. Customize the `compose.yaml` and `init-mongo.js` files. Specifically:
  - All files will be placed in this volume/folder: `/volume1/docker`. Update the file path in all locations if you have a different requirement.
  - Update the time zone to match your location. Default is `TZ=America/New_York`.
  - Update the password you want to use in `compose.yaml` in the setting `MONGO_PASS=` and in `init-mongo.js` on both lines.
1. In Synology's Container Manager application, go to **Project** and click **Create**. Recomended settings:
  - Project name: **unifi**
  - Path: **/volume1/docker/unifi-network-server**
  - Source: Upload the `compose.yaml` in this repository, once you've finished customizations.

# Reference

These are the containers that will launch:
* https://github.com/linuxserver/docker-unifi-network-application
* https://hub.docker.com/_/mongo/