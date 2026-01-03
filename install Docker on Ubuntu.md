### ✅ Method 1: Install Docker using Official Docker Repository (BEST)
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







