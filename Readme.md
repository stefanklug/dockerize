# Dockerize - your minimal build environment

Dockerize eases the process of working on a project inside a docker container.
Specifically it does the following steps:
 * Mounts the current directory into the container at the same path
 * Creates and uses a user with current uid:gid
 * Ensures that user has sudo permissions
 * Optionally mounts HOME into the container

# Installation

Put the dockerize file in your PATH and ensure it is executable

# Usage

```
cd <your-project>
echo "DOCKERIMAGE=ubuntu:22.04" >> .dockerize
dockerize
# Work on your project from inside an ubuntu 22.04 environment
```

# .dockerize Options

dockerize accepts the following options inside the .dockerize file

`DOCKERIMAGE` The docker image to use. Either `DOCKERIMAGE` or `DOCKERFILE` must be specified.

`DOCKERFILE` The dockerfile to use. **Warning** If you use that option you should also create 
a `.dockerignore` file to prevent that your whole projects gets sent as context to the docker 
daemon

`DOCKERIZE_MOUNT_HOME` Either 1 or 0. If this is 1, your home directory gets mounted into the 
container at the same path as on the host

`DOCKERIZE_ARGS`Additional arguments added to `docker run`. This can be handy for example to 
limit the available cpu usage in the container by specifying "--cpus=6"

