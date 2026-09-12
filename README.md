# 🐳 Docker Fundamentals

## 📌 Introduction

Docker is one of the most widely used technologies in modern **DevOps and Cloud environments**.

It provides a platform for packaging and running applications in lightweight, isolated environments called **Containers**.

Docker helps developers and DevOps engineers build, test, deploy, and manage applications consistently across different environments.

---

# 🐳 What is Docker?

**Docker** is an open-source containerization platform used to package applications and their dependencies into lightweight, portable containers.

Docker allows an application to run consistently across different environments such as:

- 💻 Developer Machine
- 🧪 Testing Environment
- ☁️ Cloud Environment
- 🚀 Production Environment

### Simple Definition

> Docker is a platform that packages applications and their dependencies into containers so they can run consistently anywhere.

---

# ❓ Why is Docker Used?

Docker is mainly used to simplify application deployment and maintain consistency between environments.

### Major Benefits

- 🚀 Faster Deployment
- 📦 Application Packaging
- 🔄 Environment Consistency
- 🔒 Application Isolation
- ☁️ Cloud Portability
- 📈 Easy Scalability
- 💻 Efficient Resource Usage
- 🔧 DevOps Automation
- 🔁 CI/CD Integration
- 🧪 Easy Testing

---

# 🖼️ What is a Docker Image?

A **Docker Image** is a read-only template or blueprint used to create Docker Containers.

An Image contains everything required to run an application, such as:

- 📁 Application Files
- 📦 Dependencies
- 📚 Libraries
- ⚙️ Runtime
- 🔧 Configuration
- 🖥️ Base Operating Environment

### Simple Concept

Docker Image → Blueprint → Docker Container

---

# 📦 What is a Docker Container?

A **Docker Container** is a running instance of a Docker Image.

When a Docker Image is started, Docker creates a Container that provides an isolated environment where the application can run.

### Simple Concept

Docker Image → Blueprint → Docker Container → Running Application

A container includes the application and everything it needs to run while providing an isolated runtime environment.

### Key Characteristics

- 📦 Lightweight
- ⚡ Fast Startup
- 🔒 Isolated Environment
- 🚀 Portable
- 🔄 Easy to Create and Remove
- 💻 Efficient Resource Usage

---

# ❓ Why are Containers Used?

Containers are used to run applications in **isolated, consistent, and portable environments**.

### Major Benefits

- 🚀 Fast Application Deployment
- 🔒 Application Isolation
- 📦 Consistent Environment
- 💻 Lightweight Compared to Virtual Machines
- 🔄 Easy Application Updates
- 📈 Easy Scaling
- 🧪 Simplifies Testing
- ☁️ Cloud Deployment
- 🔁 Supports CI/CD Pipelines
- 🛠️ Easy Application Management

### Without Containers

Developer Environment → Testing Environment → Production Environment

Different environments may have different configurations, dependencies, or versions.

### With Containers

Application + Dependencies → Docker Image → Container → Same Environment

This helps maintain consistency from development to production.

---

# 🔄 Docker Image vs Docker Container

| Docker Image 🖼️ | Docker Container 📦 |
|---|---|
| Blueprint of an application | Running instance of an image |
| Read-only template | Running environment |
| Used to create containers | Created from an image |
| Can be stored in a registry | Runs on a Docker host |
| Immutable application template | Has a writable container layer |

### Easy Way to Remember

> 🖼️ Image = Blueprint

> 📦 Container = Running Application

---

# 📝 What is a Dockerfile?

A **Dockerfile** is a text file that contains instructions used to build a Docker Image.

It defines how the application environment should be created.

### Example Dockerfile

    FROM nginx:alpine
    COPY . /usr/share/nginx/html/
    EXPOSE 80
    CMD ["nginx", "-g", "daemon off;"]

### Common Dockerfile Instructions

