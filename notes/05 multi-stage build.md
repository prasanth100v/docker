## 🐳✨ What is a multi-stage build in Docker?

 * A multi-stage build means using multiple FROM statements in single Dockerfile to create different stages.
 * 👉 One stage is for building the app, and another is for the final lightweight image
 * 💡 Multi-stage builds help me keep Docker images small and clean.
 * 🔧 I build the app in one stage, and copy only the necessary files to the final image.
 * 🧹 This removes all the build tools and reduces the image size.


## 🚀 Why is it useful? (Benefits)

 * ✅ Smaller image size — only copies needed files to final image
 * 🔒 Cleaner and more secure — no build tools or source code in final image
 * ⚡ Improves performance — lighter image = faster pull/deploy
 * 👉 Use multiple FROM statements in a single Dockerfile to create smaller, cleaner, and more secure images.

---

## 📦🧪 Example (Node.js + Nginx) Dockerfile:
```
# 🏗️ Stage 1: Build the app
FROM node:18 AS builder              # AS builder gives a name to the stage
WORKDIR /app                         # Working directory inside the container, All commands will run inside this folder
COPY . .
RUN npm install && npm run build

# 🌐 Stage 2: Final image
FROM nginx:alpine                                         # Only needed to run the app, not build it, 👉 Smaller + more secure image
COPY --from=builder /app/build /usr/share/nginx/html            # --from=builder → pulls from Stage 1
```

### 🔍 How It Works
🏗️ Stage 1 👉 First stage builds the app  (Builder) 
   * Uses Node.js image
   * Installs dependencies
   * Builds the application

🚀 Stage 2 👉 Second stage copies only required files (Final Image)
   * Uses lightweight NGINX image
   * Copies only the built output → smaller image
   * 👉 Final image = lightweight + production-ready

### The result?
  * 👉 My image size dropped significantly
  * 👉 No dev dependencies in production
  * 👉 Much cleaner and faster deployments

### 🧩 Simple Analogy
  * 🛠️ Workshop (Stage 1) → Build product
  * 📦 Showroom (Stage 2) → Only display final product

---

## Real-world multi-stage Dockerfiles for different applications
### 🐳 1. Java (Spring Boot / Maven App)
```
# Stage 1 - Build
FROM maven:3.9.6-eclipse-temurin-17 AS builder
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src ./src
RUN mvn clean package

# Stage 2 - Run
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app
COPY --from=builder /app/target/*.jar app.jar             # 👉 Copies the built .jar → Renames it to app.jar (Final image contains only .jar)
CMD ["java", "-jar", "app.jar"]
```

### ⚛️ 2. React.js (Frontend App)
```
# Stage 1 - Build
FROM node:18 AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2 - Serve
FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

### 🟢 3. Node.js (Backend API)
```
# Stage 1 - Install dependencies
FROM node:18 AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .

# Stage 2 - Run
FROM node:18-alpine
WORKDIR /app
COPY --from=builder /app /app
EXPOSE 3000
CMD ["node", "server.js"]
```

### ⚡ 5. Go (Golang App – Super Lightweight)
```
# Stage 1 - Build
FROM golang:1.22 AS builder
WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download
COPY . .
RUN go build -o app

# Stage 2 - Run
FROM alpine:latest
WORKDIR /app
COPY --from=builder /app/app .           # 👉 Final image is extremely small (~10–20MB)
CMD ["./app"]
```

---

* COPY --from=builder : 👉 It copies files from a previous stage into the current stage.
* ✅ This avoids copying unnecessary files like : source code and dependencies

* Can we use multiple stages beyond two❓
   * 👉 Yes ✅, You can use multiple stages like : Build stage, Test stage and Production stage
   * build tools : `FROM node:18 AS build` , `FROM node:18 AS test` , `FROM nginx:alpine AS prod`


* Is Multi-Stage Build supported in all Docker versions❓
* 👉 Supported from Docker 17.05+., 📌 Earlier versions do not support multiple `FROM`

* Can we skip a stage during build?
* 👉 Yes ✅ using --target
  * `docker build --target builder -t myapp .` 👉 Builds only up to the builder stage

* How does caching work in Multi-Stage Builds❓
* 👉 Each stage has its own cache 👉 This avoids reinstalling dependencies every time

* Your Docker image size is 1.2GB for a Java application. How would you reduce it❓
  * Use multi-stage build
  * Separate build and runtime
  * Remove build tools like Apache Maven from final image
  * Use lightweight base image like Alpine
  * ✅ Result: Image size drastically reduced (e.g., ~200MB or less)

* You only need a .jar file to run your app. How do you avoid shipping source code❓
 * 👉 Use : COPY --from=builder /app/target/app.jar app.jar  -→  ✅ Only .jar copied → no source code in final image


## 🐳 Multi-Stage Docker Commands
```
docker build -t myapp .                                # Build full Dockerfile
docker build --target builder -t myapp-builder .       # Build specific stage
docker build --no-cache -t myapp .                     # Ignore cache

run: docker run -p 8080:8080 myapp            # Run container

ps: docker ps                                 # Running containers
ps_all: docker ps -a                          # All containers
stop: docker stop <id>                        # Stop container
rm: docker rm <id>                            # Remove container


# ⚫ Multi-Stage Key Lines (Dockerfile)

stage: FROM node:18 AS builder                 # Name stage
copy: COPY --from=builder /app/build /out      # Copy from stage

```

