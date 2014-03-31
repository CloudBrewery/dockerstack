# DockerStack

The coupler between Dockerfiles and OpenStack (sort of).

The goal of this project is to run a Dockerfile and its associated files on a
new server to pre-configure it.

Process:

 - pre-load image to take an arg on what docker repo to download
   - pre-install dockerstack on the machine
 - create the instance (indicating which to create)
 - download the docker repo
 - run dockerstack builder `python builder.py ./repo`
 - let the user rock and roll with their new thing.


Things to note:

 - docker has a mechanism to open ports. Perhaps the process needs to have the
   repos available to read in the dockerfile and export these to security
   groups.

 - environment variables might want to persist, maybe we should write to
   .profile

 - there's a notion of an on-complete script, and some docker setups use it to
   run an extra setup step. maybe we should find a way to have it run on first
   log in ?

 - as well, there's a way to make sure a command is run on every boot. we
   should find a good way to register this as well. 
