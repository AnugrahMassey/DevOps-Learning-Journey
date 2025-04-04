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


# Week 6: Docker Advanced (Day 31-35)

Welcome to **Week 6**! This week focuses on advanced Docker concepts to deepen your containerization skills. We'll explore multi-container management, Docker Compose, container registries, networking, and volume management. By the end of this week, you'll be able to manage complex applications using Docker effectively.

---

## **🗓️ Day 31: Understanding Docker Compose**  
Docker Compose is a tool that helps you **define and run multi-container Docker applications** using a single YAML file. Instead of manually running multiple `docker run` commands, Compose automates this process.  

### **🔹 Why Use Docker Compose?**
- Simplifies multi-container management.
- Allows defining containers, networks, and volumes in one place.
- Easy to start and stop all services with `docker-compose up/down`.

### **🔹 Installing Docker Compose**
Most Docker installations include Compose by default. Check the version:
```bash
docker-compose --version
```
If not installed, use:
```bash
sudo apt install docker-compose -y   # Ubuntu/Debian
brew install docker-compose          # macOS
```

### **🔹 Basic Docker Compose YAML File**
```yaml
version: '3.8'

services:
  web:
    image: nginx
    ports:
      - "8080:80"

  db:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: rootpass
      MYSQL_DATABASE: testdb
      MYSQL_USER: user
      MYSQL_PASSWORD: password
```
- **Services:** Define multiple containers (`web` for Nginx, `db` for MySQL).
- **Ports:** Expose ports for communication.
- **Environment:** Pass environment variables.

### **🔹 Running the Multi-Container App**
```bash
docker-compose up -d
```
To stop:
```bash
docker-compose down
```

---

## **🗓️ Day 32: Defining Multi-Container Applications**  
Now, let’s build a real-world **multi-container setup** using **Docker Compose**.  

### **🔹 Example: WordPress + MySQL Setup**
```yaml
version: '3.8'

services:
  wordpress:
    image: wordpress
    ports:
      - "8080:80"
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: user
      WORDPRESS_DB_PASSWORD: password
      WORDPRESS_DB_NAME: wordpress

  db:
    image: mysql:5.7
    environment:
      MYSQL_DATABASE: wordpress
      MYSQL_USER: user
      MYSQL_PASSWORD: password
      MYSQL_ROOT_PASSWORD: rootpass
    volumes:
      - db_data:/var/lib/mysql

volumes:
  db_data:
```
- **WordPress container:** Serves the website.
- **MySQL container:** Stores the database.
- **Volumes:** Persist database data.

### **🔹 Running the Application**
```bash
docker-compose up -d
```
- Access **WordPress** at `http://localhost:8080`
- Stop all services:
```bash
docker-compose down
```

---

## **🗓️ Day 33: Docker Networking with Compose** 

**Docker Networking** is crucial for communication between services.

### **🔹 Default Networks in Docker Compose**
Docker Compose **automatically creates a network** so services can talk to each other by name (e.g., `db`, `wordpress`).  

### **🔹 Custom Networks in Docker Compose**
You can define custom networks like this:
```yaml
version: '3.8'

services:
  web:
    image: nginx
    networks:
      - frontend

  app:
    image: myapp
    networks:
      - frontend
      - backend

  db:
    image: postgres
    networks:
      - backend

networks:
  frontend:
  backend:
```
Here:
- `web` and `app` share the **frontend** network.
- `app` and `db` share the **backend** network.

### **🔹 Running and Inspecting Networks**
Run the stack:
```bash
docker-compose up -d
```
List networks:
```bash
docker network ls
```
Inspect a network:
```bash
docker network inspect backend
```

---

## **🗓️ Day 34: Docker Registries & Pushing Images**  

Docker Registries store and distribute Docker images. The most popular one is **Docker Hub**, but you can also use **private registries**.

### **🔹 Logging into Docker Hub**
```bash
docker login
```
### **🔹 Tagging and Pushing Images**
```bash
docker tag myapp:latest myusername/myapp:v1
docker push myusername/myapp:v1
```
To **pull** an image:
```bash
docker pull myusername/myapp:v1
```

### **🔹 Setting Up a Private Docker Registry**
Run a **local registry**:
```bash
docker run -d -p 5000:5000 --name registry registry:2
```
Tag and push:
```bash
docker tag myapp localhost:5000/myapp
docker push localhost:5000/myapp
```

---

## **🗓️ Day 35: Multi-Stage Builds for Optimization**  

Multi-stage builds **reduce image size** by keeping only necessary files.  

### **🔹 Example: Optimized Node.js App**
```dockerfile
# Stage 1 - Build
FROM node:14 AS builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

# Stage 2 - Run
FROM node:14
WORKDIR /app
COPY --from=builder /app/dist .
CMD ["node", "server.js"]
```
Here:
- First **builds** the app (`builder` stage).
- Second **runs** only the final output.

### **🔹 Benefits of Multi-Stage Builds**
✅ **Smaller Image Sizes**  
✅ **Faster Deployment**  
✅ **Better Security** (No unnecessary files)

Build and run:
```bash
docker build -t myapp .
docker run -p 3000:3000 myapp
```

---

## **📌 Week 6 Summary (Docker Advanced Recap)**  
| Day | Topic | Summary |
|----|--------|---------|
| **31** | Docker Compose Basics | Define multi-container applications with a YAML file. |
| **32** | Multi-Container Apps | WordPress + MySQL with Docker Compose. |
| **33** | Docker Networking | Custom networks for inter-container communication. |
| **34** | Docker Registries | Push and pull images from Docker Hub and private registries. |
| **35** | Multi-Stage Builds | Optimize image size and security using multi-stage builds. |

---

This concludes **Week 6: Docker Advanced**. You now have a strong foundation in **Docker Compose, Networking, Registries, and Multi-Stage Builds**. 🎯  

Next, we'll dive into **Week 7: Kubernetes Basics (Day 36-40)**. 🚀