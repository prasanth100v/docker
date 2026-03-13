# 🐳 Docker Fundamentals Guide

```{=html}
<p align="center">
```
`<img src="https://www.docker.com/wp-content/uploads/2022/03/Moby-logo.png" width="120"/>`{=html}
```{=html}
</p>
```
```{=html}
<p align="center">
```
`<img src="https://img.shields.io/badge/Container-Docker-blue?logo=docker">`{=html}
`<img src="https://img.shields.io/badge/Orchestration-Kubernetes-blueviolet?logo=kubernetes">`{=html}
`<img src="https://img.shields.io/badge/Platform-Linux%20%7C%20Windows%20%7C%20macOS-success">`{=html}
`<img src="https://img.shields.io/badge/DevOps-Tool-important">`{=html}
```{=html}
</p>
```

------------------------------------------------------------------------

# 📚 Table of Contents

-   [What is Docker](#-what-is-docker)
-   [Why Use Docker](#-why-use-docker)
-   [Docker Image](#-docker-image)
-   [Docker Container](#-docker-container)
-   [Dockerfile](#-dockerfile)
-   [Docker Compose](#-docker-compose)
-   [Docker Hub](#-docker-hub)
-   [Container Orchestration](#-container-orchestration)
-   [Summary](#-summary)

------------------------------------------------------------------------

# ✅ What is Docker?

**Docker** is a **containerization platform** that allows developers to
package applications and their dependencies into **lightweight, portable
containers**.

A Docker container includes:

-   Application code
-   Runtime environment
-   Libraries
-   System dependencies
-   Configuration files

This ensures applications run **consistently across different
environments** such as:

-   💻 Developer laptops
-   🧪 Testing environments
-   ☁️ Cloud platforms
-   🚀 Production servers

------------------------------------------------------------------------

# 🚀 Why Use Docker?

  -----------------------------------------------------------------------
  Feature                Description
  ---------------------- ------------------------------------------------
  ⚙️ **Consistency**     Same behavior across development, testing, and
                         production

  🔒 **Isolation**       Each application runs in its own container

  🌍 **Portability**     Works across Linux, Windows, macOS and cloud

  ⚡ **Efficiency**      Containers are lightweight compared to virtual
                         machines

  📈 **Scalability**     Easy scaling with Kubernetes or Docker Swarm
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 📦 Docker Image

A **Docker Image** is a **read‑only template** used to create
containers.

It contains:

-   Application code
-   Dependencies
-   Runtime
-   Environment configuration

### Key Characteristics

✔ Built in **layers**\
✔ Created using a **Dockerfile**\
✔ Stored in **registries like Docker Hub**\
✔ When executed → becomes a **container**

------------------------------------------------------------------------

# 📦 Docker Container

A **Docker Container** is a running instance of a Docker Image.

### Characteristics

-   Lightweight
-   Isolated
-   Fast startup
-   Portable

Containers are widely used in **microservices architecture** because
they make:

-   Deployment easier
-   Scaling faster
-   Environment consistency guaranteed

------------------------------------------------------------------------

# 🧾 Dockerfile

A **Dockerfile** is a script that defines how to build a Docker image.

It includes:

-   Base Image
-   Application code
-   Dependencies
-   Environment variables
-   Commands executed during build

### Example Dockerfile

``` dockerfile
FROM node:18

WORKDIR /app

COPY . .

RUN npm install

CMD ["npm", "start"]
```

------------------------------------------------------------------------

# ⚙️ Docker Compose

**Docker Compose** allows you to run **multiple containers using one
configuration file**.

Configuration file:

    docker-compose.yml

### Example

``` yaml
version: "3"

services:
  web:
    image: nginx
    ports:
      - "80:80"

  redis:
    image: redis
```

### Advantages

-   Run multi‑container applications
-   Simple environment setup
-   Start everything with one command

```{=html}
<!-- -->
```
    docker compose up

------------------------------------------------------------------------

# ☁️ Docker Hub

**Docker Hub** is a **cloud repository for Docker images**.

You can:

-   Upload images
-   Share images
-   Download public images

### Example

``` bash
docker pull nginx
```

Official images available:

-   nginx
-   redis
-   mysql
-   node
-   python

------------------------------------------------------------------------

# 🔗 Container Orchestration

## 🐳 Docker Swarm

Docker's **native orchestration tool** used for:

-   Clustering containers
-   Load balancing
-   Service scaling

------------------------------------------------------------------------

## ☸️ Kubernetes (K8s)

**Kubernetes** is the most powerful container orchestration platform.

Features include:

-   Auto scaling
-   Self healing
-   Rolling updates
-   Load balancing

Used by companies like:

-   Google
-   Netflix
-   Spotify
-   Airbnb

------------------------------------------------------------------------

# 🎯 Summary

Docker simplifies application deployment by packaging everything into
containers.

### Core Components

  Component          Purpose
  ------------------ -------------------------------
  Docker             Container platform
  Docker Image       Template to create containers
  Docker Container   Running instance of an image
  Dockerfile         Instructions to build images
  Docker Compose     Run multi‑container apps
  Docker Hub         Image registry
  Docker Swarm       Native orchestration
  Kubernetes         Advanced orchestration

------------------------------------------------------------------------

# ⭐ Final Thought

Docker enables:

-   Faster development
-   Reliable deployments
-   Scalable cloud‑native applications

🚀 **Master Docker to become a strong DevOps Engineer.**
