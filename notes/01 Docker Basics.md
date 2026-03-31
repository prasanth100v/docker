# 🐳 Docker Basics 
## ✅ 1. What is Docker?

**Docker** is a **containerization platform** that helps you package
applications and their dependencies into **lightweight and portable
containers**.

Inside a container, everything required to run the application is
included:

-   Application code
-   Runtime
-   Libraries
-   System dependencies
-   Configuration files

This ensures the application runs **the same everywhere** --- whether on
a developer laptop, testing environment, or production server.

## 🚀 Why Use Docker?
| 🧩 Feature     | 💡 Description                                                  |
| -------------- | --------------------------------------------------------------- |
| 🔁 Consistency | 📦 Works the same across dev, test, and production environments |
| 🧱 Isolation   | 🛡️ Apps run in separate containers → no conflicts              |
| 🌍 Portability | 💻 Runs anywhere (Linux, Windows, macOS, cloud)                 |
| ⚡ Efficiency   | 🚀 Lightweight vs VMs (faster startup, less overhead)           |
| 📈 Scalability | 🔄 Easily scale using Kubernetes or Docker Swarm                |


------------------------------------------------------------------------

## 📦 Docker Image
A **Docker Image** is a **read-only template** used to create containers.

It includes:
-   Application code
-   Dependencies
-   Configuration
-   Runtime environment

### Key Points
-   Images are built in **layers**
-   Each layer comes from instructions in a **Dockerfile**
-   Images are stored in **Docker registries** like **Docker Hub**
-   When an image runs → it becomes a **container**

------------------------------------------------------------------------

## 📦 Docker Container
  * A **Docker Container** is a Lightweight, Isolated and ecutable unit, It runs an application with all required dependencies.
  * It is created from a Docker image and ensures that the application runs the same in any environment.
  * Containers are widely used in microservices architecture for easy deployment and scalability.

### Benefits
-   Consistent runtime environment
-   Easy deployment
-   Quick startup compared to VMs

------------------------------------------------------------------------

## 🧾 Dockerfile

A **Dockerfile** is a script containing instructions to build a **Docker Image**. A Dockerfile is  is a script inside dockerfile set of/ instructions used to build a Docker image. It defines everything needed to create a container.

### It defines:
-   Base Image (Ubuntu, Node.js, Python)
-   Application code
-   Dependencies
-   Environment variables
-   Commands to run inside container

### Example

``` dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm","start"]
```

------------------------------------------------------------------------

## ⚙️ Docker Compose

**Docker Compose** is used to run **multiple containers together**.

It uses a configuration file:

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

Benefits:

-   Manage multiple containers
-   Start everything with one command
-   Simplifies development environments

------------------------------------------------------------------------

## ☁️ Docker Hub

**Docker Hub** is a **cloud-based repository** for Docker images.

You can:

-   Store images
-   Share images
-   Download public images

Example:

    docker pull nginx

------------------------------------------------------------------------

## 🔗 Container Orchestration

### Docker Swarm

Docker's **built-in orchestration tool** used for:

-   Clustering containers
-   Load balancing
-   Scaling services

------------------------------------------------------------------------

### Kubernetes (K8s)

**Kubernetes** is a powerful container orchestration platform used for
large-scale deployments.

Features:

-   Auto scaling
-   Self healing
-   Load balancing
-   Rolling updates

------------------------------------------------------------------------

## 🎯 Summary

Docker simplifies application deployment by packaging everything into
containers.

Main Components:

-   Docker
-   Docker Images
-   Docker Containers
-   Dockerfile
-   Docker Compose
-   Docker Hub
-   Docker Swarm
-   Kubernetes

------------------------------------------------------------------------

⭐ **Docker enables faster development, reliable deployments, and
scalable applications.**
