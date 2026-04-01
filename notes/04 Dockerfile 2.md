## 🏷️ LABEL
* LABEL is used to add metadata (information) to the Docker image, like the author name, version, or description.
* It helps with documentation and image management. Can be viewed with docker inspect

🧾 Syntax : LABEL key="value"  

```
LABEL stage="builder"                          # Single Label  
LABEL maintainer="dev@example.com"    
      version="1.0"                            # multiple labels  
      description="This is a sample image"
```

---

## 🌱 ENV
ENV is used to set environment variables in the Docker image. These variables are available during build and inside the running container.
```
ENV PORT=8080  
ENV NODE_ENV=production \  
    PORT=3000 \              # Multiple Variables  
    APP_HOME=/app  
```
WORKDIR `$APP_HOME` 

🔄 docker run -e PORT=`5000` my-app     # Override ENV at runtime  

* 💡 Environment variables are key-value pairs used to store configuration settings. (Config values available inside container)
* 💡 Use Cases:
   * App configs
   * Database URLs
   * Ports
 
### 🔑 Key Points: 🏗️ Available during build + runtime & 🔄 Can override at runtime
  
---

## 🧪 ARG
ARG is used to define build-time variables. You can pass values to it only while building the image, not when running the container.

📌 Example:
   ```
    FROM ubuntu  
    ARG APP_VERSION=1.0                               # 👉 ARG = Build-time variable
    RUN echo App version is $APP_VERSION  
  ```
  
  docker build --build-arg `APP_VERSION=2.0` .  # This replaces APP_VERSION with `2.0` during build.

### ⚙️ Docker ARG vs ENV
| 🧩 Feature              | 🛠️ ARG | 🌍 ENV |
| ----------------------- | ------- | ------ |
| 🏗️ Available at build  | ✅ Yes   | ✅ Yes  |
| 🚀 Available at runtime | ❌ No    | ✅ Yes  |

* 👉 ARG : Used during image build time only 🏗️ (Not available inside running container)
* 👉 ENV : Available during build + runtime 🌍 (Used inside)

---

## 👤 USER
* 👉 USER = Define which user runs container
* USER sets the Username or UID. The USER instruction in a Dockerfile tells Docker which user should run the application and any commands.
* By default, Docker containers run as root, but using USER improves security by running the app with a non-root user.

📌 Example: 
   ```
         FROM node:18  
         RUN useradd -m myuser     # Create a new user, -m → Creates in home directory  
         USER myuser               # Switch to that user  “Don’t run as root → more secure 🔒 & 🚫 Avoids root risks”
   ```
---

## 🚪 EXPOSE
* 👉 EXPOSE = Documentation of container port
* EXPOSE tells Docker which port the application inside the container listens on at runtime.
* It does not actually open the port — it's just documentation

### 📌 EXPOSE → Just tells Docker which port is used inside the container.

📌 Example:
```
EXPOSE 3000         # App runs on port 3000, So we use EXPOSE 3000.  
EXPOSE 80 443       # Standard HTTP/HTTPS ports  
```
```
 docker run -p 8080:3000 my-app  
```
🔗 This maps:  
  * 8080 (on your computer "Host Port")
  * 3000 (inside the container "Container Port")

🌐 So you can access the app at `http://localhost:8080`

---

# 💾 VOLUME
 * 👉 VOLUME = Persistent storage
 * The VOLUME instruction is used to create a mount point inside the container where data can be stored outside the container, so it won't be lost when the container stops or is deleted.

📌 Example:
```
VOLUME /var/lib/mysql      # This tells Docker to store MySQL data outside the container.  

docker run -v mydata:/var/lib/mysql mysql:8               # Runtime command for volume bind

docker run -v /my/local/folder:/app/uploads my-image      # Bind to a local folder  
```
---

## ❤️ HEALTHCHECK
* HEALTHCHECK tells Docker how to check if the container is still working properly.
* It runs a command at intervals, and based on the result, Docker marks the container as healthy or unhealthy.
* 👉 HEALTHCHECK = Check container health

