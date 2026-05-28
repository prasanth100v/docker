## 🏷️ LABEL
 * LABEL is used to add metadata (`information`) to the Docker image, like the `author name`, `version`, or `description`.
 * It helps with documentation and image management. Can be viewed with docker inspect
 * 🧾 Syntax : LABEL `key="value" ` 

```hcl
LABEL stage="builder"                          # Single Label  
LABEL maintainer="dev@example.com"    
      version="1.0"                            # multiple labels  
      description="This is a sample image"
```

---

## 🌱 ENV
 * ENV is used to `set environment variables` in the Docker image. These variables are available `during build` and inside the running container.
```hcl
ENV PORT=8080  
ENV NODE_ENV=production \  
    PORT=3000 \              # Multiple Variables  
    APP_HOME=/app  
```
 * WORKDIR `$APP_HOME`
 * 🔄 `docker run -e PORT=`5000` my-app`     # Override ENV at runtime
 * 💡 Environment variables are `key-value pairs` used to store configuration settings. (`Config values available inside container`)
 * 💡 Use Cases:
     * App configs
     * Database URLs
     * Ports
 
### 🔑 Key Points: 🏗️ Available during `build + runtime` & 🔄 Can override at runtime
  
---

## 🧪 ARG
 * ARG is used to define `build-time variables`. You can pass values to it only while building `the image`, not when running the container.
 * 📌 Example:
 ```hcl
    FROM ubuntu  
    ARG APP_VERSION=1.0                               # 👉 ARG = Build-time variable
    RUN echo App version is $APP_VERSION  
  ```
 * docker build --build-arg `APP_VERSION=2.0` .     # This replaces APP_VERSION with `2.0` during build.

### ⚙️ Docker ARG vs ENV
| 🧩 Feature              | 🛠️ ARG | 🌍 ENV |
| ----------------------- | ------- | ------ |
| 🏗️ Available at build   | ✅ Yes   | ✅ Yes  |
| 🚀 Available at runtime | ❌ No    | ✅ Yes  |

 * 👉 ARG : Used during image build time only 🏗️ (Not available inside running container)
 * 👉 ENV : Available `during build + runtime` 🌍 (Used inside)

---

## 👤 USER
 * 👉 USER = Define which user runs container
 * USER sets the `Username` or `UID`. The USER instruction in a Dockerfile tells Docker `which user should run the application` and any commands.
 * By default, Docker containers `run as root`, but using USER `improves security` by running the app with a `non-root user`.
 * 📌 Example: 
   ```hcl
         FROM node:18  
         RUN useradd -m myuser     # Create a new user, -m → Creates in home directory  
         USER myuser               # Switch to that user  “Don’t run as root → more secure 🔒 & 🚫 Avoids root risks”
   ```
---

## 🚪 EXPOSE
 * 👉 EXPOSE = Documentation of container port
 * EXPOSE tells Docker `which port the application` inside the container listens on at runtime.
 * It does not actually open the port — `it's just documentation`
 * 📌 EXPOSE → Just tells Docker which port is used inside the container.

📌 Example:
```hcl
EXPOSE 3000         # App runs on port 3000, So we use EXPOSE 3000.  
EXPOSE 80 443       # Standard HTTP/HTTPS ports  
```
```hcl
 docker run -p 8080:3000 my-app  
```
* 🔗 This maps:  
  * 8080 (on your computer "Host Port")
  * 3000 (inside the container "Container Port")
* 🌐 So you can access the app at `http://localhost:8080`

---

# 💾 VOLUME
  * 👉 VOLUME = Persistent storage
  * The VOLUME instruction is used to create a `mount point` inside the container where data can be stored outside the container, so it won't be lost when the `container stops` or is deleted.
  * 📌 Example:
```hcl
VOLUME /var/lib/mysql      # This tells Docker to store MySQL data outside the container.  

docker run -v mydata:/var/lib/mysql mysql:8               # Runtime command for volume bind

docker run -v /my/local/folder:/app/uploads my-image      # Bind to a local folder  
```

---

## ❤️ HEALTHCHECK
 * HEALTHCHECK tells Docker how to check if the container is still working properly.
 * It runs a command at intervals, and based on the result, Docker marks the container as healthy or unhealthy.
 * 👉 HEALTHCHECK = Check container health
 * 🔍 How to check health status: `docker inspect <container-id>`

📌 Example:
```hcl
HEALTHCHECK --interval=30s --timeout=10s --retries=3 \  
  CMD curl -f http://localhost/ || exit 1  
```
 * 💡 " Every 30 seconds, Docker runs the command. If the check fails 3 times, the container becomes unhealthy."

---

