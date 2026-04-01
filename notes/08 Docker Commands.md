# 🐳⚡ Docker Commands

---

# 📦 Create a named volume  
docker volume create my_volume  

# 📋 List all volumes         
docker volume ls  

# 🔍 Inspect a volume         
docker volume inspect my_volume  

# ❌ Remove a volume          
docker volume rm my_volume  

# 🧹 Remove all unused volumes 
docker volume prune -a  

---

# 💻 Runs a command inside a running container  
docker exec -it <container_id> /bin/bash   # Opens a shell  

---

# 📄 Show logs               
docker logs <container_id>  

# 📊 Show last 100 lines     
docker logs --tail 100 <container_id>  

# ⏱️ Logs from the last hour 
docker logs --since 1h <container_id>  

---

# ⬇️ Download an image       
docker pull nginx:alpine  

---

# 🏗️ Build image from Dockerfile   
docker build -t myapp:latest .  

---

# 🌐 List all networks       
docker network ls  

# 🔎 Show network details    
docker network inspect <network>  

---

# 💾 Disk usage (images, containers, volumes) 
docker system df  

---

# 🧹 Remove unused data      
docker system prune  

# 🚨 Remove ALL unused data (including images) 
docker system prune -a  

---

# 🏷️ Docker Tags 
docker tag myapp myusername/myapp:v1.0   # Use formats like v1, v1.0, v1.0.1 for clarity  

---

# 🚀 Run a container in the background   
docker run -d my-image  

---

# 📥 docker pull - Downloads an image from a registry (e.g., Docker Hub) but does not run it.  
Example: docker pull ubuntu:20.04  

---

# 📋 docker ps - List all running containers  

# 📋 docker ps -a - For all containers (including stopped ones)  

---

# 🛑 Stop Container 
docker stop <container_id>  

---

# ❌ Remove Container 
docker rm <container_id>  

---

# 💥 Force-remove a running container 
docker rm -f <container_id>  

---

# 🐞 Debug a crashing container 
docker logs <container_id>   # View logs  
inspect <container_id>   # Detailed container info  

---

# 🔌 Port Mapping 
docker run -p 8080:80 nginx   # Map host port 8080 → container port 80  

---

# 🧑‍💻 Access container shell 
docker exec -it <container_id> /bin/bash   # container running but need to edit files inside it  




