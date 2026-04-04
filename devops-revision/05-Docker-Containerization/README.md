# 🐳 Module 05: Docker & Containerization

Docker revolutionized the way we build, ship, and run applications. It allows you to package an application with all its dependencies into a single, portable unit called a container.

## 🏗️ Key Docker Concepts
### 1. The "Big Three"
| Term | Description | Analogy |
| :--- | :--- | :--- |
| **Dockerfile** | Instructions to build an image. | The "Recipe." |
| **Image** | A read-only template for containers. | The "Packaged Dish." |
| **Container** | Running instance of an image. | The "Actual Meal" in a restaurant. |

---

## 🔑 Crucial Architectural Parts
- **Docker Client**: How we interact with Docker (CLI).
- **Docker Host (Engine)**: Daemon that manages images and containers.
- **Docker Registry (Docker Hub)**: Store and share images.
- **Volumes**: Persistent data storage (data remains after container deletion).
- **Networks**: Connectivity between containers.

---

## 🛠️ Most-Used Docker Commands
- `docker build -t my-app .`: Build an image.
- `docker run -d -p 8080:80 my-app`: Run a container in detached mode.
- `docker ps -a`: List all containers (active and inactive).
- `docker logs <container-id>`: View the logs of a container.
- `docker exec -it <container-id> bash`: Get inside a running container.
- `docker-compose up -d`: Orchestrate multiple containers simultaneously.

---

## ❓ Interview Questions
> [!IMPORTANT]
> **Q1: Explain the difference between a Virtual Machine (VM) and a Container.**
> *A: A VM includes a full "Guest OS" on top of the Hypervisor, making it heavy and slow to start. A container shares the "Host OS" kernel and isolates only the application and its dependencies, making it much lighter and faster.*

> [!TIP]
> **Q2: What is the Layer Caching in Docker?**
> *A: In a Dockerfile, each instruction (`FROM`, `RUN`, `COPY`) creates a new layer. Docker caches these layers. If an instruction (like `COPY . .`) changes, that layer and all subsequent ones are re-built, while the ones before are reused.*

---

## 📚 Resources
- [Docker Documentation](https://docs.docker.com/)
- [Docker for Beginners (FreeCodeCamp)](https://www.freecodecamp.org/news/the-docker-handbook/)
- [A Docker Tutorial for Beginners](https://docker-curriculum.com/)
- [Play with Docker (Interactive)](https://labs.play-with-docker.com/)
