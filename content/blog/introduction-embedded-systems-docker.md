---
title: "Introduction to Embedded Systems with Docker"
date: 2024-04-30
draft: false
categories:
    - embedded
---

Hi everyone joining the course [Introduction to Embedded Systems Software and Development Environments](https://www.coursera.org/learn/introduction-embedded-systems/home/welcome) on Coursera. I found that installing VirtualBox according to the [suggestion](https://www.coursera.org/learn/introduction-embedded-systems/resources/jDf20) required downloading a large file and setting up the environment. Instead, I am sharing the steps to set up the environment for the course using Docker.

## Step 1: Install Docker
Get [Docker Desktop](https://docs.docker.com/desktop/)

## Step 2: Pull and run the Docker image
```
$ docker run -d  ubuntu:22.04 sleep 8640000
```

## Step 3: Access the Docker containe
```
$ docker container ls
```
You will see the container ID and the name of the container. Use the container ID to access the container.

| CONTAINER ID | IMAGE       | COMMAND         | CREATED       | STATUS      | PORTS | NAMES                 |
|--------------|-------------|-----------------|---------------|-------------|-------|-----------------------|
| 6ec4514d27ee | ubuntu:22.04| "sleep 864000"  | 16 hours ago  | Up 16 hours |       | wizardly_nightingale  |

```
docker exec -it wizardly_nightingale /bin/bash
```

## Step 4: Install the required packages
Now you are inside the container. Install the required packages.
```
$ apt install build-essential unzip gcc-arm-none-eabi
```

You are all set to start the course. Enjoy learning!
