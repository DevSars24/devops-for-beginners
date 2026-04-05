# 04: Key Concepts: Images, Containers, and Dockerfiles

After running pre-built images, the next step in your DevOps journey is to create your own images. This is where the **Dockerfile** comes in.

---

## 🖼️ What is a Docker Image?

A **Docker Image** is an immutable (unchangeable) read-only template that contains the application code, libraries, and dependencies. It’s like a "snapshot" of a system.

### 🌟 Image Layers
Images are built in layers. Every command in a Dockerfile adds a new layer.
1. **Base Layer**: Usually an OS like `ubuntu` or a language runtime like `python:3.9`.
2. **App Layer**: Your source code and configurations.
3. **Writable Layer**: When you run an image, Docker adds a thin, writable layer on top. This is the **Container**.

---

## 📝 Writing Your First Dockerfile

A **Dockerfile** is a simple text file with instructions on how to build your image.

### 🌟 Example: Containerizing a Node.js Application
Create a file named `Dockerfile` (no extension):

```dockerfile
# 1. Use an official base image
FROM node:18-alpine

# 2. Set the working directory inside the container
WORKDIR /app

# 3. Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# 4. Copy the rest of the application code
COPY . .

# 5. Expose the port the app runs on
EXPOSE 3000

# 6. Command to start the application
CMD ["npm", "start"]
```

---

## 🏗️ Building and Testing Your Image

Once the Dockerfile is ready, use the `docker build` command to create the image.

### 1. Build the Image
```bash
# -t: Give your image a "tag" (name:version)
docker build -t my-todo-app:v1.0 .
```

### 2. Run the Image as a Container
```bash
docker run -p 3000:3000 --name running-todo-app my-todo-app:v1.0
```

---

## 🎤 Interview Preparation: Cracking the Images

> [!IMPORTANT]
> **Q1: What is the difference between an Image and a Container?**
> *Answer: An **Image** is a static, read-only template that contains the application and its dependencies. A **Container** is a live, running instance of an image. You can think of an image as a "Class" in programming and a container as an "Object" (instance).*

> [!TIP]
> **Q2: Why should you put less frequently changed commands (like `npm install`) BEFORE the `COPY . .` command?**
> *Answer: This leverages **Docker Layer Caching**. Since `npm install` takes a long time, we only want to run it when our `package.json` changes. If we copy all our code first, every minor code change would invalidate the cache and force a slow re-install.*

---

## 📚 Next Steps
Now that you can build images, let's learn about **Module 05: Multi-Stage Builds & Optimization**.
