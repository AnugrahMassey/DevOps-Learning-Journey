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


