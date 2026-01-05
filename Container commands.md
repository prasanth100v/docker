## ✅ Correct Way to Remove the Container
1️⃣ Stop the running container
```
docker stop 6a8473d57378     # Container ID
```
2️⃣ Remove the container
```
docker rm 6a8473d57378         # Container ID
```
🚀 One-Line Shortcut (force remove)
> Stops + removes in one command:
```
docker rm -f 6a8473d57378
```
✅ Verify
```
docker ps
```
➡️ Container should be gone.

### 🧹 (Optional) Remove the Docker Image
> If you also want to delete the image:
```
docker rmi ec5887dd3cb8         #docker rmi IMAGE_ID
```
If it fails:
```
docker rmi -f ec5887dd3cb8     #Image ID
```
## 📌 Pro Tip (Use container name)
Instead of IDs, you can do:
```
docker rm -f prasanth-poultry-app
```
Much easier 👍

## 🧹 Remove ALL Unused Images (SAFE)
```
docker image prune
```
Add -a to remove unused + dangling:
```
docker image prune -a
```
🧼 Full Docker Cleanup (Images + Containers + Cache)
```
docker system prune -a
```

## Dangling images
### Dangling images in Docker are unused, untagged images that are left behind after builds.
💣 Remove ALL Unused Images (More Aggressive)
```
docker image prune -a         # Remove all dangling images.
```
🤔 Why Dangling Images Are Created
> When you rebuild an image:
```
docker build -t myapp .
```
Docker:
```
Creates a new image
Removes the tag from the old image
Old image becomes dangling
```
🧪 Check Dangling Images Only
```
docker images -f dangling=true
```
🧹 Remove Dangling Images (SAFE)
```
docker image prune
```
This:  ✅ Removes only dangling images   ❌ Does NOT remove images in use


