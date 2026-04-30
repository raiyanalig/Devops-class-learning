# 📦 Docker Environment Variables & MySQL – Complete Notes + Practice

---

# ✅ 1. Exam-Ready Definitions

## 🔹 Docker Container

A **Docker container** is a lightweight, standalone, executable package that includes everything needed to run an application (code, runtime, libraries, dependencies).

---

## 🔹 Environment Variables in Docker

**Environment variables** in Docker are key-value pairs used to pass configuration data into containers at runtime, allowing dynamic and flexible application behavior without modifying code.

---

## 🔹 Multiple Environment Variables

Docker allows **multiple environment variables** using:

* `-e` flag
* `.env` files
* Dockerfile `ENV`
* Docker Compose

👉 Used for:

* Configuration management
* Security (passwords, credentials)
* Environment separation (dev/test/prod)

---

## 🔹 Key Concept

> Environment variables exist **inside the container**, not on the host system.

---

# ✅ 2. Setting Multiple Environment Variables

## 🔹 Using CLI (`-e`)

docker run -d 
-e VAR1=value1 
-e VAR2=value2 
image_name

---

## 🔹 Using `.env` File

APP_ENV=production
DB_HOST=localhost
DB_USER=admin
DB_PASS=secret

docker run --env-file .env image_name

---

## 🔹 Using Dockerfile

ENV NODE_ENV=production PORT=3000

---

## 🔹 Using Docker Compose

environment:
  NODE_ENV: production
  DB_HOST: localhost

---

# ⚡ Priority Order (Exam Important)

1. CLI (`-e`)
2. Docker Compose
3. `.env` file
4. Dockerfile

👉 “CLI overrides everything”

---

# ✅ 3. MySQL Docker Practical

## 🔹 Correct Command

docker run -d --name Tarun_Container -p 3306:3306 
-e MYSQL_ROOT_PASSWORD=root123 
-e MYSQL_DATABASE=college 
-e MYSQL_USER=admin 
-e MYSQL_PASSWORD=admin123 
mysql:8

---

## 🔹 Important Variables

MYSQL_ROOT_PASSWORD → Root password
MYSQL_DATABASE → Creates database
MYSQL_USER → Creates user
MYSQL_PASSWORD → User password

---

## ❌ Common Mistakes

* Wrong variable names (`MYSQL_user`, `MY_SQL_PASSWORD`)
* Case sensitivity issues
* Container stops due to misconfiguration

---

## 🔹 Access MySQL

docker exec -it Tarun_Container mysql -u admin -p

---

## 🔹 Show Databases

SHOW DATABASES;

---

## 🔹 Use Database

USE college;

---

## 🔹 Create Table

CREATE TABLE students (
  id INT PRIMARY KEY,
  name VARCHAR(50)
);

---

## 🔹 Show Tables

SHOW TABLES;

---

# ⚠️ SQL Mistakes Learned

❌ Wrong:
select *
show database

✔ Correct:
SHOW DATABASES;

---

## 🔥 Important SQL Concept

* `->` means query incomplete
* `;` executes query

👉 “Without `;`, MySQL keeps waiting”

---

# ✅ 4. Debugging Containers

docker ps
docker ps -a
docker logs container_name
docker rm -f container_name

---

# ✅ 5. Ubuntu Container & Environment Variables

## ❌ Problem

docker run --name ubuntu_container -e COLLEGE=CSE ubuntu

👉 Container stops immediately

---

## 🔥 Reason

> Containers run only while their main process is running
> Ubuntu has no default process → exits

---

## ✅ Correct Way (Interactive Mode)

docker run -it --name ubuntu_container -e COLLEGE=CSE ubuntu bash

---

## 🔹 Access Variable

echo $COLLEGE

👉 Output: CSE

---

## ❌ Mistake

echo$COLLEGE

👉 Treated as invalid command

---

# ✅ 6. Key Concept: Host vs Container

Host (PowerShell) → ❌ Cannot access container variables
Container → ✅ Can access variables

---

## 🔹 Example

echo $COLLEGE ❌ (host)

docker exec ubuntu_container printenv COLLEGE ✅

---

# ✅ 7. Keep Container Running

docker run -it ubuntu bash
docker run -dit ubuntu sleep infinity

---

# ✅ 8. Exit Interactive Mode

exit;
Ctrl + D

---

## 🔹 If Stuck (`->`)

\c

---

# 🧠 Final Revision

* Docker env variables are **runtime configs**
* They are **case-sensitive**
* Exist **inside container only**
* Containers stop if **no running process**
* MySQL requires **correct env variables**
* SQL requires **semicolon (;) to execute**

---

# ⚡ One-Line Summary

👉 “Docker environment variables configure containers at runtime, but exist only inside the container, and correct syntax + proper process is required to keep containers running.”

---

# 🚀 Practice Checklist

✔ Run MySQL container
✔ Fix env variable errors
✔ Access MySQL
✔ Execute SQL commands
✔ Handle SQL syntax errors
✔ Run Ubuntu container
✔ Access environment variables
✔ Understand container lifecycle

---