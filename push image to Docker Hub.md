# 🐳☁️ Push Docker Image to Docker Hub (Step-by-Step)

### 🔐 1️⃣ Login to Docker Hub
 * 👉 From your EC2 terminal : `docker login`
 * 📝 Enter:
    * 👤 Username → your Docker Hub username
    * 🔑 Password → password or Personal Access Token (recommended)

✅ You should see: ***Login Succeeded***

## 🏷️ 2️⃣ Tag the Image
👉 Docker Hub requires this format: `(dockerhub-username/image-name:tag)`  (replace with YOUR username)  (prasanth100v/prasanth-poultry:latest)
```hcl
docker tag prasanth-poultry:latest prasanth100v/prasanth-poultry:latest
```

### 🔍 Verify Image
```hcl
docker images               # 👉 You should see :  **prasanth100v/prasanth-poultry   latest**
```

## 3️⃣ Push the image 🚀
```hcl
docker push prasanth100v/prasanth-poultry:latest       #👉 This uploads your image to Docker Hub ☁️
```
## 🌐 4️⃣ Verify on Docker Hub
 * Go to Docker Hub
 * Open your repository : `https://hub.docker.com/r/prasanth100v/prasanth-poultry`
 * Image should be visible & Tag (latest) should appear ✅ 

## ✅ DONE — Image is now public
⬇️ Anyone can now pull image using:
```hcl
docker pull prasanth100v/prasanth-poultry:latest
```
▶️ run Container :
```hcl
docker run -d -p 80:80 --name prasanth-poultry-app prasanth100v/prasanth-poultry:latest
```

## 🔐 OPTIONAL (Best Practice)
Use version tags instead of latest
```hcl
docker tag prasanth-poultry:latest prasanth100v/prasanth-poultry:v1
docker push prasanth100v/prasanth-poultry:v1
```

🎯 With Version Tags Rollback easily 🔄