🔍 How to check health status: `docker inspect <container-id>`

📌 Example:
```
HEALTHCHECK --interval=30s --timeout=10s --retries=3 \  
  CMD curl -f http://localhost/ || exit 1  
```
💡 " Every 30 seconds, Docker runs the command. If the check fails 3 times, the container becomes unhealthy."

---

## 👨‍🔧 MAINTAINER
* MAINTAINER is used to specify the name and email of the person who maintains the Docker image, but now it's better to use LABEL maintainer=... instead.
* 👉 MAINTAINER is Deprecated instruction ; `LABEL` is flexible, Can store multiple metadata

📌 Example:
```
MAINTAINER Rahul Sharma <rahul@example.com>              # Not recommend  
LABEL maintainer="Rahul Sharma <rahul@example.com>"      # New Approach (Recommended)
```

- 💡 LABEL is more flexible and can store other metadata too.

---

## 🐚 SHELL
 * SHELL instruction is used to set the default shell for executing commands like RUN, CMD, and ENTRYPOINT in a Dockerfile.
 * 👉 SHELL = Change default shell to bash
 * 🔑 Use Case: Advanced scripting and Bash features

📌 Example:
```
SHELL ["/bin/bash", "-c"]      # “Use bash instead of sh”
```
### This changes the shell from the default /bin/sh to /bin/bash. Now all RUN commands after this will use Bash.

---

# 🛑 STOPSIGNAL
 * 👉 STOPSIGNAL = Signal to stop container
 *  STOPSIGNAL instruction sets the signal Docker will send to the container when stopping it.
 *  By default, Docker sends `SIGTERM` to stop a container. (🧹 Graceful shutdown & 🚫 Prevent data loss)

📌 Example:
```
STOPSIGNAL SIGINT      # Now, when the container is stopped, Docker sends SIGINT to the process.
```

💡 (SIGINT (Signal Interrupt) is the signal sent when you press Ctrl+C in a terminal.  
    It tells the process: "Stop what you're doing!")

---

## 🔥 Final Summary (Interview Ready)
### 🐳 Dockerfile Cheat Sheet
| 🧩 Instruction     | 💡 Description                                |
| ------------------  | --------------------------------------------- |
| 📄 Dockerfile      | 🏗️ Instructions to build an image            |
| ⚡ Cache           | 🚀 Speeds up builds using layer caching       |
| 🚫 `.dockerignore` | 🗑️ Skips unnecessary files from build        |
| 🧱 `FROM`          | 📦 Base image (starting point)                |
| ⚙️ `RUN`           | 🛠️ Executes commands during build            |
| 📁 `COPY`          | 📂 Copies files into image                    |
| 📦 `ADD`           | ➕ Like COPY + extra features (URLs, archives) |
| 📂 `WORKDIR`       | 📍 Sets working directory                     |
| 🎨 `CMD`           | ▶️ Default command at runtime                 |
| 🎯 `ENTRYPOINT`    | 🔒 Fixed main command                         |
| 🏷️ `LABEL`         | 📝 Adds metadata                              |
| 🌱 `ENV`           | 🌍 Runtime environment variables              |
| 🧪 `ARG`           | 🏗️ Build-time variables                      |
| 👤 `USER`          | 🔐 Runs container as specific user (non-root) |
| 🚪 `EXPOSE`        | 🌐 Documents container ports                  |
| 💾 `VOLUME`        | 📦 Persistent storage                         |
| ❤️ `HEALTHCHECK`   | 🩺 Checks container health                    |
| 👨‍🔧 `MAINTAINER`    | ⚠️ Deprecated → use LABEL                     |
| 🐚 `SHELL`         | 🔄 Change default shell (e.g., bash)          |
| 🛑 `STOPSIGNAL`    | 🧯 Graceful container stop signal             |
