# 🐳✨ What is a multi-stage build in Docker?

A multi-stage build means using multiple FROM statements in one Dockerfile to create different stages.

👉 One stage is for building the app, and another is for the final lightweight image

💡 Multi-stage builds help me keep Docker images small and clean.

🔧 I build the app in one stage, and copy only the necessary files to the final image.

🧹 This removes all the build tools and reduces the image size.

---

# 🚀 Why is it useful? (Benefits)

✅ Smaller image size — only copies needed files to final image  

🔒 Cleaner and more secure — no build tools or source code in final image  

⚡ Improves performance — lighter image = faster pull/deploy  

---

# 📦🧪 Example (Node.js + Nginx) Dockerfile:

# 🏗️ Stage 1: Build the app
FROM node:18 AS builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

# 🌐 Stage 2: Final image
FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
