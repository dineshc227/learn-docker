# 🐳 DOCKER – DAY 2 (Hands-On Foundations)

## Topic Coverage:

1. Networking basics (IP + Port + Accessing applications)
2. Docker Architecture
3. Installing Docker Desktop
4. Docker CLI introduction
5. Using public images
6. Running first container
7. Accessing application via browser
8. Basic Docker commands

---

# 🎯 Day-2 Learning Objectives

By the end of this class, students will be able to:

✅ Understand IP and Port mapping
✅ Explain Docker architecture
✅ Install Docker Desktop correctly
✅ Use Docker CLI
✅ Pull public images
✅ Run containers
✅ Access containerized applications in browser
✅ Understand Image → Container relationship practically

---

# 1️⃣ Pre-Requisite Concepts — IP Address & Port (VERY IMPORTANT)

Before Docker commands, students must understand **how applications are accessed**.

---

## What is an IP Address?

### Definition:

> **An IP address is a unique address used to identify a machine in a network.**

Examples:

```
192.168.1.10
10.0.0.5
127.0.0.1
```

---

### Types You Should Explain:

---

### Public IP:

* Used on internet
* Accessible globally

---

### Private IP:

* Used inside networks
* Example:

```
192.168.x.x
10.x.x.x
```

---

### Localhost (127.0.0.1):

> Means: **This same machine**

When you access:

```
http://localhost
```

You are accessing your own computer.

---

## What is a Port?

### Definition:

> **A port is a logical number used to identify a specific application running on a machine.**

---

### Example:

| Application | Port |
| ----------- | ---- |
| HTTP        | 80   |
| HTTPS       | 443  |
| MySQL       | 3306 |
| SSH         | 22   |
| Nginx       | 80   |

---

## Why Ports Are Needed?

One IP can run multiple applications.

Ports help OS decide:

👉 Which app should receive traffic.

---

## How Browser Access Works

When you type:

```
http://localhost:8080
```

It means:

```
localhost → Your machine
8080 → Application port
```

---

## Real World Analogy

### IP = Building Address

### Port = Flat Number

---

## Important Line To Say:

> IP identifies the machine, Port identifies the application.


# 2️⃣ Installing Docker Desktop (Windows)

Now that students understand **how applications are accessed**, move to Docker installation.

---

## What is Docker Desktop?

> Docker Desktop is an application that installs Docker Engine and Docker CLI on Windows/Mac.

---

## System Requirements

Tell students:

✔ Windows 10 / 11 (64-bit)
✔ Virtualization enabled
✔ Minimum 8GB RAM recommended

---

## Step 1: Download Docker Desktop

Open browser:

👉 [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)

Click:

```
Download for Windows
```

---

## Step 2: Install Docker Desktop

Run installer.

During installation:

✔ Enable WSL2
✔ Use recommended settings

Click:

```
Install
```

---

## Step 3: Restart System

Restart is mandatory.

---

## Step 4: Start Docker Desktop

After reboot:

Open Docker Desktop.

Wait until:

✅ Docker Engine is running
(Green indicator)

---

## Step 5: Verify Installation

Open terminal (PowerShell / CMD):

Run:

```bash
docker --version
```

Expected:

```
Docker version xx.x.x
```

---

## Verify Engine Running

```bash
docker info
```

No error = Docker working.

---

# 3️⃣ Running First Docker Container (Hands-On First)
---

> We are NOT creating our own image now.
> Someone has already created an image and uploaded it to the internet.
> We will download it and run it.

---

# Pulling Public Image (Nginx)

---

## Step 1: Download Image

Run:

```bash
docker pull nginx
```

Explain:

✔ Image downloaded from internet
✔ Stored locally
✔ Application is NOT running yet

---

## Verify Image Downloaded

Run:

```bash
docker images
```

Explain output:

* Repository = image name
* Tag = version
* Image ID
* Size

---

Tell students:

> Image is just a package/template.
> It does not run automatically.

---

# 4️⃣ Running Container From Image

Now convert **image → container**

---

## Run Container

```bash
docker run -d -p 8080:80 nginx
```

---

## Explain Command Slowly

| Part   | Meaning                           |
| ------ | --------------------------------- |
| docker | Docker command                    |
| run    | Create + start container          |
| -d     | Run in background                 |
| -p     | Port mapping                      |
| 8080   | Host machine port                 |
| 80     | Application port inside container |
| nginx  | Image name                        |

---

## Explain Port Mapping

Say:

```
Your Laptop Port 8080 → Container Port 80
```

Browser request:

```
localhost:8080
```

is forwarded to:

```
nginx inside container
```

---

# 5️⃣ Access Application In Browser

Open browser:

```
http://localhost:8080
```

Students will see:

👉 Nginx Welcome Page

---

Explain:

> We did not install Nginx on Windows.
> Nginx is running inside container.

---

# 6️⃣ Verify Running Container

Run:

```bash
docker ps
```

Explain columns:

✔ Container ID
✔ Image used
✔ Status
✔ Port mapping

---

# 7️⃣ Basic Docker Commands (Containers + Images)


---

## Show All Containers

```bash
docker ps -a
```

Shows:

✔ Running
✔ Stopped containers

---

## Stop Container

```bash
docker stop <container-id>
```

Explain:

Container stopped but not deleted.

---

## Start Container Again

```bash
docker start <container-id>
```

---

## Remove Container

```bash
docker rm <container-id>
```

Explain:

Deletes container instance.

---

## Remove Image

```bash
docker rmi nginx
```

Explain:

Deletes downloaded image.

---

# 8️⃣ Important Concept Reinforcement


---

### Image:

* Template
* Downloaded from internet
* Read-only

---

### Container:

* Running instance
* Uses CPU & RAM
* Created from image

---

Example:

> One nginx image → multiple containers.

---

# 9️⃣ Now Introduce Docker Architecture (After Hands-On)



---

## Docker Architecture Components

```
Docker CLI → Docker Engine → Docker Registry
```

---

### Docker CLI

What students used:

```bash
docker run
docker pull
docker ps
```

CLI only sends commands.

---

### Docker Engine

Engine:

✔ Pulled nginx image
✔ Created container
✔ Started application
✔ Managed ports

---

### Docker Registry

Registry:

✔ Stored nginx image
✔ Provided it when we pulled

Example:

Docker Hub.

---

## Architecture Flow Using Today’s Demo

When we ran:

```bash
docker run nginx
```

What happened:

1. CLI sent command
2. Engine checked local images
3. Engine pulled from registry
4. Engine created container
5. Application started

---

# 🔚 Day-2 Final Summary (Tell Students)

Students should remember:

✔ IP + Port = Application access
✔ Docker Desktop installs Docker Engine
✔ Public images exist
✔ Image is template
✔ Container is running app
✔ Port mapping exposes container apps
✔ Docker uses CLI, Engine, Registry

---

# 📝 Homework

---

### Task 1:

Run redis:

```bash
docker run redis
```

---

### Task 2:

Run nginx on different port:

```bash
docker run -d -p 9090:80 nginx
```

---
