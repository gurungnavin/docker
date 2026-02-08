# Docker + Ubuntu on Windows (WSL 2) Setup Guide

This guide explains how to set up **Docker** with **Ubuntu** on Windows using **WSL 2**.  
After following this guide, you will have a fully working Linux + Docker environment.

---

# Overview
- [Install WSL 2 and Ubuntu](https://github.com/gurungnavin/docker/tree/main?tab=readme-ov-file#step-1-install-wsl-2-and-ubuntu)  
- [Install Docker Desktop on Windows](https://github.com/gurungnavin/docker/tree/main?tab=readme-ov-file#step-2--install-docker-desktop-on-windows)  
- [Verify Docker](https://github.com/gurungnavin/docker/tree/main?tab=readme-ov-file#step-3-verify-docker)  
- [Run Ubuntu container inside Docker](https://github.com/gurungnavin/docker/tree/main?tab=readme-ov-file#step-4-run-ubuntu-container-inside-docker)  
- [Manage containers](https://github.com/gurungnavin/docker/tree/main?tab=readme-ov-file#step-5-manage-containers)  
- [IMAGES VS CONTAINER : Ultra-short version:](https://github.com/gurungnavin/docker/tree/main?tab=readme-ov-file#images-vs-container--ultra-short-version)

## Step 1: Install WSL 2 and Ubuntu

1. Enable WSL 2 on Windows:
```bash
wsl --install
```
2. Install Ubuntu fom the Microsoft Store(or from web)
3. Open Ubuntu and update it.
 - Press Windows key
 - Type Ubuntu
 - A Terminal windown open - this is our Ubuntu shell. And Run the Commands below(one by one).

```bash
sudo apt update
sudo apt upgrade -y
sudo apt autoremove -y
```

## Step 2:  Install Docker Desktop on Windows
1. Download Docker Desktop: https://www.docker.com/products/docker-desktop


## Step 3: Verify Docker

- In Windows CMD or PowerShell.
```bash
docker --version
docker run hello-world
```

- In Ubuntu WSL shell:]
```bash
docker --version
docker run hello-world
```

## Step 4: Run Ubuntu container inside Docker

1. Pull and Start an Ubuntu container
```bash
docker run -it ubuntu bash
```
- We are now inside a live Ubuntu container.

2. Inside the container, we can update or install packages.
```bash
apt update
apt upgrade -y
apt install -y curl vim python3
```
3. Exit the container.
```bash
exit
```
- The container stops but still exists.

## Step 5: Manage containers
- List containers
```bash
docker ps          # running
docker ps -a       # all
```

- Restart a container
```bash
docker start -ai <container_id>
```

- Remove a container
```bash
docker rm <container_id>
```

- Remove a image
```bash
docker rmi <image_id>
```

- Downloads an image from Docker Hub (like downloading an app).
```bash
docker pull IMAGE_NAME
```

- Shows all images you have downloaded on your machine.
```bash
docker images
```

- Creates a container from the image and runs it.
```bash
docker run IMAGE_NAME
```

- Run image in interactive terminal (FIXED ❗)
```bash
docker run -it IMAGE_NAME
```

- Stop a running container
```bash
docker stop CONT_NAME or CONT_ID
```

- Start a stopped container
```bash
docker start CONT_NAME or CONT_ID
```


## IMAGES VS CONTAINER : Ultra-short version:

- Image = blueprint (template, not running)

- Container = built house (running thing made from image)

Yes — using one image, we can create many containers 👍


### What is Docker Hub
Docker Hub is an online store for Docker images.
- We download images from it
- We can upload your own images to it

example
```bash
docker pull ubuntu
docker pull node
docker pull nginx
```

Other common Docker Hub images:

- `node` → Node.js environment
- `nginx` → Web server
- `mysql` → MySQL database
- `postgres` → PostgreSQL database
- `redis` → Cache / in-memory DB
- `python` → Python environment
- `mongo` → MongoDB





----


- Downloads a specific version of a Docker image from Docker Hub (or another registry) to your local machine.

```bash
docker pull IMAGE_NAME:version
```
-  Creates and starts a container from the image in detached mode (runs in the background).
```bash
docker run -d IMAGE_NAME
```

- Creates and starts a container in the background with a custom container name, making it easier to manage (start, stop, inspect).
```bash
docker run --name CONT_NAME -d IMAGE_NAME
```
