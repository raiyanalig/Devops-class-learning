# 📦 Docker Image, Registry & Distribution Notes

---

# 🧱 1. Docker Image

## 🧠 Definition
A Docker image is a read-only template that contains everything required to run an application, including base OS, libraries, runtime, and application code.

## 🧩 Components of Docker Image

1. **Base OS**  
   Minimal operating system (e.g., Ubuntu, Alpine)

2. **Libraries**  
   Required dependencies for the application

3. **Runtime**  
   Environment to execute the application (e.g., Python, JVM)

4. **Application Code**  
   Actual program or project files

---

# ✍️ 2. Docker Container (Writable Layer)

## 🧠 Definition
A Docker container is a running instance of an image with an additional writable layer on top.

## 🔹 Key Points
- Image layers are read-only
- Container adds a writable layer
- Uses Copy-on-Write mechanism

## 📌 Behavior
- Changes are stored in writable layer
- Original image remains unchanged
- Writable layer is deleted when container is removed

---

# 📦 3. Image Registry

## 🧠 Definition
An image registry is a centralized repository used to store, manage, and distribute Docker images.

---

## ❌ Without Registry

1. Each system must build images independently  
2. High inconsistency across environments  
3. Manual software installation  
4. No version control of application environments  

---

## ✅ With Registry

1. Build once, deploy anywhere  
2. Faster deployments  
3. Version-controlled environments  
4. Rollback capability  

---

# 🌍 4. Public vs Private Registry

## 🌍 Public Registry

### 🔹 Characteristics
- Open to everyone  
- Easy sharing  
- Less secure  

### 🔹 Examples
- Docker Hub  
- Images: nginx, ubuntu, node, mysql  

---

## 🔒 Private Registry

### 🔹 Characteristics
1. Secure and controlled access  
2. Used in enterprises  
3. Stores proprietary applications  
4. Integrated with IAM and RBAC  

### 🔹 Examples
- AWS ECR  
- Azure Container Registry  
- GitHub Container Registry  
- On-premise private registry  

---

# 🔐 5. RBAC (Role-Based Access Control)

## 🧠 Definition
RBAC is a security mechanism where permissions are assigned to roles, and users are assigned to those roles.

## 🔹 Key Idea
- Roles → Permissions  
- Users → Roles  

## 🎯 Example
- Admin → Full access  
- Developer → Push, Pull  
- Viewer → Pull only  

---

# 🔐 6. IAM vs RBAC

| IAM | RBAC |
|-----|------|
| User-based access | Role-based access |
| Permissions to users | Permissions to roles |
| Less scalable | More scalable |

## 🎯 Key Idea
- IAM → Who you are  
- RBAC → What you can do  

---

# 📦 7. Image Naming Convention

## 🧠 Format
<registry>/<namespace>/<image>:<tag>

## 🔍 Example
docker.io/harpreet/webapp:v1

## 🧩 Components

| Component | Meaning |
|----------|--------|
| Registry | Location of image |
| Namespace | User or organization |
| Image | Application name |
| Tag | Version of image |

---

# 🏷️ 8. Tags and Versioning

## 🧠 Definition
Tags represent different versions of a Docker image.

## 🔹 Types

### latest
- Default tag  
- Used when no tag is specified  

### Versioned Tags
- v1, v2, v2.1, 1.0.0  
- Represent specific versions  

## 🔥 Importance
- Consistency  
- Easy debugging  
- Rollback support  

---

# 🔄 9. Image Distribution Process

## 🧠 Definition
The process of moving Docker images from development to production using a registry.

## 🔹 Flow

1. Developer builds image locally  
2. Image is pushed to registry  
3. Registry stores the image  
4. Servers pull the image  
5. Containers are created from the image  

## 🔁 Flow Diagram
Developer → Build → Push → Registry → Pull → Run → Container
