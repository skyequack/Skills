# Docker for RoboGPT

This repository contains a `Dockerfile` and a shell script to build and run RoboGPT locally inside a Docker container. It is intended strictly for development use.

## Clone the Repository

It is recommended to clone this repository in your `HOME` directory.

```bash
git clone git@github.com:orangewood-co/robogpt_image.git
```

If you have already cloned the repository, you can update it with:

```bash
cd ~/robogpt_image

git checkout v0.1-dev
git pull  # Fetch the latest updates
cd setup
./setup.sh
```

## Manual Build Method

### Method 1: Using the Build Script

```bash
cd ~/robogpt_image/build
./build_app_image.sh
```

You will be prompted to choose:

- `0` for a cached build (faster, but may skip new dependencies)
- `1` for a non-cached build (recommended if there are new dependencies)

The build process may take 10–20 minutes.

## Running the Software

Once the image is built, run the container using:

```bash
robogpt dev
```

This command starts the RoboGPT container and opens an interactive terminal session. You can now run RoboGPT bringup commands inside the container.

### Accessing the Web Application

To access the RoboGPT web app, go to:

```
https://robogpt.orangewood.co/chat
```

If you do not already have access, please contact the Orangewood Labs team to request an invitation.

### To run agent stack:

```Shell
roslaunch robogpt_agents agent_bringup.launch robot_name:=sim use_case:=base
```

default robot_name is sim and use_case is set to base
base contains all the basic skills like move to pose, save pose, connect robot

Note: On the webapp, ensure that the execute switch in the bottom right corner is toggled 'on'.
## Opening Additional Terminals in the Same Container

To open another terminal instance in the same running container, run:

```bash
docker exec -it robogpt_app /bin/bash
```

Note: If the container is not named `robogpt_app`, use `docker ps` to find the correct container name or ID.


## Checking Container and Image Status

List all containers (running and stopped):

```bash
docker ps -a
```

List all available Docker images:

```bash
docker images --all
```

## Stopping and Removing Containers and Images

Stop all running containers:

```bash
docker stop $(docker ps -q)
```

If no containers are running, you can use this safe alternative:

```bash
docker ps -q | xargs -r docker stop
```

Remove all stopped containers:

```bash
docker rm $(docker ps -aq)
```

Remove all Docker images:

```bash
docker rmi $(docker images -q)
```

Remove all Docker data, including volumes (use with caution):

```bash
docker system prune -a --volumes
```

## Saving Changes to a New Image

To save the current state of a running container as a new image:

```bash
docker commit <container-id> <new-image-name>:<tag>
```

Example:

```bash
docker commit 123abc robogpt_app:custom
```

This will create a new image with your changes saved.