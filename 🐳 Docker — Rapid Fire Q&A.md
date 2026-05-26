## 🐳 Docker — Rapid Fire Q&A

| #️⃣    | ❓ Question                                              | ✅ Answer                                                                    |
| ------ | ------------------------------------------------------- | --------------------------------------------------------------------------- |
| 1️⃣    | 🐳 What is Docker?                                      | 👉 A containerization platform used to build, package, and run applications |
| 2️⃣    | 📦 What is a container?                                 | 👉 Lightweight isolated environment containing application + dependencies   |
| 3️⃣    | ⚔️ Difference between container and VM?                 | 👉 Containers share host OS kernel; VMs have separate OS                    |
| 4️⃣    | 🚀 Main advantage of Docker?                            | 👉 Consistency across environments                                          |
| 5️⃣    | 🔧 Why is Docker popular in DevOps?                     | 👉 Fast deployment, portability, scalability                                |
| 6️⃣    | 💡 One-line Docker definition?                          | 👉 Docker packages applications into portable containers                    |
| 7️⃣    | 👨‍💻 Who created Docker?                               | 👉 Docker                                                                   |
| 8️⃣    | ⚙️ Main Docker components?                              | 👉 Docker Client, Daemon, Registry, Images, Containers                      |
| 9️⃣    | 🔄 What is Docker Daemon?                               | 👉 Background service managing containers/images                            |
| 🔟     | 💻 What is Docker Client?                               | 👉 CLI used to interact with Docker daemon                                  |
| 1️⃣1️⃣ | 🌐 What is Docker Hub?                                  | 👉 Public container image registry from Docker                              |
| 1️⃣2️⃣ | 📚 What is a Docker Registry?                           | 👉 Storage location for container images                                    |
| 1️⃣3️⃣ | 🖼️ What is a Docker image?                             | 👉 Read-only template used to create containers                             |
| 1️⃣4️⃣ | 🔄 Difference between image and container?              | 👉 Image = template, container = running instance                           |
| 1️⃣5️⃣ | 📃 Command to list Docker images?                       | 👉 `docker images`                                                          |
| 1️⃣6️⃣ | 📥 Command to pull image?                               | 👉 `docker pull nginx`                                                      |
| 1️⃣7️⃣ | ❌ Command to remove image?                              | 👉 `docker rmi nginx`                                                       |
| 1️⃣8️⃣ | 🧱 What is image layering?                              | 👉 Docker images are built in reusable layers                               |
| 1️⃣9️⃣ | ⚡ Benefit of Docker layers?                             | 👉 Faster builds and smaller storage usage                                  |
| 2️⃣0️⃣ | ▶️ Command to run container?                            | 👉 `docker run nginx`                                                       |
| 2️⃣1️⃣ | 🔙 Run container in background?                         | 👉 `docker run -d nginx`                                                    |
| 2️⃣2️⃣ | 🔤 Meaning of `-d`?                                     | 👉 Detached/background mode                                                 |
| 2️⃣3️⃣ | 📋 Command to list running containers?                  | 👉 `docker ps`                                                              |
| 2️⃣4️⃣ | 📋 Command to list all containers?                      | 👉 `docker ps -a`                                                           |
| 2️⃣5️⃣ | ⛔ Command to stop container?                            | 👉 `docker stop container_id`                                               |
| 2️⃣6️⃣ | ▶️ Command to start stopped container?                  | 👉 `docker start container_id`                                              |
| 2️⃣7️⃣ | 🔄 Command to restart container?                        | 👉 `docker restart container_id`                                            |
| 2️⃣8️⃣ | 🗑️ Command to remove container?                        | 👉 `docker rm container_id`                                                 |
| 2️⃣9️⃣ | 🖥️ Command to enter running container?                 | 👉 `docker exec -it container_id bash`                                      |
| 3️⃣0️⃣ | ⌨️ Meaning of `-it`?                                    | 👉 Interactive terminal mode                                                |
| 3️⃣1️⃣ | 🔌 Command to map ports?                                | 👉 `docker run -p 8080:80 nginx`                                            |
| 3️⃣2️⃣ | 🔢 Meaning of `8080:80`?                                | 👉 Host port : Container port                                               |
| 3️⃣3️⃣ | 🌍 Why use port mapping?                                | 👉 Access container services externally                                     |
| 3️⃣4️⃣ | 📄 What is a Dockerfile?                                | 👉 Script containing image build instructions                               |
| 3️⃣5️⃣ | 🏗️ Command to build image?                             | 👉 `docker build -t myapp .`                                                |
| 3️⃣6️⃣ | 🏷️ Meaning of `-t`?                                    | 👉 Tag image name                                                           |
| 3️⃣7️⃣ | 📚 Common Dockerfile instructions?                      | 👉 FROM, RUN, COPY, CMD, EXPOSE, ENTRYPOINT                                 |
| 3️⃣8️⃣ | 🧱 Purpose of FROM?                                     | 👉 Base image definition                                                    |
| 3️⃣9️⃣ | ⚙️ Purpose of RUN?                                      | 👉 Execute commands during build                                            |
| 4️⃣0️⃣ | 📂 Purpose of COPY?                                     | 👉 Copy files into image                                                    |
| 4️⃣1️⃣ | ▶️ Purpose of CMD?                                      | 👉 Default container startup command                                        |
| 4️⃣2️⃣ | 🌐 Purpose of EXPOSE?                                   | 👉 Document container port                                                  |
| 4️⃣3️⃣ | 💾 What is a Docker volume?                             | 👉 Persistent storage for containers                                        |
| 4️⃣4️⃣ | 🔒 Why use volumes?                                     | 👉 Preserve data after container deletion                                   |
| 4️⃣5️⃣ | 📦 Command to create volume?                            | 👉 `docker volume create myvol`                                             |
| 4️⃣6️⃣ | 🔗 Command to mount volume?                             | 👉 `docker run -v myvol:/data nginx`                                        |
| 4️⃣7️⃣ | ⚖️ Difference between volume and bind mount?            | 👉 Volume managed by Docker; bind mount maps host path                      |
| 4️⃣8️⃣ | 🌉 Default Docker network type?                         | 👉 bridge                                                                   |
| 4️⃣9️⃣ | 📋 Command to list networks?                            | 👉 `docker network ls`                                                      |
| 5️⃣0️⃣ | ➕ Command to create custom network?                     | 👉 `docker network create mynet`                                            |
| 5️⃣1️⃣ | 🔗 Why use custom networks?                             | 👉 Container-to-container communication                                     |
| 5️⃣2️⃣ | 🧩 What is Docker Compose?                              | 👉 Tool to manage multi-container applications                              |
| 5️⃣3️⃣ | 📄 Compose configuration file name?                     | 👉 `docker-compose.yml`                                                     |
| 5️⃣4️⃣ | ▶️ Command to start compose services?                   | 👉 `docker compose up`                                                      |
| 5️⃣5️⃣ | 🔙 Run compose in background?                           | 👉 `docker compose up -d`                                                   |
| 5️⃣6️⃣ | ⛔ Command to stop compose services?                     | 👉 `docker compose down`                                                    |
| 5️⃣7️⃣ | 📜 Command to view container logs?                      | 👉 `docker logs container_id`                                               |
| 5️⃣8️⃣ | 🔄 Command to follow logs continuously?                 | 👉 `docker logs -f container_id`                                            |
| 5️⃣9️⃣ | 🔍 Command to inspect container details?                | 👉 `docker inspect container_id`                                            |
| 6️⃣0️⃣ | 📈 Command to view resource usage?                      | 👉 `docker stats`                                                           |
| 6️⃣1️⃣ | 🧹 Command to remove unused resources?                  | 👉 `docker system prune`                                                    |
| 6️⃣2️⃣ | 🗑️ Command to delete unused images only?               | 👉 `docker image prune`                                                     |
| 6️⃣3️⃣ | 💽 Why clean Docker resources?                          | 👉 Free disk space                                                          |
| 6️⃣4️⃣ | 🔍 Why scan Docker images?                              | 👉 Detect vulnerabilities before deployment                                 |
| 6️⃣5️⃣ | 🛡️ Common image scanning tool?                         | 👉 Trivy                                                                    |
| 6️⃣6️⃣ | 📦 Best practice for Docker images?                     | 👉 Use minimal base images                                                  |
| 6️⃣7️⃣ | 🚫 Why avoid running containers as root?                | 👉 Security risk                                                            |
| 6️⃣8️⃣ | 🔄 Why Docker useful in CI/CD?                          | 👉 Consistent builds and deployments                                        |
| 6️⃣9️⃣ | ☸️ Common container orchestration tool?                 | 👉 Kubernetes                                                               |
| 7️⃣0️⃣ | 🔗 Why use Docker with Kubernetes?                      | 👉 Kubernetes manages container workloads                                   |
| 7️⃣1️⃣ | 🏗️ Typical Docker workflow?                            | 👉 Build → Push → Deploy → Scale                                            |
| 7️⃣2️⃣ | 📤 Command to push image to registry?                   | 👉 `docker push username/app:tag`                                           |
| 7️⃣3️⃣ | 🔐 Command to login Docker registry?                    | 👉 `docker login`                                                           |
| 7️⃣4️⃣ | ❌ Container exits immediately after start — why?        | 👉 Main process finished                                                    |
| 7️⃣5️⃣ | 🌍 Docker container cannot access app externally — why? | 👉 Port mapping missing                                                     |
| 7️⃣6️⃣ | 💾 Data lost after container deletion — why?            | 👉 No volume configured                                                     |
| 7️⃣7️⃣ | 🐢 Image build slow — improve?                          | 👉 Optimize Docker layers and caching                                       |
| 7️⃣8️⃣ | 🪶 Why use Alpine Linux images?                         | 👉 Smaller image size                                                       |
| 7️⃣9️⃣ | 🏗️ Why use multi-stage builds?                         | 👉 Reduce final image size                                                  |
| 8️⃣0️⃣ | ⚖️ Difference between CMD and ENTRYPOINT?               | 👉 CMD provides default args; ENTRYPOINT defines main executable            |