| Instruction | Purpose |
|---|---|
| FROM | Defines the base image |
| COPY | Copies files into the image |
| ADD | Adds files or directories |
| RUN | Executes commands while building the image |
| WORKDIR | Sets the working directory |
| EXPOSE | Documents the application port |
| ENV | Defines environment variables |
| CMD | Defines the default command |
| ENTRYPOINT | Defines the main executable |

---

# 🏗️ Basic Docker Workflow

Application Source Code → Dockerfile → docker build → Docker Image → docker run → Docker Container → Running Application

---

# 💻 Docker CMD Summary

## 🔹 Docker Information

    docker --version
    docker info
    docker help

## 🔹 Docker Images

    docker images
    docker pull nginx
    docker build -t myapp .
    docker rmi IMAGE_ID

## 🔹 Docker Containers

    docker ps
    docker ps -a
    docker run nginx
    docker run -d nginx
    docker stop CONTAINER_ID
    docker start CONTAINER_ID
    docker restart CONTAINER_ID
    docker rm CONTAINER_ID

## 🔹 Container Logs

    docker logs CONTAINER_ID
    docker logs -f CONTAINER_ID

## 🔹 Execute Commands Inside Container

    docker exec -it CONTAINER_ID /bin/bash

## 🔹 Container Details

    docker inspect CONTAINER_ID
    docker stats

## 🔹 Docker Networks

    docker network ls
    docker network create NETWORK_NAME
    docker network inspect NETWORK_NAME
    docker network rm NETWORK_NAME

## 🔹 Docker Volumes

    docker volume ls
    docker volume create VOLUME_NAME
    docker volume inspect VOLUME_NAME
    docker volume rm VOLUME_NAME

## 🔹 Docker Cleanup

    docker container prune
    docker image prune
    docker volume prune
    docker system prune

> ⚠️ Cleanup commands can remove unused Docker resources. Use them carefully.

---

# 🌐 Docker Port Mapping

Docker containers can expose application ports to the host machine.

### Example

    docker run -d -p 8080:80 nginx

### Port Mapping

Host Port 8080 → Container Port 80 → NGINX → Web Application

---

# 🌐 Docker Networking

Docker Networking allows containers to communicate with:

- 📦 Other Containers
- 💻 Host Machine
- 🌐 External Networks
- 🌍 Internet

### Common Network Types

- bridge
- host
- none
- overlay

### Basic Commands

    docker network ls
    docker network create mynetwork
    docker network inspect mynetwork

---

# 💾 Docker Volumes

Docker Volumes are used for **persistent data storage**.

Normally, data inside a container can be lost when the container is removed.

Volumes help store data outside the container lifecycle.

### Basic Commands

    docker volume create myvolume
    docker volume ls
    docker volume inspect myvolume

### Simple Concept

Container → Application Data → Docker Volume → Persistent Storage

---

# 🏗️ Docker Architecture

Docker Client → Docker Engine → Docker Images → Docker Containers → Running Applications

### Main Components

- 🧑‍💻 Docker Client
- ⚙️ Docker Engine
- 🖼️ Docker Images
- 📦 Docker Containers
- 🌐 Docker Networks
- 💾 Docker Volumes
- 📦 Container Registry

---

# 📦 Container Registry

A **Container Registry** is used to store and distribute Docker Images.

### Examples

- 🐳 Docker Hub
- ☁️ Amazon ECR
- 🐙 GitHub Container Registry

### Basic Workflow

Developer → Docker Build → Docker Image → Container Registry → Pull Image → Docker Container

---

# 🔐 Docker Security Best Practices

- 🔒 Do not store passwords or secrets inside images
- 🔑 Use environment variables or secret management
- 📦 Use trusted base images
- 🔍 Scan images for vulnerabilities
- 🔄 Keep images updated
- 👤 Avoid running containers as root when possible
- 📁 Use `.dockerignore`
- 🛡️ Limit container resources
- 📌 Prefer versioned or pinned image references
- 🔐 Follow least-privilege principles

---

# 🔁 Docker Lifecycle

