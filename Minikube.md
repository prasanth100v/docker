# 🚀 What is Minikube?
Minikube is a tool, It creates a single-node Kubernetes cluster for learning, development, and testing.

## 📜 Minikube Installation Script (Ubuntu)
🔹 Step 1: Create the script
```
vi install-minikube.sh
```
```
#!/bin/bash
set -e

echo "========================================"
echo " Minikube + Docker + kubectl Installer "
echo "========================================"

echo "[1/8] Updating system..."
sudo apt update -y
sudo apt upgrade -y

echo "[2/8] Installing required packages..."
sudo apt install -y curl wget apt-transport-https ca-certificates gnupg

echo "[3/8] Installing Docker..."
sudo apt install -y docker.io
sudo systemctl enable docker
sudo systemctl start docker
docker --version

echo "[4/8] Creating docker group (if not exists)..."
if ! getent group docker > /dev/null; then
  sudo groupadd docker
  echo "Docker group created"
else
  echo "Docker group already exists"
fi

echo "[5/8] Adding user to docker group..."
sudo usermod -aG docker $USER
echo "⚠️ Logout & login again for docker group to apply"

echo "[6/8] Installing kubectl..."
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
kubectl version --client

echo "[7/8] Installing Minikube..."
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
chmod +x minikube-linux-amd64
sudo mv minikube-linux-amd64 /usr/local/bin/minikube
minikube version

echo "========================================"
echo " Installation completed successfully!"
echo "========================================"
echo "➡️ Please LOGOUT and LOGIN again"
echo "➡️ Then run: minikube start --driver=docker"
```
> 👉set -e tells Bash: if any command fails, the script stops right there ❌

## minikube start
```
minikube start --driver=docker
minikube status
```
## Test Kubernetes cluster
```
kubectl get nodes
kubectl get pods -A
```

## 🔹 Common Useful Commands
```
minikube stop
minikube delete
minikube ssh
minikube addons list
minikube addons enable ingress
```

## Minikube fails to start?
```
minikube delete
minikube start --driver=docker --force
```