## 👨‍🔧 MAINTAINER
 * MAINTAINER is used to specify the `name` and `email` of the person who maintains the Docker image, but now it's better to use LABEL maintainer=... instead.
 * 👉 MAINTAINER is Deprecated instruction ; `LABEL` is flexible, Can store multiple metadata..

📌 Example:
```hcl
MAINTAINER Rahul Sharma <rahul@example.com>              # Not recommend  
LABEL maintainer="Rahul Sharma <rahul@example.com>"      # New Approach (Recommended)
```
 * 💡 LABEL is `more flexible` and can store other metadata too.

---

## 🐚 SHELL
 * SHELL instruction is used to set the `default shell` for executing commands like `RUN, CMD, and ENTRYPOINT` in a Dockerfile.
 * 👉 SHELL = Change default shell to bash
 * 🔑 Use Case: Advanced scripting and Bash features

📌 Example:
```hcl
SHELL ["/bin/bash", "-c"]      # “Use bash instead of sh”
```
 * This changes the shell from the default `/bin/sh` to `/bin/bash`. Now all RUN commands after this will use Bash.

---

## 🛑 STOPSIGNAL
  * 👉 STOPSIGNAL = Signal to stop container
  *  STOPSIGNAL instruction sets the `signal Docker` will send to the container when stopping it.
  *  By default, Docker sends `SIGTERM` to stop a container. (🧹 Graceful shutdown & 🚫 Prevent data loss)
  * 📌 Example:
```hcl
STOPSIGNAL SIGINT      # Now, when the container is stopped, Docker sends SIGINT to the process.
```

 * 💡 (SIGINT (Signal Interrupt) is the signal sent when you press `Ctrl+C` in a terminal. It tells the process: "Stop what you're doing!")

---

## 🔥 Final Summary (Interview Ready)
### 🐳 Dockerfile Cheat Sheet
| 🧩 **Instruction**     | 💡 **Description**                 | 🧠 **Detailed Explanation**                      | 🚀 **Best Practice**              |
| ---------------------- | ---------------------------------- | ------------------------------------------------ | --------------------------------- |
| 📄 **Dockerfile**      | 🏗️ Instructions to build an image | Defines how Docker image is created step-by-step | Keep clean & version-controlled   |
| ⚡ **Cache**            | 🚀 Speeds up builds                | Docker reuses unchanged layers                   | Optimize layer order              |
| 🚫 **`.dockerignore`** | 🗑️ Excludes unnecessary files     | Prevents copying unwanted files into image       | Reduce image size                 |
| 🧱 **`FROM`**          | 📦 Base image                      | Starting point of image                          | Use minimal trusted images        |
| ⚙️ **`RUN`**           | 🛠️ Executes commands during build | Installs packages/configures image               | Combine commands to reduce layers |
| 📁 **`COPY`**          | 📂 Copies files into image         | Simple file copy                                 | Preferred over ADD                |
| 📦 **`ADD`**           | ➕ COPY + extra features            | Supports URLs & archive extraction               | Avoid unless needed               |
| 📂 **`WORKDIR`**       | 📍 Sets working directory          | Default path for next instructions               | Improves readability              |
| 🎨 **`CMD`**           | ▶️ Default runtime command         | Runs when container starts                       | Easily overridden                 |
| 🎯 **`ENTRYPOINT`**    | 🔒 Fixed startup command           | Defines main container executable                | Used for stable behavior          |
| 🏷️ **`LABEL`**        | 📝 Metadata                        | Adds image information                           | Store owner/version info          |
| 🌱 **`ENV`**           | 🌍 Runtime environment variables   | Sets persistent env vars                         | App configuration                 |
| 🧪 **`ARG`**           | 🏗️ Build-time variables           | Available only during build                      | Version customization             |
| 👤 **`USER`**          | 🔐 Run as specific user            | Avoid root execution                             | Security best practice            |
| 🚪 **`EXPOSE`**        | 🌐 Documents ports                 | Indicates container listening port               | Better documentation              |
| 💾 **`VOLUME`**        | 📦 Persistent storage              | External data persistence                        | Databases/uploads                 |
| ❤️ **`HEALTHCHECK`**   | 🩺 Container health monitoring     | Detect unhealthy containers                      | Kubernetes/Docker monitoring      |
| 👨‍🔧 **`MAINTAINER`** | ⚠️ Deprecated                      | Old metadata instruction                         | Use `LABEL` instead               |
| 🐚 **`SHELL`**         | 🔄 Change shell                    | Switch default shell (bash/sh)                   | Advanced scripting                |
| 🛑 **`STOPSIGNAL`**    | 🧯 Graceful shutdown               | Defines stop signal                              | Proper app termination            |
