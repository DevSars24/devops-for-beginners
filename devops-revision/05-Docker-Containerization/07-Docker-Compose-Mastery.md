# 07: Docker Compose for Multi-Container Apps

In production, applications rarely exist as a single container. You typically have a **Frontend**, a **Backend**, and a **Database**. Manually running `docker run` for each is error-prone. **Docker Compose** is the solution.

---

## 🏗️ What is Docker Compose?

**Docker Compose** is a tool for defining and running multi-container Docker applications. You use a single **YAML file** (`docker-compose.yml`) to configure all your application's services.

### 🌟 Key Functions of Docker Compose
- **One Command**: Start/stop the entire stack with `docker compose up`.
- **Isolated Environments**: Creates a shared network automatically.
- **Service Management**: Restarts crashed containers and handles dependencies.

---

## 🛠️ Hands-on: Building a Multi-Service Application

Let's containerize a **Full-Stack Application** (Frontend + Backend + Database).

### 1. Structure the Project
```text
myapp/
├── frontend/ (Dockerfile)
├── backend/  (Dockerfile)
└── docker-compose.yml
```

### 2. Create the `docker-compose.yml`
```yaml
version: '3.8'

services:
  # 1. Database (PostgreSQL)
  db:
    image: postgres:15-alpine
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydb
    volumes:
      - db-data:/var/lib/postgresql/data

  # 2. Backend (Node.js API)
  backend:
    build: ./backend
    ports:
      - "5000:5000"
    depends_on:
      - db
    environment:
      DB_HOST: db
      DB_PORT: 5432

  # 3. Frontend (React)
  frontend:
    build: ./frontend
    ports:
      - "3000:3000"
    depends_on:
      - backend

volumes:
  db-data:
```

---

## 🚀 Running Your Stack

| Command | Action |
| :--- | :--- |
| **`docker compose up -d`** | Start all services in the background. |
| **`docker compose ps`** | Check the status of your entire stack. |
| **`docker compose logs -f`** | Follow the logs of all services at once. |
| **`docker compose down`** | Stop and remove all containers and networks. |
| **`docker compose build`** | Re-build images when you change the Dockerfiles. |

---

## 🎤 Interview Preparation: Cracking the Compose

> [!IMPORTANT]
> **Q1: What is the purpose of `depends_on` in a Docker Compose file?**
> *Answer: `depends_on` defines the **startup order** of services. In the example above, Docker will ensure that the `db` container starts *before* the `backend`. However, it doesn't wait for the database to be "ready"—you may still need a "wait-for-it" script in your application code.*

> [!TIP]
> **Q2: Why should you use `volumes` in your `docker-compose.yml` for databases?**
> *Answer: Containers are **ephemeral** (all data is lost when the container is deleted). By mapping a volume, you ensure that even if you `docker compose down`, your data remains safe on the host machine and is re-mounted the next time you start the stack.*

---

## 📚 Next Steps
Congratulations! You have mastered Docker. Now, let's learn how to scale these containers across a cluster in **Module 06: Kubernetes Orchestration**.
