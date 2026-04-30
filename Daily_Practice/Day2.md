# 🚀 Docker Environment Variables — Complete Exam-Ready Guide

---

## 🔹 Definition (Exam Ready)

Environment variables in Docker are key-value pairs used to pass configuration data into a container at runtime without modifying the Docker image.

---

## 🔹 Key Concept

- Key → variable name (e.g., MY_NAME)
- Value → actual data (e.g., Tarun)

Example:
MY_NAME=Tarun

---

## 🔹 Why Environment Variables?

- Avoid hardcoding values in code
- Same image can be reused with different values
- Secure sensitive data (passwords, API keys)
- Change behavior without rebuilding image

---

# 🔹 1. Basic Usage with -e

Command:
docker run -e MY_NAME=Tarun ubuntu env

Explanation:
- -e MY_NAME=Tarun → sets environment variable
- env → prints all variables inside container

Output:
MY_NAME=Tarun
PATH=...

---

# 🔹 2. Access Variable Inside Container

Command:
docker run -it -e MY_NAME=Tarun ubuntu bash

Inside container:
echo $MY_NAME

Output:
Tarun

Explanation:
- $MY_NAME → accesses variable
- -it → interactive terminal

---

# 🔹 3. Multiple Environment Variables

Command:
docker run -e NAME=Tarun -e AGE=21 ubuntu env

Output:
NAME=Tarun
AGE=21

---

# 🔹 4. Real App Example (Node.js)

app.js:
console.log("Hello " + process.env.MY_NAME);

Run:
docker run -e MY_NAME=Tarun node node app.js

Output:
Hello Tarun

Change value:
docker run -e MY_NAME=Rahul node node app.js

Output:
Hello Rahul

Explanation:
Same code, different output using env variable

---

# 🔹 5. Using .env File

.env file:
MY_NAME=Tarun
AGE=21

Run:
docker run --env-file .env ubuntu env

Output:
MY_NAME=Tarun
AGE=21

Advantage:
Cleaner than multiple -e

---

# 🔹 6. Using ENV in Dockerfile

Dockerfile:
FROM ubuntu
ENV MY_NAME=Tarun
CMD ["env"]

Build:
docker build -t myimage .

Run:
docker run myimage

Output:
MY_NAME=Tarun

Note:
Value is fixed (needs rebuild to change)

---

# 🔹 7. Overriding ENV at Runtime

Dockerfile:
FROM ubuntu
ENV MY_NAME=Default
CMD ["env"]

Run:
docker run -e MY_NAME=Tarun myimage

Output:
MY_NAME=Tarun

Explanation:
Runtime value overrides Dockerfile value

---

# 🔹 8. Difference Summary

- -e → runtime, flexible
- .env → runtime, cleaner for multiple variables
- ENV → build-time, less flexible

---

# 🔹 9. Real-World Example

app.js:
const dbHost = process.env.DB_HOST;
const dbUser = process.env.DB_USER;

console.log("Connecting to DB:", dbHost);

Run:
docker run -e DB_HOST=localhost -e DB_USER=admin myapp

Output:
Connecting to DB: localhost

---

# 🔹 10. Important Commands Summary

docker run -e MY_NAME=Tarun ubuntu env
docker run -e NAME=Tarun -e AGE=21 ubuntu env
docker run -it -e MY_NAME=Tarun ubuntu bash
docker run --env-file .env ubuntu env
docker build -t myimage .
docker run myimage

---

# 🔹 Final One-Line Summary (Exam Ready)

Environment variables in Docker allow dynamic configuration of containers at runtime, enabling flexibility, reusability, and separation of code from configuration.