Dockerfile → Build → Image → Create → Start → Running Container → Stop → Restart / Remove

---

# 🔧 Docker in DevOps

Docker plays an important role in the **DevOps lifecycle**.

Code → Build → Docker Image → Test → Scan → Container → Deploy → Production

Docker can be integrated with:

- 🔧 Git
- 🐙 GitHub
- 🔄 CI/CD
- ⚙️ Jenkins
- ☁️ AWS
- ☸️ Kubernetes
- 📦 Container Registries

---

# ☁️ Docker and Cloud

Docker containers can be deployed on cloud platforms such as:

- ☁️ AWS
- ☁️ Microsoft Azure
- ☁️ Google Cloud

In AWS environments, Docker can be used with services such as:

- Amazon EC2
- Amazon ECS
- Amazon EKS
- AWS Fargate
- Amazon ECR

---

# 🆚 Docker vs Virtual Machine

| Docker Container | Virtual Machine |
|---|---|
| Lightweight | Heavier |
| Starts quickly | Takes more time to start |
| Shares host OS kernel | Includes a full guest OS |
| Uses fewer resources | Uses more resources |
| Easy to scale | Comparatively slower to scale |
| Ideal for microservices | Useful for complete OS isolation |

---

# 🎯 Important Docker Concepts

Docker → Dockerfile → Build → Docker Image → Run → Docker Container → Application

### Remember

> 🐳 Docker = Platform

> 📝 Dockerfile = Instructions

> 🖼️ Image = Blueprint

> 📦 Container = Running Application

---

# 🎤 Docker Interview Questions

### 1. What is Docker?

Docker is a containerization platform used to package and run applications in isolated containers.

### 2. What is a Docker Image?

A Docker Image is a read-only blueprint used to create Docker Containers.

### 3. What is a Docker Container?

A Docker Container is a running instance of a Docker Image.

### 4. Why are containers used?

Containers provide isolation, portability, consistency, fast deployment, and efficient resource usage.

### 5. What is a Dockerfile?

A Dockerfile contains instructions used to build a Docker Image.

### 6. What is Docker Hub?

Docker Hub is a public container registry used to store and distribute Docker Images.

### 7. What is Docker Compose?

Docker Compose is a tool used to define and run multi-container applications using a YAML configuration file.

### 8. What is Docker Networking?

Docker Networking allows containers to communicate with each other, the host, and external networks.

### 9. What are Docker Volumes?

Docker Volumes provide persistent storage for container data.

### 10. What is the difference between Image and Container?

> **Image is a blueprint, while Container is a running instance of that image.**

---

# 🧠 Easy Docker Memory Trick

Docker → Dockerfile → Build → Image → Run → Container → Application

---

# 🎯 Key Takeaways

- 🐳 **Docker** is a containerization platform.
- 📝 **Dockerfile** contains instructions to build an image.
- 🖼️ **Docker Image** is a blueprint used to create containers.
- 📦 **Docker Container** is a running instance of an image.
- 🔒 Containers provide application isolation.
- 🚀 Containers make deployment faster and more consistent.
- 🌐 Docker Networking enables container communication.
- 💾 Docker Volumes provide persistent storage.
- 📦 Container Registries store and distribute images.
- 🔄 Docker is widely used in DevOps and CI/CD.
- ☁️ Docker can be used to deploy applications in cloud environments.

---

# 🏁 Conclusion

Docker has become an important technology in modern **DevOps and Cloud environments**.

It helps teams package applications and dependencies into portable containers, making applications easier to build, test, deploy, scale, and manage.

The core Docker concept can be remembered as:

Docker → Dockerfile → Docker Image → Docker Container → Running Application

> 🚀 **Docker helps DevOps engineers create consistent, portable, isolated, and efficient application environments.**

---

## 👨‍💻 Author

**Mohit Gadilohar**

🐳 Docker | ☁️ AWS | ⚙️ DevOps | 🚀 Cloud

> *Learning Docker and building practical DevOps skills.*
