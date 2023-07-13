---
title: Docker Installation
layout: home
---
If you’ve never heard of docker before, this may help explain things for you:  [Docker introduction]

In a nut shell, Docker is a utility that enables you to use virtualization on a Linux system to install and customize your own Linux deployment.  We use it to store our deployments (called containers) as images on disk which we can use and improve on later.

We will also store our customized docker images on a remote container cloud service called Canister.io (similar to Docker.io and quay.io). Doing so will allow us to move images across machines (e.g. CSIL and laptop) so you can use them anywhere docker/podman is installed.  It also ensures that if we lose CSIL or its image repository, you can restore your snapshot from the cloud so that you don’t lose your progress.  You are responsible for backing up your images.



# Setup Steps
## 1. Setup an account on canister.io  [info]:

a. Create an account on canister.io. it is a cloud repository that will hold your private docker/podman containers when you want to save them off. Make a canister ID something that you remember, mine is ucsbckrintz and give it a password.

b. Log into [canister.io], and login using your canister ID (not username) and password

c. Under Repositories, click the gray box to Create Repo, Name it: `cs190b-bullseye`, give it a description like this: _Debian Bullseye image configured for CS190B labs._



d. Click Submit

The resulting repo in this case is called – you will use this below, replacing _ucsbckrintz_ with your repo name: `cloud.canister.io:5000/ucsbckrintz/cs190b-bullseye`

## 2. Download the image
As a start, we need to have a docker setup. We advise you to use CSIL, but you can install docker on your own laptop if you want, we will give you some helping instructions [Docker Desktop Setup]. Note that the instructional staff CANNOT help you get docker running on your personal machine.  If you cannot get it running on your personal machine, you will have to use CSIL.  All of our steps/instructions have been tested ONLY on the CSIL machines.

### (Recommended) Option 1: Docker on CSIL:
Docker on CSIL is called podman.  Podman is a docker command line interface (CLI) replacement. Docker requires root access (use of sudo) which is not allowed on many systems (including CSIL).  We therefore must use podman on CSIL.  Fortunately, podman and docker are interchangeable.  Here is how you “alias” the podman program name so that you can call it docker. Each time you ssh into CSIL, run this command to do so (or put it in your ~/.bashrc file): 

`alias docker=podman`

All of our instructions use docker instead of podman. If you’d like to use the podman CLI directly, check this [cheatsheet]

### (Not Recommended) Option 2: Docker on Desktop
If you want to install docker on your desktop, you need to follow these instructions [Docker Desktop Setup]. #TODO this is going to be a link in here

### Image download for both options    
Use the docker command line interface (CLI) to download the repo, download a container image for a Debian Linux distro (Bullseye version which the raspberry pi’s use) and configure your own version of the image using a container.  You will then save it off for future use. You start by getting the base/starting/empty image from docker.io (aka docker hub which is configured into docker by default (so we don’t have to identify it here).The bullseye string after the colon is the tag which indicates the version:

    `docker pull debian:bullseye`

Next, you will run the debian image as a Linux container (aka an instance) using a /bin/bash (aka shell) process and configure the container for use as the customized base image for CS190B labs.  These and all the configuration steps can be found at this link.  Implement all of them then return back here to finish/continue.

3. Bullseye Setup
<!-- TODO: Add this info: Latest tag is base image configured, lab2 tag is the lab2 implementation, lab3 tag is lab3, etc. -->

We will add here the bullseye setup

----
[canister.io]: https://cloud.canister.io/
[Docker introduction]: https://youtu.be/rOTqprHv1YE
[cheatsheet]: https://drive.google.com/file/d/17m50SS-L13dny4QGjZbB66c-R4tWIxLK/view?usp=share_link
[Docker Desktop Setup]: https://docs.google.com/document/d/1aBPZzcoESMWSMrxYCkA9FqNpIK0FVc4Xb5t_qDwRE-k/edit
[info]: https://ncona.com/2017/02/host-your-docker-images-for-free-with-canister-io/