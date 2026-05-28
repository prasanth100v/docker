### ✅  Install Docker using Official Docker Repository (BEST)
1️⃣ Remove old Docker versions (important)
```hcl
sudo apt remove -y docker docker-engine docker.io containerd runc
```
2️⃣ Update system
```hcl
sudo apt update
sudo apt upgrade -y
```
3️⃣ Install required packages
```hcl
sudo apt install -y ca-certificates curl gnupg lsb-release
```
4️⃣ Add Docker’s official GPG key
```hcl
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
5️⃣ Add Docker repository
```hcl
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
6️⃣ Install Docker Engine
```hcl
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
7️⃣ Start & enable Docker & Verify Docker installation
```hcl
sudo systemctl start docker
sudo systemctl enable docker
docker --version
```
### 🟢 Run Docker Without sudo (Highly Recommended)
```hcl
sudo usermod -aG docker $USER
newgrp docker
```
Test:
```bash
docker ps
systemctl status docker
```

## 🟡 Remove Docker Completely (Start Fresh) ❌
```hcl
sudo systemctl stop docker
sudo apt purge -y docker-ce docker-ce-cli containerd.io
sudo rm -rf /var/lib/docker /var/lib/containerd
```
