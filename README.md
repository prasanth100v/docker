## 🐳 Docker Glossary with Examples
| 🌟 **Term**                   | 📘 **Definition (Simple)**                                    | 💡 **Example / Explanation**                                 |
| ----------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------ |
| 🐳 **Docker**                 | A platform to build, ship, and run applications in containers | Run the same app on laptop, server, or cloud without changes |
| 📦 **Container**              | A lightweight, isolated environment to run an app             | Running Nginx web server container                           |
| 🖼️ **Image**                 | A read-only template used to create containers                | `nginx:latest` image                                         |
| 📜 **Dockerfile**             | A text file with instructions to build an image               | Contains `FROM`, `RUN`, `CMD`                                |
| 🧱 **Layer**                  | Each instruction in Dockerfile creates a layer                | `RUN apt install` creates a new layer                        |
| 🏗️ **Base Image**            | The starting image for your Dockerfile                        | `FROM ubuntu:22.04`                                          |
| 🗂️ **Registry**              | Storage for Docker images                                     | Docker Hub, AWS ECR                                          |
| ☁️ **Docker Hub**             | Public Docker image registry                                  | Pull images like `mysql`, `redis`                            |
| 🏷️ **Tag**                   | Version of an image                                           | `nginx:1.25`, `python:3.11`                                  |
| 💾 **Volume**                 | Persistent storage for containers                             | DB data survives container restart                           |
| 🔗 **Bind Mount**             | Map host directory to container                               | `/home/app:/usr/src/app`                                     |
| 🚪 **Port Mapping**           | Connect container port to host port                           | `-p 8080:80`                                                 |
| ▶️ **CMD**                    | Default command run in container                              | `CMD ["node","app.js"]`                                      |
| 🚀 **ENTRYPOINT**             | Fixed command that always runs                                | Used for scripts or binaries                                 |
| ⚙️ **RUN**                    | Executes command during image build                           | `RUN apt-get update`                                         |
| 📂 **COPY**                   | Copy files from host to image                                 | `COPY app.py /app/`                                          |
| ➕ **ADD**                     | Copy files + extract archives                                 | Auto-extract `.tar`                                          |
| 🌐 **EXPOSE**                 | Documents container port                                      | `EXPOSE 80`                                                  |
| 🌍 **ENV**                    | Set environment variables                                     | `ENV DB_HOST=localhost`                                      |
| 📁 **WORKDIR**                | Set working directory                                         | `WORKDIR /app`                                               |
| 🏗️ **docker build**          | Build image from Dockerfile                                   | `docker build -t myapp .`                                    |
| ▶️ **docker run**             | Create and start container                                    | `docker run -d nginx`                                        |
| 📋 **docker ps**              | List running containers                                       | Shows container IDs                                          |
| ⏹️ **docker stop**            | Stop a running container                                      | `docker stop abc123`                                         |
| ❌ **docker rm**               | Delete container                                              | `docker rm abc123`                                           |
| 🗑️ **docker rmi**            | Delete image                                                  | `docker rmi nginx`                                           |
| 🖥️ **docker exec**           | Run command inside container                                  | `docker exec -it c1 bash`                                    |
| 🌙 **Detached Mode**          | Run container in background                                   | `docker run -d nginx`                                        |
| 💻 **Interactive Mode**       | Run container with terminal                                   | `docker run -it ubuntu bash`                                 |
| 🌐 **Network**                | Enables container communication                               | Bridge network by default                                    |
| 🌉 **Bridge Network**         | Default Docker network                                        | Containers communicate via IP                                |
| 🏠 **Host Network**           | Container uses host network                                   | No port mapping needed                                       |
| 🚫 **None Network**           | No network access                                             | Fully isolated container                                     |
| 🧩 **Docker Compose**         | Tool to run multi-container apps                              | Run app + DB together                                        |
| 📜 **docker-compose.yml**     | YAML file for Compose                                         | Defines services and volumes                                 |
| 🛠️ **Service**               | One container definition in Compose                           | `web`, `db`                                                  |
| 📈 **Scaling**                | Run multiple containers of same service                       | `docker compose up --scale web=3`                            |
| ❤️ **Health Check**           | Checks container health                                       | Restart if app crashes                                       |
| 🏗️➡️📦 **Multi-stage Build** | Use multiple images to reduce size                            | Build → copy → runtime                                       |
| 👻 **Orphan Container**       | Container not in Compose file                                 | Leftover container                                           |
| 🗑️ **Dangling Image**        | Unused image without tag                                      | `<none>:<none>`                                              |
