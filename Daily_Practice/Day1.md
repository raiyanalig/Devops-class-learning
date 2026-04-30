# Docker Basic Commands Notes (Basic → Container Management)

Each command has:
- short explanation
- simple example

---

# 1. Check Docker Installation

## docker --version

Shows the installed Docker version.

Explanation:
- Used to verify Docker is installed correctly.
- Displays the Docker Engine version.

Example:

```bash
docker --version
```

Example Output:

```
Docker version 26.x.x
```

---

# 2. View Docker System Information

## docker info

Displays detailed information about the Docker system.

Explanation:
- Shows number of containers, images, storage driver and system configuration.
- Useful for debugging Docker setup.

Example:

```bash
docker info
```

---

# 3. List Docker Images

## docker images

Shows all Docker images stored locally.

Explanation:
- Displays repository name, tag, image ID and size.
- Used to check available images before creating containers.

Example:

```bash
docker images
```

Example Output:

```
REPOSITORY   TAG       IMAGE ID       SIZE
httpd        latest    abcd1234       145MB
ubuntu       latest    efgh5678       77MB
```

---

# 4. Download an Image

## docker pull httpd

Downloads an image from Docker Hub.

Explanation:
- Retrieves the image from the remote Docker registry.
- Stores it locally on your system.

Example:

```bash
docker pull httpd
```

---

# 5. Create and Run Container

## docker run httpd

Creates and starts a container using the specified image.

Explanation:
- If the image is not present locally, Docker automatically downloads it.
- Container starts immediately.

Example:

```bash
docker run httpd
```

---

# 6. Run Container with Name

## docker run --name First_container httpd

Creates a container with a custom name.

Explanation:
- Makes container identification easier.
- Otherwise Docker assigns a random name.

Example:

```bash
docker run --name First_container httpd
```

---

# 7. Run Container in Detached Mode

## docker run -d httpd

Runs the container in background.

Explanation:
- `-d` stands for detached mode.
- Container runs in background while terminal remains free.

Example:

```bash
docker run -d httpd
```

---

# 8. Interactive Mode (Iterative Mode)

## docker run -it ubuntu bash

Runs container with terminal interaction.

Explanation:
- `-i` keeps standard input open.
- `-t` allocates a terminal.
- Used to interact with container shell.

Example:

```bash
docker run -it ubuntu bash
```

This opens a bash shell inside the container.

---

# Difference Between Detached Mode and Interactive Mode in Docker

## Detached Mode (-d)

- Runs the container in the **background**.
- The **terminal becomes free immediately** after starting the container.
- Mostly used for running **services like web servers, databases, or APIs**.
- Docker returns a **container ID** after starting the container.
- You **cannot directly interact with the container terminal**.

Example command:

docker run -d httpd

Explanation:  
Starts the **httpd (Apache web server) container in background mode**.

---

## Interactive Mode (-it)

- Runs the container with an **interactive terminal**.
- The **terminal remains attached** to the container.
- Allows the user to **execute commands inside the container**.
- Mainly used for **testing, debugging, or exploring containers**.
- Uses two options:
  - **-i** → keeps input open
  - **-t** → allocates a terminal

Example command:

docker run -it ubuntu bash

Explanation:  
Starts an **Ubuntu container and opens a bash shell inside it**, allowing the user to interact with the container.
---

# 9. List Running Containers

## docker ps

Displays currently running containers.

Explanation:
- Shows container ID, image name, status and container name.

Example:

```bash
docker ps
```

---

# 10. List All Containers

## docker ps -a

Displays all containers (running + stopped).

Explanation:
- Shows the complete container list.

Example:

```bash
docker ps -a
```

---

# 11. docker container ls

Lists running containers.

Explanation:
- Similar to `docker ps`.
- Uses Docker’s newer command structure.

Example:

```bash
docker container ls
```

---

# Difference: docker ps vs docker container ls

| Command | Meaning |
|------|------|
| docker ps | Old command |
| docker container ls | New Docker CLI format |

Both show running containers.

---

# 12. Start a Container

## docker start container_name

Starts an existing stopped container.

Explanation:
- Used to restart previously created containers.
- Does not create a new container.

Example:

```bash
docker start First_container
```

---

# 13. Stop a Container

## docker stop container_name

Stops a running container.

Explanation:
- Gracefully stops container execution.

Example:

```bash
docker stop First_container
```

---

# 14. Restart Container

## docker restart container_name

Restarts a container.

Explanation:
- Stops the container and starts it again.

Example:

```bash
docker restart First_container
```

---

# 15. Remove Container

## docker rm container_name

Deletes a stopped container.

Explanation:
- Container must be stopped before removing.

Example:

```bash
docker rm First_container
```

---

# 16. Remove Image

## docker rmi image_name

Deletes an image from local system.

Explanation:
- Frees storage space.

Example:

```bash
docker rmi httpd
```

---

# 17. View Container Logs

## docker logs container_name

Shows logs generated by the container.

Explanation:
- Used for debugging applications.

Example:

```bash
docker logs First_container
```

---

# 18. Execute Command Inside Container

## docker exec -it container_name bash

Runs commands inside a running container.

Explanation:
- Used to access container terminal after it starts.

Example:

```bash
docker exec -it First_container bash
```

---

# Typical Docker Workflow

```
docker --version
docker pull httpd
docker images
docker run -d --name First_container httpd
docker ps
docker stop First_container
docker start First_container
docker rm First_container
```

---

# Quick Command Summary

| Command | Purpose |
|------|------|
| docker pull | Download image |
| docker images | List images |
| docker run | Create and start container |
| docker ps | Show running containers |
| docker ps -a | Show all containers |
| docker container ls | List running containers |
| docker start | Start container |
| docker stop | Stop container |
| docker rm | Remove container |
| docker rmi | Remove image |

---