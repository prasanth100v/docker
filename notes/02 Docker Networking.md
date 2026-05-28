# 🌐 Docker Networking 
## 🚀 What is Docker Networking?
 * ✨ Docker Networking = How containers talk to each other & the outside world
 * Docker Networking allows containers to communicate with:
   * Other containers 🔗
   * Host machine 🖥️
   * External systems 🌍  
 * 👉 It provides **isolation, security, and flexibility**

## 🧠 Types of Docker Networks
## 🟢 1. Bridge Network (Default) – Like Private Wi-Fi
  - Default network in Docker  
  - Containers can communicate **within the same bridge**  
  - 🚫 Not accessible outside unless port exposed (**port mapping**) 

### 🧪 Example:
```hcl
docker network create my_bridge

docker run -d --network=my_bridge --name=app nginx
docker run -d --network=my_bridge --name=db mysql
```
 * 👉 Now `app` can talk to `db` using container name  

### 🌍 Access from Outside :
```hcl
docker run -d -p 8080:80 nginx          # Port 8080 on the host maps to port 80 in the container
```
 * 👉 Access: `http://localhost:8080  `

### 🎯 Interview Tips:
 - Uses **NAT (Network Address Translation)**  
 - Each container gets **internal IP**  
 - Best for **single-host applications**

## 🔵 2. Host Network – Like Direct Internet Connection
   * host mode makes a container use the hosts network.
   * 📌 Key Points:
     * No network isolation  (📡 `Same IP as host machine`)
     * Container uses **host IP directly**
     * No port mapping needed  

### 🧪 Example:
```hcl
docker run -d --network=host nginx
```
* 👉 Access directly: `http://localhost:80`
* If Nginx listens on port `80`, it will be accessible at `http://localhost:80` on the host.

### 🎯 Interview Tips:
  - Faster performance ⚡ (`no NAT`)  
  - Port conflicts possible ❗  
  - Not supported on Docker Desktop (`Mac/Windows`)

## 🟣 3. Overlay Network – Multi-Host Communication
### 📌 Key Points:
 - Used in **Docker Swarm**  
 - Connects containers across multiple servers  
 - Secure communication using **VXLAN**  

## 🟡 4. Macvlan Network – “Real Device on Network”
### 📌 Key Points:
 * Each container gets **unique IP & MAC** 🆔 like a real computer.
 * Appears as a real device on network  (🖥️ Acts like `physical device`)
 * 🎯 Use Cases:
   * Legacy apps requiring direct network access
   * Network monitoring tools  
 * Example:
   * Container gets IP like:` 192.168.1.10` (Other systems can access it directly)


## ⚫ 5. None Network – Airplane Mode
### 📌 Key Points:
 - No network access ❌  (No internet)
 - 🔒 Fully isolated container
 - ❌ No container communication

### 🧪 Example:
```hcl
docker run -d --network=none nginx        # 👉 Container cannot communicate with anything  
```
### 🎯 Interview Tips:
 - Used for **high-security workloads**  
 - Manual networking can be configured later  

---

## 🌐 Common Docker Networking Commands
| 🧩 Command                  | 📌 Purpose      | 💡 Description                            |
| --------------------------- | --------------- | ----------------------------------------- |
| 📋 `docker network ls`      | List networks   | 🔍 Shows all available Docker networks    |
| 🔍 `docker network inspect` | Inspect network | 📊 Displays detailed info about a network |
| ➕ `docker network create`   | Create network  | 🌐 Creates a new custom network           |
| ❌ `docker network rm`       | Remove network  | 🗑️ Deletes a Docker network              |

---

# 💡 Important Interview Questions & Answers
### ❓ How do containers communicate in bridge network?
  * 👉 Using **container names as DNS**

### ❓ What is port mapping?
  * 👉 Mapping host port to container port using `-p`

### ❓ Difference between bridge and host?
   - Bridge → isolated + NAT
   - Host → no isolation + faster  

### ❓ When to use overlay network?
  * 👉 In **multi-host / swarm environments**

### ❓ How to secure container networking?
   - Use custom networks  
   - Avoid exposing unnecessary ports  
   - Use firewalls & security groups  

✨ *Master Docker Networking for DevOps Interviews!* ✨
