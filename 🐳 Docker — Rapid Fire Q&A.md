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

---

## 🐳 Docker Scenario-Based — Rapid Fire Q&A

| #️⃣    | ❓ Question                                                                 | ✅ Answer                                                        |
| ------ | -------------------------------------------------------------------------- | --------------------------------------------------------------- |
| 1️⃣    | ❌ Docker container exits immediately after starting — why?                 | 👉 Main process inside container stopped                        |
| 2️⃣    | 🔍 How troubleshoot exited container?                                      | 👉 Check logs using `docker logs <container-id>`                |
| 3️⃣    | 🌍 Container works locally but fails in server — reasons?                  | 👉 Environment differences, missing ports, volume/config issues |
| 4️⃣    | 🏗️ Docker image build failing at dependency install — checks?             | 👉 Internet access, package repository, Dockerfile syntax       |
| 5️⃣    | 🐢 Build extremely slow — optimization?                                    | 👉 Layer caching, smaller base image, multi-stage builds        |
| 6️⃣    | 🧩 Why use multi-stage builds?                                             | 👉 Reduce final image size                                      |
| 7️⃣    | 🌐 Application running inside container but inaccessible externally — why? | 👉 Port not exposed/mapped                                      |
| 8️⃣    | 🔌 Correct Docker port mapping example?                                    | 👉 `docker run -p 8080:80 nginx`                                |
| 9️⃣    | 🌍 Container cannot reach internet — checks?                               | 👉 Docker network and host firewall                             |
| 🔟     | 💾 Data lost after container restart — reason?                             | 👉 No persistent volume mounted                                 |
| 1️⃣1️⃣ | 📦 Solution for persistent data?                                           | 👉 Docker volumes/bind mounts                                   |
| 1️⃣2️⃣ | 💽 Create Docker volume?                                                   | 👉 `docker volume create myvol`                                 |
| 1️⃣3️⃣ | 📈 Docker container consuming high CPU — troubleshooting?                  | 👉 Check processes, app loops, monitor resources                |
| 1️⃣4️⃣ | 📊 Command to monitor containers live?                                     | 👉 `docker stats`                                               |
| 1️⃣5️⃣ | 💽 Docker server disk full — causes?                                       | 👉 Unused images, containers, volumes, logs                     |
| 1️⃣6️⃣ | 🧹 Cleanup unused Docker resources?                                        | 👉 `docker system prune`                                        |
| 1️⃣7️⃣ | 🔗 Two containers cannot communicate — checks?                             | 👉 Ensure same Docker network                                   |
| 1️⃣8️⃣ | 🌉 Create custom Docker network?                                           | 👉 `docker network create mynet`                                |
| 1️⃣9️⃣ | 🧩 Why use Docker Compose?                                                 | 👉 Manage multi-container applications                          |
| 2️⃣0️⃣ | ▶️ Start services with Compose?                                            | 👉 `docker compose up -d`                                       |
| 2️⃣1️⃣ | 🔍 One Compose service failing — troubleshooting?                          | 👉 Check service logs individually                              |
| 2️⃣2️⃣ | 🚫 Why avoid running containers as root?                                   | 👉 Security risk                                                |
| 2️⃣3️⃣ | 🛡️ Best practice for Docker image security?                               | 👉 Minimal images, vulnerability scanning, non-root users       |
| 2️⃣4️⃣ | 📤 Docker push failing — reasons?                                          | 👉 Authentication issue, tag missing, permission denied         |
| 2️⃣5️⃣ | 🔐 Login to Docker registry?                                               | 👉 `docker login`                                               |
| 2️⃣6️⃣ | ☸️ Pod crashing due to Docker issue — checks?                              | 👉 Image pull, entrypoint, logs                                 |
| 2️⃣7️⃣ | ❌ ImagePullBackOff error means?                                            | 👉 Kubernetes unable to pull image                              |
| 2️⃣8️⃣ | 🔄 Docker build works locally but fails in CI — why?                       | 👉 Environment/dependency differences                           |
| 2️⃣9️⃣ | 🏷️ Why tag Docker images properly?                                        | 👉 Version tracking and rollback                                |
| 3️⃣0️⃣ | 📌 Recommended tagging strategy?                                           | 👉 Semantic versions + commit SHA                               |
| 3️⃣1️⃣ | 🔙 New container version causing failures — action?                        | 👉 Rollback to previous stable image                            |
| 3️⃣2️⃣ | 🚫 Why avoid `latest` tag in production?                                   | 👉 Unpredictable deployments                                    |
| 3️⃣3️⃣ | 📜 Container logs growing too large — solution?                            | 👉 Configure log rotation                                       |
| 3️⃣4️⃣ | 🔄 View running container logs?                                            | 👉 `docker logs -f <container>`                                 |
| 3️⃣5️⃣ | ❤️ Container marked unhealthy — reasons?                                   | 👉 Health endpoint failing                                      |
| 3️⃣6️⃣ | 🩺 Why use Docker HEALTHCHECK?                                             | 👉 Automatic application health monitoring                      |
| 3️⃣7️⃣ | 📦 Docker image size too large — fixes?                                    | 👉 Alpine images, remove packages, multi-stage builds           |
| 3️⃣8️⃣ | 🌐 Container cannot resolve service name — why?                            | 👉 DNS/network misconfiguration                                 |
| 3️⃣9️⃣ | 🔄 Auto-restart container after crash — how?                               | 👉 `docker run --restart always`                                |
| 4️⃣0️⃣ | 🔁 Containers restart continuously — checks?                               | 👉 App crash, env vars, health checks                           |
| 4️⃣1️⃣ | 🗄️ App works but DB connection fails — why?                               | 👉 Wrong hostname/network configuration                         |
| 4️⃣2️⃣ | 🔐 Secrets hardcoded in image — problem?                                   | 👉 Major security vulnerability                                 |
| 4️⃣3️⃣ | 🛡️ Better way to manage secrets?                                          | 👉 Environment variables/secrets manager                        |
| 4️⃣4️⃣ | 📊 How monitor Docker containers?                                          | 👉 Prometheus, Grafana, cAdvisor                                |
| 4️⃣5️⃣ | 🪶 Why use distroless images?                                              | 👉 Smaller attack surface                                       |
| 4️⃣6️⃣ | ⚠️ What happens if Docker daemon stops?                                    | 👉 Containers stop/manageability lost                           |
| 4️⃣7️⃣ | 📋 List running containers?                                                | 👉 `docker ps`                                                  |
| 4️⃣8️⃣ | 📋 List all containers?                                                    | 👉 `docker ps -a`                                               |
| 4️⃣9️⃣ | 🔍 Inspect container details?                                              | 👉 `docker inspect <container>`                                 |
| 5️⃣0️⃣ | 🚀 Why Docker popular in DevOps?                                           | 👉 Consistent environments + portability + scalability          |

---

## 🔥 Pro Tips (Interview Gold)

| ⭐ Best Practice            | 💡 Why Important            |
| -------------------------- | --------------------------- |
| 🚫 Avoid `latest` tag      | Predictable deployments     |
| ❤️ Use health checks       | Automatic monitoring        |
| 💾 Use volumes             | Persistent data storage     |
| 🛡️ Scan images with Trivy | Detect vulnerabilities      |
| 📦 Keep images small       | Faster builds & deployments |
| 👤 Run as non-root user    | Better security             |
| 🧩 Use multi-stage builds  | Smaller optimized images    |
