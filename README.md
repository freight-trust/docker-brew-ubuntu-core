# Base Images

Core Images
  - ENV/VM/etc
  
  - Critical
  
  - Applications
  
  - Other

### Branches 
  - core
  
  - azul 
  
  - step

  - base
  - besu 

## Overview

> tl;dr: git clone --single-branch https://github.com/tianon/docker-brew-ubuntu-core.git


Scripts to prepare updates to the Ubuntu official Docker images
The process for updating the images goes like this:

Tarballs are published at https://partner-images.canonical.com/core/ by Canonical

The button is clicked by someone with appropriate permissions to run https://doi-janky.infosiftr.net/job/tianon/job/update-ubuntu/ (this job is defined by https://github.com/docker-library/oi-janky-groovy/blob/master/tianon/update-ubuntu-pipeline.groovy)

This updates each arch-* branch of https://github.com/tianon/docker-brew-ubuntu-core/ to be one commit ahead of master, that commit adding tarballs/Dockerfiles/manifests/checksums for each supported release of Ubuntu (this is why you pass --single-branch to clone to get this repo, you don’t want to be downloading all these tarballs)

generate-stackbrew-library.sh from this repo is run on a developer machine to produce a replacement for https://github.com/docker-library/official-images/blob/master/library/ubuntu

This replacement is proposed as a PR to https://github.com/docker-library/official-images

The PR is reviewed, approved and submitted by the official image maintainers (https://github.com/docker-library/official-images/blob/master/MAINTAINERS)

Some more Jenkins happens

The new images are published on https://hub.docker.com

Please feel free to open issues and discuss these images. You can submit pull requests to update the scripts and image metadata, but submitting pull requests to the arch-* branches to update the images does not work and only upsets the pig, or something like that.
