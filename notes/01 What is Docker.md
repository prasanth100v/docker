# 🐳 Docker Basics 
## ✅ 1. What is Docker?
 * **Docker** is a **containerization platform** that helps you package applications and their dependencies into **lightweight and portable containers**.
 * Inside a container, everything required to run the application is included :
    * Application code
    * Runtime
    * Libraries
    * System dependencies
    * Configuration files
 * This ensures the application runs **the same everywhere** --- whether on a `developer laptop`, `testing environment`, or `production server`.

## 🚀 Why Use Docker?
| 🧩 Feature     | 💡 Description                                                  |
| -------------- | --------------------------------------------------------------- |
| 🔁 Consistency | 📦 Works the same across dev, test, and production environments |
| 🧱 Isolation   | 🛡️ Apps run in separate containers → `no conflicts  `            |
| 🌍 Portability | 💻 Runs anywhere (`Linux, Windows, macOS, cloud`)                 |
| ⚡ Efficiency   | 🚀 Lightweight vs VMs (`faster startup`, `less overhead`)       |
| 📈 Scalability | 🔄 Easily scale using Kubernetes or Docker Swarm                 |

---

## 📦 Docker Image
 * A **Docker Image** is a **read-only template** used to create containers.
 * It includes:
   * Application code
   * Dependencies
   * Configuration
   * Runtime environment

### Key Points
  * Images are built in **layers**
  * Each layer comes from instructions in a **Dockerfile**
  * Images are stored in **Docker registries** like **Docker Hub**
  * When an image runs → it becomes a **container**

## 📦 Docker Container
  * A **Docker Container** is a `Lightweight`, Isolated and executable unit, It runs an application with all required dependencies.
  * It is created from a Docker image and ensures that the application runs the same in any environment.
  * Containers are widely used in `microservices architecture` for easy deployment and scalability.
  * Docker simplifies `application deployment` by packaging everything into containers.

### Benefits
 * Consistent runtime environment
 * Easy deployment
 * Quick startup compared to VMs

## 🧾 Dockerfile
 * A **Dockerfile** is a set of instructions instructions to build a **Docker Image**. It defines everything needed to create a container.
 * It defines:
   * Base Image (`Ubuntu`, `Node.js`, `Python`)
   * Application code
   * Dependencies
   * Environment variables
   * Commands to run inside container

### Example
``` dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm","start"]
```

---

## ⚙️ Docker Compose
 * **Docker Compose** Used for managing **multiple containers** in a single machine, Using a single YAML file (docker-compose.yml)

## ☁️ Docker Hub
 * **Docker Hub** is a **cloud-based repository** for Docker images.
 * You can:
   * Store images
   * Share images
   * Download public images = Example: `docker pull nginx`

---

## 🔗 Container Orchestration
 * Docker Swarm : Docker's **built-in orchestration tool** for clustering and scaling containers.
 * Kubernetes (K8s) : **Kubernetes** is a powerful container orchestration platform used for `large-scale` deployments.
    * Features:
     * Auto scaling & Self healing
     * Load balancing & Rolling updates

---

## 🚀 Difference Between Docker Container and VM
### 🟢 Docker Containers
  * Docker containers are `lightweight` and start quickly because they share the `Host OS kernel` 🚀.
  * Example:⚡If you're using `Ubuntu` and you install Docker on it, then Ubuntu is the Host OS. All Docker containers will run on top of `Ubuntu's kernel`.

### 🔴 Virtual Machines (VMs)
  * 🐢 VMs are heavier because each one runs its own OS through a hypervisor.

---

## 📥 docker pull vs docker run
### 📥 docker pull
 * ⬇️ Downloads image from registry
 * ❌ Does NOT start container
 *  👉 Example:
  ```bash
   docker pull nginx
  ```

### ▶️ docker run
  * 🏃 Creates & starts a container
  * Example:
```hcl
docker run -d nginx
```

### 💡 Simple Analogy
 * 📥 docker pull = Download app
 * ▶️ docker run = Install + Start app

---

## 🛠️ Debugging Docker Containers
 * To debug a container, I check the `logs` with `docker logs`, use `docker exec` to go inside the container, and `docker inspect` to view its configuration and settings.

```hcl
docker logs <container-name>                 # 📄 View Logs

docker exec -it <container-name> /bin/sh     # 💻 Access Container : Open terminal inside the container to check files, processes, or configs

docker inspect <container-name>              # 🔍 Inspect Container : Shows low-level info like environment variables, network settings, mounts, etc. 
```

## 🔐 Scanning Docker Images for Vulnerabilities (`docker scan`, `Trivy`)
 * I use tools like docker scan and Trivy to check Docker images for any security issues. 

### 🧪 Docker Scan :
 * Scans the image for known `vulnerabilities` in OS packages and dependencies.
 * Example: 
```hcl
docker scan <image-name>           # 🧪 docker scan
```

### ⚡ Trivy
 * Trivy is fast, easy to use, and gives detailed reports on :
   * OS vulnerabilities
   * Application dependencies (`npm`, `pip`)
   * Misconfigurations & secrets  
 * Example :
```hcl
trivy image <image-name>
```
 * I use `docker scan` and `Trivy` to find security vulnerabilities in my Docker images.
 * These tools help me fix known issues before pushing images to production.

---

## 🔎 What is Trivy?
  * Trivy is an open-source security vulnerability scanner that check the Docker images 🔓
  * Fast & lightweight ⚡
  * Easy to use – one command scans everything
  * Works in `CI/CD pipelines`
  * No external services needed  

## 📥 Install Trivy (Linux)
```hcl
sudo apt install wget
wget https://github.com/aquasecurity/trivy/releases/latest/download/trivy_0.49.1_Linux-64bit.deb
sudo dpkg -i trivy_0.49.1_Linux-64bit.deb
```

### Check version:
```hcl
trivy --version
```

## ▶️ How do you run a Docker container?
```hcl
docker run -d -p 8080:80 --name my_container nginx
```
### 🧩 Options Explained
 - `-d` → 💤 Run in background  
 - `-p` 8080:80 → 🌐 Port mapping
 - `--name` → 🏷️ Container name

👉 Access app:
```hcl
http://localhost:8080
```

## 📉 How to reduce Docker image size?
  - Use minimal base image (Use `alpine` instead of Ubuntu 👉 Smaller = Fastere) 🪶  
  - Combine RUN commands to 👉 Reduces layers
  ```hcl
  RUN apt update && apt install -y curl && rm -rf /var/lib/apt/lists/*
  ```
  - Remove unnecessary files after installation. ( `Delete cache`, `temp files` )
  - Use `.dockerignore` to exclude unwanted files. (`node_modules`, `logs` & `temp files`)

---

## 🐳 Docker Quick Concepts
| 🧩 Concept    | 💡 Description                         |
| ------------- | -------------------------------------- |
| 🐳 Containers | ⚡ Fast, lightweight, share host OS     |
| 🖥️ VMs       | 🐢 Heavy, include full OS              |
| 📥 `pull`     | 📦 Download image from registry        |
| ▶️ `run`      | 🚀 Start a container                   |
| 🛠️ Debug     | 🔍 Use `logs`, `exec`, `inspect`       |
| 🔐 Security   | 🛡️ Scan images (`docker scan`, Trivy) |
| 📦 Optimize   | ⚡ Use Alpine images + reduce layers    |

✨ *Happy Learning DevOps!* ✨

