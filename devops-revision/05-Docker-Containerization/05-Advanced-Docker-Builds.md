# 05: Multi-Stage Builds & Optimization

While a basic Dockerfile works, it often results in large, inefficient images containing unnecessary build tools (SDKs, compilers) that aren't needed in production. **Multi-Stage Builds** solve this problem.

---

## 🏗️ What is a Multi-Stage Build?

A **Multi-Stage Build** allows you to use multiple `FROM` statements in a single Dockerfile. You can use one stage to **compile/build** your app and another stage to **run** it using a much smaller base image.

### 🌟 Example: A Go or Node.js Application
In this example, we use a heavy "Build" image to compile the code and then copy only the final executable to a tiny "Production" image.

```dockerfile
# STAGE 1: Build Stage
FROM golang:1.20-alpine AS builder
WORKDIR /build
COPY . .
# Compile the application into a single binary named 'myapp'
RUN go build -o myapp main.go

# STAGE 2: Production Stage
FROM alpine:latest
WORKDIR /app
# Copy ONLY the binary from the builder stage
COPY --from=builder /build/myapp .
# Run the binary
CMD ["./myapp"]
```

**Result**:
- **Single Stage Image**: ~800 MB (includes Golang SDK, source code, etc.)
- **Multi-Stage Image**: ~15 MB (only includes the Alpine OS + the binary)

---

## 🐍 Practical Scenario: Containerizing a Python App

Python apps often have many dependencies. Here is how to keep them lean:

```dockerfile
FROM python:3.9-slim

WORKDIR /app
COPY requirements.txt .

# Install dependencies without keeping the cache to save space
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["python", "app.py"]
```

---

## ⚡ Image Optimization Techniques

1. **Use Small Base Images**: Prefer `alpine` or `slim` versions (e.g., `node:alpine` vs `node:latest`).
2. **Minimize Layers**: Combine multiple `RUN` commands into one using `&&` and `\`.
3. **Use `.dockerignore`**: Exclude `.git`, `node_modules`, `tests`, and `logs` to keep the build context small.
4. **Leverage Cache**: Always put `RUN npm install` or `pip install` before `COPY . .`.

---

## 🎤 Interview Preparation: Cracking the Optimization

> [!IMPORTANT]
> **Q1: Why are Multi-Stage builds considered a best practice for production images?**
> *Answer: They achieve two critical goals: **Security** and **Size**. By excluding build-time tools (like compilers, SSH keys, or source code) from the final image, you reduce the attack surface. By only including the binary or runtime, you reduce the image size, making it faster to pull and deploy.*

> [!TIP]
> **Q2: What is a "Dangling Image" and how do you clean it up?**
> *Answer: A dangling image is an image that is not tagged and is not used by any container. They are typically created when you Re-build an image with the same name. Use `docker image prune` to delete them.*

---

## 📚 Next Steps
Now that your images are optimized, let's learn how to connect them in **Module 06: Docker Networking**.
