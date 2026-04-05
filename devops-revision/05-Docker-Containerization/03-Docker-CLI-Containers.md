# 03: Running Your First Container & Essential CLI Commands

Now that Docker is installed, it's time to get hands-on. This guide focuses on the most common commands you will use daily as a DevOps engineer.

---

## 🚀 Running Your First Container

To run a container, use the `docker run` command. Docker will look for the image locally; if it doesn't find it, it will download it from **Docker Hub**.

### 🔌 Basic Syntax
```bash
docker run <options> <image_name> <command>
```

### 🌟 Running Nginx (Web Server)
```bash
# -d: Run in "Detached" mode (background)
# -p: Map local port 8080 to container port 80
# --name: Give your container a friendly name
docker run -d -p 8080:80 --name my-web-server nginx
```

**Verify**: Open your browser and go to `localhost:8080`. You should see the "Welcome to nginx!" message.

---

## 🛠️ Essential Docker CLI Commands (Cheat Sheet)

| Command | Action | Explanation |
| :--- | :--- | :--- |
| **`docker ps`** | List Containers | Shows running containers. Add `-a` to see all (including stopped). |
| **`docker pull <image>`** | Download Image | Pulls an image from Docker Hub without running it. |
| **`docker stop <id>`** | Stop Container | Gracefully shuts down a running container. |
| **`docker start <id>`** | Start Container | Restarts a previously stopped container. |
| **`docker rm <id>`** | Remove Container | Deletes a stopped container. Use `-f` to force delete a running one. |
| **`docker rmi <id>`** | Remove Image | Deletes a local image to save disk space. |
| **`docker logs <id>`** | View Logs | Sees the standard output (stdout) of a container. Vital for debugging! |
| **`docker exec -it <id> sh`** | Access Shell | Jumps into a running container's terminal (for inspection). |
| **`docker inspect <id>`** | View Details | Shows low-level JSON metadata (IP address, mounts, etc.). |
| **`docker stats`** | Monitor Resources | Displays live CPU and memory usage for all containers. |

---

## 💾 Managing the Lifecycle of a Container

A container goes through several states during its life:
1. **Created**: Use `docker create`.
2. **Running**: Use `docker run` or `docker start`.
3. **Paused**: Use `docker pause`.
4. **Stopped**: Use `docker stop` or when the internal process finishes.
5. **Deleted**: Use `docker rm`.

---

## 🎤 Interview Preparation: Cracking the Commands

> [!IMPORTANT]
> **Q1: What is the difference between `docker run` and `docker start`?**
> *Answer: `docker run` is used to create and start a **new** container from an image. `docker start` is used to restart an **existing**, stopped container that was created previously.*

> [!TIP]
> **Q2: How do you access a running container's shell to debug it?**
> *Answer: Use the command `docker exec -it <container_id> /bin/bash` (or `/bin/sh`). The `-it` flag stands for **interactive** and **pseudo-TTY**, allowing you to interact with the container's terminal.*

---

## 📚 Next Steps
Now that you can manage containers, let's learn how to **Module 04: Build Your Own Images with Dockerfiles**.
