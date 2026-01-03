## 1️⃣ Login to Docker Hub
First, log in from your EC2 terminal:
```
docker login
```
#### Enter:
> Username: your Docker Hub username && Password: Docker Hub password or **Access Token**

✅ You should see: ***Login Succeeded***

## 2️⃣ Tag the image for Docker Hub
Docker Hub requires this format: ***<dockerhub-username>/<image-name>:tag***
> (replace with YOUR username)
```
docker tag prasanth-poultry:latest prasanth100v/prasanth-poultry:latest
```
### Verify:
```
docker images
```
You should now see: ***prasanth100v/prasanth-poultry   latest***
## 3️⃣ Push the image 🚀
```
docker push prasanth100v/prasanth-poultry:latest
```
## 4️⃣ Verify on Docker Hub
```
Go to Docker Hub
Open your repository:
https://hub.docker.com/r/prasanth100v/prasanth-poultry
```
> Image should be visible ✅

## ✅ DONE — Image is now public
Anyone can now pull it using:
```
docker pull prasanth100v/prasanth-poultry:latest
```
And run it:
```
docker run -d -p 80:80 --name prasanth-poultry-app prasanth100v/prasanth-poultry:latest
```
## 🔐 OPTIONAL (Best Practice)
Use version tags instead of latest
```
docker tag prasanth-poultry:latest prasanth100v/prasanth-poultry:v1
docker push prasanth100v/prasanth-poultry:v1
```


