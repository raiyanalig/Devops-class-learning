# 🐳 Docker Learning Log – Environment Variables & Containers

## 📅 Date

31 March 2026

---

# 🚀 Topics Covered

* Running containers (MySQL, Ubuntu, Nginx)
* Docker `run` and `exec` commands
* Environment variables (`-e`)
* Passing environment variables from host to container
* Troubleshooting Docker errors

---

# 1️⃣ Running MySQL Container

## ✅ Command

```bash
docker run -d \
--name Cont1_name \
-p 3306:3306 \
-e MYSQL_ROOT_PASSWORD=root123 \
-e MYSQL_DATABASE=college \
-e MYSQL_USER=admin \
-e MYSQL_PASSWORD=admin123 \
mysql:8
```

## 🔍 Key Learnings

* `-d` → Run container in background
* `-p` → Port mapping (host ↔ container)
* `-e` → Pass environment variables
* MySQL image uses **predefined env variables**

---

# 2️⃣ Connecting to MySQL Container

## ✅ Command

```bash
docker exec -it Cont1_name mysql -u admin -p
```

## 🔍 Understanding

* `docker exec` → Run command inside container
* `-it` → Interactive terminal
* `mysql -u admin -p` → MySQL login

---

# 3️⃣ Verifying Database

## ✅ Command

```sql
SHOW DATABASES;
```

## 📌 Output

* `college` (created by us)
* `information_schema` (system DB)
* `performance_schema` (system DB)

---

# 4️⃣ Ubuntu Container Behavior

## ❌ Issue

```bash
docker run -d ubuntu
```

👉 Container stops immediately

## 🔍 Reason

* No running process inside container
* Containers run only while a process is active

---

## ✅ Fix

```bash
docker run -it ubuntu bash
```

## 🔥 Learning

* Ubuntu is a **base image**, no default service
* Need to manually start shell (`bash`)

---

# 5️⃣ Understanding Environment Variables (`-e`)

## 🧠 Key Concept

Environment variables depend on **image type**

### 🔹 Generic Image (Ubuntu)

```bash
-e COLLEGE=CSE
```

✔ Any name works

---

### 🔹 Application Image (MySQL)

```bash
-e MYSQL_ROOT_PASSWORD=root123
```

✔ Must use **predefined variable names**

---

## 🔠 Naming Convention

* Usually **UPPERCASE**
* Not mandatory but standard

---

# 6️⃣ Host to Container Environment Variables

## 🪟 PowerShell (Windows)

### ✅ Step 1: Set variable

```powershell
$env:APP_PORT="8080"
```

### ✅ Step 2: Verify

```powershell
echo $env:APP_PORT
```

---

### ✅ Step 3: Pass to container

```powershell
docker run --rm -e APP_PORT=$env:APP_PORT nginx env
```

---

## 🔍 What Happens

1. Variable created on host
2. Docker reads it
3. Passes to container
4. Container prints it using `env`

---

# 7️⃣ Errors Faced & Fixes

## ❌ Error 1: Image not found

```bash
Unable to find image 'nginx:latest'
```

✔ Docker pulls image automatically

---

## ❌ Error 2: DNS / Network Issue

```bash
no such host
```

✔ Fix:

* Check internet
* Change DNS (8.8.8.8)
* Restart Docker

---

## ❌ Error 3: Rate Limit

```bash
429 Too Many Requests
```

## 🔍 Reason

* Too many image pulls without login

## ✅ Fix

```bash
docker login
```

---

# 8️⃣ Important Concepts Learned

## 🧠 Container Lifecycle

* Runs only when process is active
* Stops if no process

---

## 🧠 Docker Behavior

* Pulls image if not available locally
* Uses Docker Hub registry

---

## 🧠 Environment Variables

* Docker just passes variables
* Application inside container decides usage

---

# 🏁 Summary

✔ Ran MySQL container with environment variables
✔ Connected and verified database
✔ Understood difference between Ubuntu & MySQL containers
✔ Learned `docker exec` and interactive shells
✔ Understood environment variables deeply
✔ Passed variables from host to container (Windows PowerShell)
✔ Debugged real-world Docker errors

---

# 🔥 Next Steps

* Docker Volumes (data persistence)
* Docker Compose (.env files)
* Connecting container to backend project
* CI/CD integration

---

**✅ Status: Strong foundation in Docker basics achieved**
