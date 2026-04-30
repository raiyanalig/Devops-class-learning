## 1. Why Docker Containers are Lightweight

Docker containers are **lightweight** compared to virtual machines because of the following reasons:

### 1. Shared Host OS Kernel
Containers share the **host operating system kernel** instead of running their own separate OS.  
This eliminates the need to install a full guest OS for each application.

Architecture:

Hardware  
↓  
Host Operating System  
↓  
Docker Engine  
↓  
Containers (share the same kernel)

Because of this:
- Less memory usage
- Faster startup time
- Lower resource consumption

---

### 2. No Guest Operating System
In traditional virtualization (Virtual Machines), each VM contains:
- Full operating system
- Kernel
- System libraries
- Application

This increases memory and storage usage.

Containers include only:
- Application
- Required dependencies

Therefore containers are much **lighter and faster** than virtual machines.

---

### 3. Layered Image System
Docker images are built using **layers**.

Example:

Base Image (Ubuntu)  
↓  
Runtime Layer (Python / Node.js)  
↓  
Application Layer  

If multiple containers use the **same base image**, Docker stores that layer **only once** and reuses it.

Benefits:
- Saves disk space
- Faster image builds
- Efficient container management

---

### 4. Process-Level Isolation
Containers isolate applications using Linux kernel features:

**Namespaces**
- Provide isolation for processes, networking, users, and file systems.

**Control Groups (cgroups)**
- Limit and manage resource usage such as CPU, memory, and disk.

These mechanisms allow multiple containers to run independently **without requiring separate operating systems**.

---

### Summary
Docker containers are lightweight because they:

- Share the host OS kernel
- Do not include a separate guest operating system
- Reuse shared image layers
- Use namespaces and cgroups for process isolation

This results in **low resource usage, fast startup time, and efficient system utilization**.

---

# 2. Docker Build Flow

The Docker build flow describes the **process of creating and running a container**.

Dockerfile → Image → Container

### Dockerfile
A **Dockerfile** is a text file containing instructions used to build a Docker image.

Typical instructions include:
- Selecting a base image
- Installing dependencies
- Copying application files
- Running commands
- Defining the container startup command

Example steps:
1. Define base image
2. Add dependencies
3. Copy application code
4. Define the command to run the application

---

### Image
A **Docker Image** is a read-only template created from a Dockerfile.

Characteristics:
- Contains application code and dependencies
- Built using layered architecture
- Can be stored in container registries (Docker Hub, etc.)

Images act as a **blueprint for containers**.

---

### Container
A **container** is a running instance of a Docker image.

It contains:
- Application
- Runtime environment
- Required libraries and dependencies

Multiple containers can be created from the **same image**.

Example workflow:

Write Dockerfile  
↓  
Build Image (docker build)  
↓  
Run Container (docker run)

---

# 3. Docker Container Lifecycle

The container lifecycle represents the **different states a container goes through during its existence**.

Created → Running → Paused → Stopped → Deleted

---

### Created
The container is created but not started.

Command:
docker create <image_name>

---

### Running
The container is actively executing its main process.

Commands:
docker start <container_id>

or

docker run <image_name>

---

### Paused
The container processes are temporarily suspended.

Commands:
docker pause <container_id>
docker unpause <container_id>

---

### Stopped
The container has stopped executing but still exists in the system.

Command:
docker stop <container_id>

The container can be restarted later.

---

### Deleted (Removed)
The container is permanently removed from the system.

Command:
docker rm <container_id>

After removal, the container no longer exists, but the **image may still remain in the system**.

---

# Quick Recap

Why Docker Containers are Lightweight:
- Share host OS kernel
- No guest OS required
- Reuse layered images
- Use namespaces and cgroups

Docker Build Flow:
Dockerfile → Image → Container

Docker Container Lifecycle:
Created → Running → Paused → Stopped → Deleted