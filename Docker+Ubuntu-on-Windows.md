# Docker + Ubuntu on Windows (WSL 2) Setup Guide

This guide explains how to set up **Docker** with **Ubuntu** on Windows using **WSL 2**.  
After following this guide, you will have a fully working Linux + Docker environment.

---

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