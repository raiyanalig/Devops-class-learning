# 🚀 Docker Quick Revision Sheet (Exam Ready)

## 🔹 1. What is Docker?

* Docker is a platform to **build, run, and manage containers**
* Containers = lightweight, isolated environments

---

## 🔹 2. docker run

* Creates + starts a container from an image

docker run <image>

---

## 🔹 3. Port Mapping (-p)

* Maps host port to container port
* Needed to access apps from browser

docker run -p <HOST_PORT>:<CONTAINER_PORT> <image>

### Example:

docker run -p 8080:80 nginx

### Flow:

Browser → localhost:8080 → Docker Host → Container:80 → App

---

## 🔹 4. docker ps

* Shows **running containers only**

docker ps

---

## 🔹 5. docker ps -a

* Shows **all containers (running + stopped)**

docker ps -a

---

## 🔹 6. Remove Container

docker rm <container_id>

* Removes stopped container

### Force remove:

docker rm -f <container_id>

---

## 🔹 7. Remove Image

docker rmi <image_name>

### Example:

docker rmi nginx

---

## 🔹 8. Important Rules

* Cannot remove running container ❌
* Cannot remove image used by container ❌
* Containers are isolated by default

---

## 🔹 9. Key Concepts (1-line)

* Container → running instance of image
* Image → blueprint/template
* -p → connects container to outside world
* ps → list containers
* rm → remove container
* rmi → remove image

---

## 🔹 10. Memory Tricks

* ps = process list
* rm = remove container
* rmi = remove image
* -p = port mapping

---

# 🎯 Final Tip

👉 "No -p = No browser access"
👉 "Image → Container → Run → Access via port"
