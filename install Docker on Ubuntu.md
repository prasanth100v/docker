### ✅  Install Docker using Official Docker Repository (BEST)
1️⃣ Remove old Docker versions (important)
```
sudo apt remove -y docker docker-engine docker.io containerd runc
```
2️⃣ Update system
```
sudo apt update
sudo apt upgrade -y
```
3️⃣ Install required packages
```
sudo apt install -y ca-certificates curl gnupg lsb-release
```
4️⃣ Add Docker’s official GPG key
```
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
5️⃣ Add Docker repository
```
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
6️⃣ Install Docker Engine
```
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
7️⃣ Start & enable Docker & Verify Docker installation
```
sudo systemctl start docker
sudo systemctl enable docker
docker --version
```
### 🟢 Run Docker Without sudo (Highly Recommended)
```
sudo usermod -aG docker $USER
newgrp docker
```
Test:
```
docker ps
systemctl status docker
```

### 🟡 Remove Docker Completely (Start Fresh) ❌
```
sudo systemctl stop docker
sudo apt purge -y docker-ce docker-ce-cli containerd.io
sudo rm -rf /var/lib/docker /var/lib/containerd
```


```
############################################
# 🐳 DOCKER INSTALLATION (OFFICIAL METHOD)
############################################

##############################
# 🔴 Step 1: Remove Old Versions
##############################
sudo apt remove -y docker docker-engine docker.io containerd runc
# 🧹 Clean old/unused Docker packages

##############################
# 🔵 Step 2: Update System
##############################
sudo apt update
sudo apt upgrade -y
# 🔄 Update package index & upgrade system

##############################
# 🟢 Step 3: Install Required Packages
##############################
sudo apt install -y ca-certificates curl gnupg lsb-release
# 📦 Install dependencies for secure repo access

##############################
# 🟣 Step 4: Add Docker GPG Key
##############################
sudo mkdir -p /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
# 🔐 Add official Docker GPG key for verification

##############################
# 🟡 Step 5: Add Docker Repository
##############################
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
# 🌐 Add official Docker repo

##############################
# 🔶 Step 6: Install Docker Engine
##############################
sudo apt update

sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
# 🚀 Install Docker Engine + CLI + Buildx + Compose

##############################
# 🔷 Step 7: Start & Enable Docker
##############################
sudo systemctl start docker
sudo systemctl enable docker
# ▶️ Start Docker & enable at boot

docker --version
# ✅ Verify installation

############################################
# 🟢 Run Docker Without sudo (Recommended)
##############################################
sudo usermod -aG docker $USER
newgrp docker
# 👤 Add user to docker group

##############################
# 🧪 Test Docker
##############################
docker ps
systemctl status docker
# 🔍 Verify Docker is running

############################################
# 🔴 Remove Docker Completely (Reset)
##############################################
sudo systemctl stop docker

sudo apt purge -y docker-ce docker-ce-cli containerd.io
# ❌ Remove Docker packages

sudo rm -rf /var/lib/docker /var/lib/containerd
# 💥 Delete all Docker data (containers, images, volumes)
```




