# 🐳⚙️ ONBUILD
 * ONBUILD is used in a Dockerfile to add instructions that will run later, when another Dockerfile uses this image as a base.
 * It helps in creating base images that automatically do things like copying code or installing dependencies for child images.
 * It's mainly used to create reusable base images with pre-defined behaviors, making easier for developers who build similar apps.

## 📌 Example:
### 🧱 (1) Dockerfile Base Image (With ONBUILD)
```
FROM node:18  
WORKDIR /app  
ONBUILD COPY . /app  
ONBUILD RUN npm install      # This image has ONBUILD instructions inside.
```

🏷️ `docker build -f Dockerfile.base -t my-node-base .`   # created an image called my-node-base


### 🧩 (2) Child Dockerfile:
```
FROM my-node-base  
CMD ["node", "app.js"]      # Another project, you write this Dockerfile
```

### 🔥 What Happens Internally?
#### 👉 When child image builds:
   * FROM my-node-base
   * ONBUILD triggers automatically:
     * COPY . /app 📂
     * RUN npm install 📦
   * Then CMD runs

#### ⚠️ 🚨 ONBUILD : Can cause confusion if not documented & Not commonly used in modern production

---

## 📉 How do you reduce Docker image size?

To reduce Docker image size, I follow a few best practices:
- 🪶 I use a small base image like Alpine and slim variants  `node:alpine`, `python:slim`. (Lightweight Images)
- 🚫 I add a .dockerignore file to skip unnecessary files  
- 🔗 I combine RUN commands to reduce layers  
- 🧹 Clean up cache and temporary files 
- 🗑️ I clean up temporary files during the build  
- 🏗️ And I use multi-stage builds to copy only what's needed into the final image  

💡 Example: in a Node.js app, I install dependencies in the first stage, build the app, and then copy only the build folder to a lightweight Nginx image.


## 🔐 How would you secure a Dockerfile against common vulnerabilities?

- 🪶 Use minimal base images (like alpine) to reduce the attack surface  `👉 Smaller images = fewer vulnerabilities`
- 👤 Run as non-root user (USER instruction)  `👉 Prevents privilege escalation`
- 🔄 Keep dependencies updated and remove unused packages  
- 🔍 Scan images for vulnerabilities (docker scan, trivy)  
- 🚫 Don’t store secrets in the Dockerfile  
- 🏗️ Use multi-stage builds to 👉 Remove build tools from final image 
- ✅ Use trusted base images from official repos  
- 🧹 Combine RUN commands and clean up temp files to avoid leaking data in layers  

