# 🐳✨ What is Dockerfile ?
Dockerfile is a text file with a set of instructions (e.g., FROM, RUN, COPY, CMD) to build a Docker image. It tells Docker how to create an image step by step.

### ⚡ Docker Build Cache
  * 👉 Docker remembers previous steps
  * ⚡ Docker build cache means Docker remembers the steps from last time. If something didn't change, Docker skips ⏩ that step to save time.
     * 💡 Example: If I install packages and those packages didn't change, Docker will not install them again.

### 🚫 .dockerignore
  * 🚫 .dockerignore helps Docker skip unwanted files during image build. It makes the image smaller, builds faster
  * 👉 Works like .gitignore
  * 🎯 Purpose: 🚫 Exclude unwanted files, ⚡ Faster builds and 📦 Smaller images

 #### 📌 Example:
    ```
    node_modules/
    .git/
    *.log
    ---

## 🧱📦 FROM
  FROM indicates the base image for the container. It tells Docker what environment to start from, like Ubuntu, Alpine, or Python.
  ```
  👉 FROM ubuntu:20.04      # It's the first instruction in most Dockerfiles.
  ```
 * 🔥 Use smaller base images like alpine if you want lighter containers.
 * ⚠️ Always specify the tag (e.g., python:3.11) instead of latest image (🎯 Always use specific version (not latest))
 * 🔁 In multi-stage builds, we can use multiple FROM statements with different names.

📚 Common base images:
- ubuntu, alpine → for Linux environments
- node, python, golang → for language-specific environments

 🔁 Multi-stage Example:
  ```
  FROM node:18 AS builder
  FROM nginx:alpine
  ```

---

## ⚙️🛠️ RUN
* RUN executes commands inside the container during the build process and creates a new layer for each RUN statement.
* It's mostly used to install software or set up the environment inside the image.
* 👉 Executes commands during build time

📌 Example: Installing Packages
```
RUN apt-get update && \                         ✅ # Good (single layer)
    apt-get install -y package && \            🐧 # Debian/Ubuntu
    rm -rf /var/lib/apt/lists/*                🧹 # Clean Up After Installations
```

```
RUN yum install -y curl git && yum clean all          🧰 # CentOS/RHEL
```

```
RUN mkdir -p /usr/src/app \
    && cd /usr/src/app \                                     🔗 # Combine commands with && to minimize layers
    && git clone https://github.com/user/repo.git
```

```
RUN useradd -ms /bin/bash appuser && \
    chown -R appuser:appuser /app                           👤 # Setting Up Environment
```

* ❌ Leaves unnecessary files in image  → ✅   Solution:  Always `rm -rf /var/lib/apt/lists/*`  (after apt-get)
* 📦 Each RUN creates a new layer       → ✅   Solution:  Chain commands with `&&`

---

## 📁📥 COPY
 * The COPY instruction is used to copy files or folders from your local machine (host machine) into the Docker image during the build process. 
 * It's one of the most fundamental and frequently used Dockerfile command.

🧾 Syntax: COPY <source> <destination>
```
COPY . /app     # 👉 Copies files from local → image (📄 Copy code OR 📂 Copy folders)
```

🚫 .dockerignore filters which files are available to be copied during the build. Create a .dockerignore file to exclude unnecessary files  
- .git/
- node_modules/
- .log

### 📌 Examples:
```
COPY . /app                                        # Copy everything in current directory  
COPY app.py /app/                                    # Copying Single File  
COPY package.json package-lock.json /app/             # Copying Multiple Files # Good - explicit  
COPY src/ /app/src/                                    # Copying Directory  
COPY --chown=user:group files/ /app/                     # Set Proper File Permissions  
COPY --from=builder /src/dist /usr/share/nginx/html      # Copy from Multi-Stage Builds  
```
💡 # Better to Create Destination Directory first RUN mkdir -p /app   COPY file.txt /app/

"COPY is for simple file copying, while ADD has additional features like URL support and auto-extraction of archives."
* ⚡ Best Practices: Use .dockerignore & Copy only required files

---

# 📦➕ ADD
ADD is used to copy files/folders into the Docker image just like COPY, but it also has some extra features.

✨ Extra features of ADD:
- 📦 It can automatically extract .tar, .tar.gz, etc.  
- 🌐 It can download files from remote URLs (not recommended for security reasons)

```
ADD apps/ /app/                              # Copies apps from local to image's /app/  
ADD app.tar.gz /app/                         # extracting a .tar file  
ADD https://example.com/app.tar.gz /app/     # download from a URL  
```
✅ Best Practice:
"I prefer using COPY for most use cases because it's clearer and more secure. I use ADD only when I need to extract archives or work with remote URLs."  
- ADD follows .dockerignore rules same as COPY

---

# 📂📍 WORKDIR
 * WORKDIR sets the default folder inside the Docker image where commands will run (RUN, CMD, COPY, etc.).
 * 💬 It's like saying: "From now on, we'll work in this folder inside the image."
 * working directory inside container

👉 WORKDIR /path     # Sets current working directory in image to run commands (RUN, CMD, ENTRYPOINT, COPY, etc.)

🧾 Syntax:
```
WORKDIR /app      # WORKDIR /app creates (if needed) and switches to /app   (👉 All commands run inside /app)
COPY . .          # Copies to /app  
RUN npm install   # Runs in /app
```
---

## 🎨 CMD
* CMD is the default command that runs when the container starts. It's often used to start the main application inside the container.
* If does not run during the build — it runs when the container starts.
* Only one CMD is allowed → if there are multiple, only the last one will run.
* 🔄 Can overridden at runtime using `docker run <image> <new-command>`.

## 🌈 Examples
### 🚀 Running App:
```
 CMD ["python", "app.py"]      # means this will start your Python app.
 CMD ["node", "server.js"]     # mean This will start your Node.js app.
```

### ⚙️ If both ENTRYPOINT and CMD are used:
- ENTRYPOINT ["python"]
- CMD ["app.py"]

👉 It runs: `python app.py`

### 🌐 Starting Nginx Web Server:
```
 CMD ["nginx", "-g", "daemon off;"]  # nginx -g daemon off;     #⚠️ Without daemon off: the container would start and then immediately stop.
```

### 🧩 More Examples:
- CMD ["npm", "start"]    # Code form            # Good (exec form) 
- CMD npm start           # Avoid shell form

#### 🛠️ Important Notes
- 🔹 CMD executes at **RUNTIME**
- 🔹 RUN executes during **BUILD**

### 🔐 Make Commands Executable
```
- COPY start.sh .
- RUN chmod +x start.sh    # If using a script
- CMD ["./start.sh"]       # Must be executable
```

### 🔗 CMD with ENTRYPOINT
```
ENTRYPOINT ["python"]  
CMD ["app.py"]               # 👉 Can override: docker run <image> test.py
```
#### ⚖️ Behavior
- 🟢 Overridable → CMD → Yes (with docker run)  
- 🔴 ENTRYPOINT → No (without --entrypoint)

### 📌 Best Practice
 * You can write many RUN commands. They all get executed when building the image (in order, top to bottom).
 * If you write more than one CMD, Docker will ignore all except the last one. So it's best to write only one CMD.

---

## 🎨 ENTRYPOINT
 * ENTRYPOINT is used to set the 👉 main command that will always run when the container starts.
 * Unlike CMD, it's not overridden by default when you pass extra commands it will override (requires --entrypoint flag).
 * Only one ENTRYPOINT (last one). ENTRYPOINT Runs when container starts.

### 🌈 Example
```
- ENTRYPOINT ["python"]                # Good (exec form)
- docker run myscript node my-image    # overridden
```

## ⚙️ ENTRYPOINT + CMD
If you specify both ENTRYPOINT and CMD in the Dockerfile:
- ENTRYPOINT is the main command. CMD provides default arguments to that command.
### 📌 Example:
```
 ENTRYPOINT ["echo"]                
 CMD ["Hello"]                # CMD provides default arguments to ENTRYPOINT                   

# docker run <image>            → Hello
# docker run <image> Goodbye    → Goodbye  (Overridden Hello)
```

### 🧠 Final Concept
👉 CMD vs ENTRYPOINT → ENTRYPOINT runs first because it is the main command.

---

✨ *Docker CMD & ENTRYPOINT Made Easy!* ✨
