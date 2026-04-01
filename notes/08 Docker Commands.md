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

## volume commands
```
docker volume create my_volume           # 📦 Create a named volume 
docker volume ls                         # 📋 List all volumes
docker volume inspect my_volume          # 🔍 Inspect a volume 
docker volume rm my_volume               # ❌ Remove a volume  
docker volume prune -a                   # 🧹 Remove all unused volumes 
```

## 🧑‍💻 Access container shell 
```
docker exec -it <container_id> /bin/bash   # 💻 container running but need to edit files inside it (inside a running container)
```

 ## 📄 logs commands
 ```
docker logs <container_id>                    # 📄 Show logs   
docker logs --tail 100 <container_id>         # 📊 Show last 100 lines   
docker logs --since 1h <container_id>         # ⏱️ Logs from the last hour 
```

## Network commands
```
docker network ls                      # 🌐 List all networks  
docker network inspect <network>       # 🔎 Show network details  
```

### Data commands
```
docker system df                  # 💾 Disk usage (images, containers, volumes) 
docker system prune               # 🧹 Remove unused data  
docker system prune -a            # 🚨 Remove ALL unused data (including images) 
```

## 🏷️ Tag Command
```
docker tag myapp myusername/myapp:v1.0        # 🏷️ Docker Tags  # Use formats like v1, v1.0, v1.0.1 for clarity  
```

## 🐞 Debug a crashing container 
```
docker logs <container_id>       # View logs  
inspect <container_id>           # Detailed container info  
```

## 🔌 Port Mapping 
```
docker run -p 8080:80 nginx   # Map host port 8080 → container port 80  
```
