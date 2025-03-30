# Week 5: Docker Basics (Days 26-30)

Welcome to **Week 5** of your DevOps journey! This week focuses on Docker, a critical containerization platform that allows you to package, distribute, and run applications in isolated environments. By the end of this week, you will have a solid understanding of Docker fundamentals, including containers, images, Dockerfiles, volumes, and networking.

---

## ✅ **Day 26: Introduction to Docker**

### What is Docker?
- Docker is a containerization platform that packages applications and all dependencies into a container.
- Containers are lightweight, portable, and ensure consistency across multiple environments (dev, test, prod).

### Key Concepts
- **Containers**: Isolated environments that run your application.
- **Images**: Templates used to create containers.
- **Dockerfile**: A script that contains instructions to build an image.
- **Volumes**: Persistent data storage for containers.
- **Docker Hub**: A repository for sharing container images.

### Installation
- Install Docker from the official [Docker website](https://docs.docker.com/get-docker/) for your OS (Linux, macOS, Windows).
- Verify installation:
  ```bash
  docker --version
  ```
- Start Docker service:
  ```bash
  sudo systemctl start docker
  ```

---

## ✅ **Day 27: Working with Docker Images and Containers**

### Pulling Docker Images
- Docker Hub contains thousands of prebuilt images.
  ```bash
  docker pull nginx
  ```

### Running a Container
- Start a container using the image:
  ```bash
  docker run -d -p 80:80 nginx
  ```
- Explanation:
  - `-d`: Detached mode (runs in the background)
  - `-p 80:80`: Maps port 80 of the container to port 80 on the host

### Listing and Managing Containers
- List running containers:
  ```bash
  docker ps
  ```
- List all containers (including stopped ones):
  ```bash
  docker ps -a
  ```
- Stop a container:
  ```bash
  docker stop <container_id>
  ```
- Remove a container:
  ```bash
  docker rm <container_id>
  ```

---

## ✅ **Day 28: Dockerfile and Building Images**

### What is a Dockerfile?
- A Dockerfile is a script that contains a series of instructions to build a Docker image.
- Example Dockerfile for a simple Python app:
  ```dockerfile
  # Use official Python image
  FROM python:3.12-slim

  # Set working directory
  WORKDIR /app

  # Copy files
  COPY . /app

  # Install dependencies
  RUN pip install -r requirements.txt

  # Run the app
  CMD ["python", "app.py"]
  ```

### Building an Image
- Run the following command to build an image:
  ```bash
  docker build -t my-python-app .
  ```
- Explanation:
  - `-t`: Tag the image with a name

### Running the Built Image
- Start a container from the custom image:
  ```bash
  docker run -d -p 5000:5000 my-python-app
  ```

---

## ✅ **Day 29: Docker Volumes and Data Management**

### What are Docker Volumes?
- Docker volumes are used to store persistent data.
- Containers are ephemeral, meaning data inside them is lost when they stop. Volumes ensure data persists across container restarts.

### Creating and Using Volumes
- Create a volume:
  ```bash
  docker volume create my-volume
  ```
- Use the volume with a container:
  ```bash
  docker run -d -v my-volume:/app/data nginx
  ```
- Explanation:
  - `-v`: Mounts the volume to the container's `/app/data` directory

### Managing Volumes
- List volumes:
  ```bash
  docker volume ls
  ```
- Inspect a volume:
  ```bash
  docker volume inspect my-volume
  ```
- Remove a volume:
  ```bash
  docker volume rm my-volume
  ```

---

## ✅ **Day 30: Docker Networking**

### Docker Networking Concepts
- Docker uses networks to allow containers to communicate.
- Three main types of networks:
  - **Bridge**: Default network for containers on the same host.
  - **Host**: Container uses the host's network directly.
  - **None**: No network connection.

### Creating a Network
- Create a custom network:
  ```bash
  docker network create my-network
  ```

### Connecting Containers to Networks
- Run a container in a specific network:
  ```bash
  docker run -d --network my-network nginx
  ```
- List networks:
  ```bash
  docker network ls
  ```
- Inspect a network:
  ```bash
  docker network inspect my-network
  ```

### Container Communication
- Containers on the same network can communicate using container names.
- Example:
  ```bash
  docker run -d --name web --network my-network nginx
  docker run -it --network my-network alpine sh
  ping web
  ```

---

## 📌 **Weekly Summary**

This week, you learned the foundational concepts of Docker. Here’s a recap:

- **Day 26:** Introduction to Docker, containers, images, and installation.
- **Day 27:** Working with Docker images and containers.
- **Day 28:** Building custom Docker images using Dockerfiles.
- **Day 29:** Managing persistent data using Docker volumes.
- **Day 30:** Networking containers using Docker networks.

By now, you should be comfortable running containers, building images, managing data with volumes, and setting up container networks.

**Next Week:** You'll explore advanced Docker topics like Docker Compose and container orchestration!

---

**Keep practicing and happy learning! 🚀**


