# 🐳⚡ Basic Docker Commands
```
docker pull nginx:alpine                # ⬇️ Download an image 
docker build -t myapp:latest .            # 🏗️ Build image from Dockerfile
docker run -d my-image                  # 🚀 Run a container in the background
docker pull ubuntu:20.04                #📥 Downloads an image from a registry (e.g., Docker Hub) but does not run it.  
docker ps                                # 📋 - List all running containers  
docker ps -a                             # 📋 - For all containers (including stopped ones)  
```

## 🛑 Stop & Remove Commands
```
docker stop <container_id>             # 🛑 Stop Container   
docker rm <container_id>               # ❌ Remove Container 
docker rm -f <container_id>            # 💥 Force-remove a running container 
```

## 🧑‍💻 Access container shell 
```
docker exec -it <container_id> /bin/bash   # 💻 container running but need to edit files inside it (inside a running container)
```

## 🌐 Network commands
```
docker network ls                      # 🌐 List all networks  
docker network inspect <network>       # 🔎 Show network details  
```

## 🏷️ Tag Command
```
docker tag myapp myusername/myapp:v1.0        # 🏷️ Docker Tags  # Use formats like v1, v1.0, v1.0.1 for clarity  
```

## 🔵 Docker Info & Version
```
docker --version              # 📌 Show Docker version
docker version                # 📊 Detailed version info
docker info                   # 🧠 System-wide information
```

## 🟢 Docker Images
```
docker images                 # 📦 List all images
docker pull nginx             # ⬇️ Download image from Docker Hub
docker push myimage           # ⬆️ Upload image to Docker Hub
docker rmi image_id           # ❌ Remove image
docker build -t myimage .     # 🏗️ Build image from Dockerfile
```

## 🟡 Docker Containers
```
docker run nginx                     # ▶️ Run container
docker run -d nginx                 # 💤 Run in detached mode
docker run -it ubuntu bash          # 💻 Interactive terminal
docker ps                           # 📃 List running containers
docker ps -a                         # 📚 List all containers
docker stop container_id             # ⛔ Stop container
docker start container_id             # ▶️ Start container
docker restart container_id          # 🔄 Restart container
docker rm container_id               # ❌ Remove container
docker exec -it container bash        # 🔐 Access running container
docker logs container_id               # 📜 View logs
```

## 📦 volume commands
```
docker volume create my_volume           # 📦 Create a named volume 
docker volume ls                         # 📋 List all volumes
docker volume inspect my_volume          # 🔍 Inspect a volume 
docker volume rm my_volume               # ❌ Remove a volume  
docker volume prune -a                   # 🧹 Remove all unused volumes 
```

## 🔴 Docker System Cleanup
```
docker system df                  # 📊 Show disk usage
docker system prune               # 🧹 Remove unused data
docker system prune -a            # 🚨 Remove ALL unused data (including images)
docker container prune            # 🧼 Remove stopped containers
docker image prune                # 🗑️ Remove unused images
docker volume prune               # 💥 Remove unused volumes
```

## 🟤 Docker Logs & Stats
```
docker logs container_id      # 📜 Show logs
docker logs --tail 100 <container_id>         # 📊 Show last 100 lines   
docker logs --since 1h <container_id>         # ⏱️ Logs from the last hour
docker logs -f container_id   # 🔄 Follow logs
docker stats                  # 📈 Live resource usage
```

## ⚫ Docker Inspect & Debug
```
docker inspect container_id   # 🔍 Detailed info (JSON)
docker top container_id       # 🧵 Running processes
docker diff container_id      # 🔄 Changes in container
```

## 🔷 Docker Copy Files
```
docker cp file.txt container:/app     # 📤 Copy to container
docker cp container:/app/file.txt .   # 📥 Copy from container
```

## 🟠 Docker Login / Logout
```
docker login                  # 🔐 Login to Docker Hub
docker logout                 # 🚪 Logout
```

## 🟢 Docker Compose (Important)
```
docker-compose up             # 🚀 Start services
docker-compose up -d          # 💤 Start in background
docker-compose down           # 🛑 Stop services
docker-compose build          # 🏗️ Build services
docker-compose logs           # 📜 View logs
```


## 🟡 Useful Shortcuts
```
docker rm $(docker ps -aq)        # 💥 Remove all containers
docker rmi $(docker images -q)    # 🧨 Remove all images
docker stop $(docker ps -aq)      # 🛑 Stop all containers
```


## 🔥 Advance Commands
```
 docker run -p 8080:80 nginx             # 🌐 Port mapping  # Map host port 8080 → container port 80            
 docker run --name mycontainer nginx    # 🏷️ Name container
 docker run --rm nginx                   # ♻️ Auto-remove after stop
 docker run -e ENV=dev nginx            # 🌍 Set env variable
```



