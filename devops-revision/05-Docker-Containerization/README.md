# 🐳 Module 05: Docker & Containerization

      - "80:80"
  database:
    image: "postgres:alpine"
    environment:
      POSTGRES_PASSWORD: "securepassword"
```

---

## 💾 Storage and Networking
1. **Volumes**: Persistent storage. Since containers are ephemeral (they disappear when deleted), volumes ensure that your data (like database records) persists.
2. **Networking**: Allows containers to communicate with each other and the outside world. The default "Bridge" network is standard for local multi-container communication.

---

## ❓ Interview Preparation (Mastering the Discussion)

> [!IMPORTANT]
> **Q1: What is a Dockerfile?**
> *Answer: A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. It serves as the "recipe" for your container (e.g., `FROM node:18`, `COPY . .`, `RUN npm install`).*

> [!TIP]
> **Q2: How do you optimize a Docker image for production?**
> *Answer: 1. Use **Multi-stage builds** to keep the final image small. 2. Use **Alpine** or "distroless" base images. 3. Use `.dockerignore` to exclude unnecessary files like `node_modules` or `.git`.*

---

## 📚 Resources
- [Docker Documentation](https://docs.docker.com/) — The official source of truth.
- [Play with Docker](https://labs.play-with-docker.com/) — A free, browser-based lab.
- [Docker Best Practices for Production](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- [The Docker Handbook by FreeCodeCamp](https://www.freecodecamp.org/news/the-docker-handbook/)
