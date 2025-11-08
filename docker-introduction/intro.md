##  DOCKER INTRODUCTION

## What is Docker?

**Docker** is an open-source platform that automates the deployment, scaling, and management of applications using **containerization** technology. It allows you to package an application and its dependencies into a standardized unit called a **container**, which can run consistently across any environment.

> Think of containers like lightweight, portable virtual machines — but faster and more efficient.

---

## Why Use Docker?

| Benefit | Description |
|-------|-----------|
| **Consistency** | "It works on my machine" → "It works everywhere" |
| **Isolation** | Each app runs in its own container, no dependency conflicts |
| **Portability** | Run the same container on dev, test, staging, or production |
| **Efficiency** | Containers share the host OS kernel → faster startup, less overhead |
| **Microservices Ready** | Perfect for building and deploying microservices |
| **Version Control** | Dockerfile = code for your environment |

---

## When to Use Docker?

Use Docker when you want to:

- Eliminate environment inconsistencies
- Simplify deployment and CI/CD pipelines
- Scale applications horizontally
- Develop microservices architectures
- Share development environments easily
- Run multiple versions of services side-by-side
- Deploy to cloud platforms (AWS, GCP, Azure, etc.)

**Avoid Docker** for:
- Applications requiring direct hardware access
- Extremely performance-sensitive workloads (sometimes)

---
## Core Docker Components

| Component                | Description |
|--------------------------|-----------|
| **Docker Engine**        | Core runtime that builds and runs containers |
| **Docker CLI**           | Command-line tool (`docker`) to interact with Docker |
| **Docker Daemon (`dockerd`)** | Background service managing images, containers, networks, volumes |
| **Dockerfile**           | Text file with instructions to build a Docker image |
| **Docker Image**         | Read-only template (like a class) |
| **Docker Container**     | Runnable instance of an image (like an object) |
| **Docker Hub / Registry**| Cloud repository for storing and sharing images |
| **Docker Compose**       | Tool for defining and running multi-container apps |

---

## Types of Docker Containers

| Type                  | Use Case |
|-----------------------|--------|
| **Application Containers** | Run web apps, APIs, workers (e.g., `nginx`, `node`) |
| **Database Containers**    | Run DBs like `postgres`, `mysql`, `mongo` |
| **Cache Containers**       | `redis`, `memcached` |
| **Message Queue**          | `rabbitmq`, `kafka` |
| **System Containers**      | Full OS-like environments (rarely used) |

---

## Common Use Cases

| Use Case               | Example |
|------------------------|--------|
| **Local Development**  | `docker run -v $(pwd):/app -p 8080:80 nginx` |
| **CI/CD Pipelines**    | Build → Test → Push image → Deploy |
| **Microservices**      | Each service in its own container |
| **Testing**            | Spin up DB, cache, app in isolated containers |
| **Production Deployment** | Kubernetes, Docker Swarm, ECS |
| **Learning/Training**  | Share identical environments with team |

---
## docker container creation

# Docker Run Options Guide

This repository provides a reference for commonly used Docker `run` command options to help you configure and manage Docker containers effectively. Below is a table of key options, their descriptions, and examples to demonstrate their usage.

## Overview

Docker is a platform for developing, shipping, and running applications inside containers. The `docker run` command is used to create and start a container from a Docker image. By using various options, you can customize the container's behavior, such as networking, resource limits, and volume mounts.

## Docker Run Options

The following table lists common `docker run` options, their descriptions, and example usage:

| Option                     | Description                                                     | Example                              |
|----------------------------|-----------------------------------------------------------------|--------------------------------------|
| `--name`                   | Assign a name to the container                                  | `--name myapp`                       |
| `-d`                       | Run in detached (background) mode                               | `-d`                                 |
| `-p`                       | Publish container port to host                                  | `-p 8080:80`                         |
| `-P`                       | Publish all exposed ports to random ports                       | `-P`                                 |
| `-v`                       | Mount a volume (bind mount)                                     | `-v /data:/app/data`                 |
| `--volume-driver`          | Specify a volume driver                                         | `--volume-driver local`              |
| `--volumes-from`           | Mount volumes from another container                            | `--volumes-from dbcontainer`         |
| `-e`                       | Set environment variables                                       | `-e ENV=production`                  |
| `--env-file`               | Load environment variables from a file                          | `--env-file .env`                    |
| `--add-host`               | Add custom host-to-IP mapping                                   | `--add-host mydb:192.168.1.10`       |
| `--dns`                    | Set custom DNS servers                                          | `--dns 8.8.8.8`                      |
| `-h`, `--hostname`         | Set container hostname                                          | `-h mycontainer`                     |
| `-w`, `--workdir`          | Set working directory inside container                          | `-w /usr/src/app`                    |
| `--entrypoint`             | Override image’s default ENTRYPOINT                             | `--entrypoint "/bin/bash"`           |
| `--restart`                | Restart policy (`no`, `on-failure`, `always`, `unless-stopped`) | `--restart=always`                   |
| `--read-only`              | Mount root filesystem as read-only                              | `--read-only`                        |
| `--privileged`             | Give extended privileges to the container                       | `--privileged`                       |
| `--cpu-shares`             | Set CPU priority (relative weight)                              | `--cpu-shares=512`                   |
| `--cpuset-cpus`            | Limit CPUs available to the container                           | `--cpuset-cpus="0,1"`                |
| `-m`, `--memory`           | Limit container memory usage                                    | `--memory=512m`                      |
| `--memory-swap`            | Set total memory + swap limit                                   | `--memory-swap=1g`                   |
| `--oom-kill-disable`       | Disable Out-Of-Memory killer                                    | `--oom-kill-disable`                 |
| `--cap-add` / `--cap-drop` | Add or remove Linux capabilities                                | `--cap-add=NET_ADMIN`                |
| `-u`, `--user`             | Run container as specific user                                  | `-u 1000:1000`                       |
| `-t`                       | Allocate a pseudo-TTY                                           | `-t`                                 |
| `-i`                       | Keep STDIN open (interactive mode)                              | `-i`                                 |
| `--attach`                 | Attach to STDIN/STDOUT/STDERR                                   | `--attach stdout`                    |
| `--log-driver`             | Specify logging driver                                          | `--log-driver=json-file`             |
| `--security-opt`           | Set security options (AppArmor, SELinux, etc.)                  | `--security-opt apparmor=unconfined` |

## Example Usage

Here’s an example of a `docker run` command that incorporates several options from the table:

```bash
docker run -d --name myapp -p 8080:80 -v /data:/app/data -e ENV=production --restart=always nginx
