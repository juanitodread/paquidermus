This document is a compilation of the book: [Docker In Action](https://www.manning.com/books/docker-in-action-second-edition)

# Table of contents
* [Containers](#containers)
  * [Management](#management)
    * [List containers](#list-containers)
      * [List running containers](#list-running-containers)
      * [List all state containers](#list-all-state-containers)
    * [Run container](#run-container)
      * [Run in background](#run-in-background)
      * [Run interactive](#run-interactive)
    * [Create container](#create-container)
    * [Start container](#start-container)
    * [Stop container](#stop-container)
    * [Restart container](#restart-container)
    * [Remove container](#remove-container)
    * [Show container logs](#show-container-logs)
    * [Show container metadata](#show-container-metadata)
  * [Good practices](#good-practices)
    * [Building environment agnostic systems](#building-environment-agnostic-systems)
  * [Notes](#notes)
* [Help](#help)
  * [General help](#general-help)
  * [Command help](#command-help)


# Containers
## Management
### List containers
#### List running containers
`docker ps`

#### List all state containers
`docker ps -a`

### Run container
#### Run in background
`docker run --detach --name <NAME> <IMAGE-TAG>`

* `--detach` or `-d`: Starts the program in background.

#### Run interactive
`docker run --interactive --tty --link <CONTAINER-NAME>:<IMAGE> --name <NAME> <SHELL-COMMAND>`

* `--interactive` or `-i`: Keeps STDIN open for the container.
* `--tty` or `-t`: Allocates a virtual terminal for the container. Which allows you to pass commands to the container.

### Create container
`docker create <IMAGE>`

### Start container
`docker start <CONTAINER-NAME>`

### Stop container
`docker stop <CONTAINER-NAME>`

### Restart container
`docker restart <CONTAINER-NAME>`

### Remove container
`docker rm <CONTAINER-NAME>`

### Show container logs
`docker logs -f <CONTAINER-NAME>`

* `--follow` or `-f`: Continues watching and updating the log console. 

### Show container metadata
`docker inspect <CONTAINER-NAME>`

## Good practices
### Building environment agnostic systems
* Read-only filesystems (`--read-only`)
* Environment variable injection (`--env`)
* Volumes (`-v`)

## Notes
* Containers can be run with virtual terminals attached to the user's shell or in detached mode.
* Every Docker container has its own PID namespace, isolating process information for each container.
* Docker identifies every container by its container ID or its human-friendly name.
* All containers are in any one of six states: `created`, `running`, `restarting`, `paused`, `removing` or `exited`.
* The `docker exec` command can be used to run additional processes inside a running container.
* An Additional configuration can be provided to a process in a container as environment variables.
* The `--read-only` flag at container-creation time will mount the container filesystem as read-only and prevent specialization of the container.
* A container restart policy, set with the `--restart` flag at container-creation time, will help your systems automatically recover in the event of failure.
* Docker makes cleaning up containers with the `docker rm` command as simple as creating them.

# Help
## General help
`docker help`

## Command help
`docker help <COMMAND>`