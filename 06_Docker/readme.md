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

