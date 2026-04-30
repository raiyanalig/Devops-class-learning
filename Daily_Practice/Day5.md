# 🐳 Docker Environment Variables & Command-Line Utilities (Pre-Exam Notes)

---

## 🔹 1. Environment Variables in Docker

Definition:
Environment variables are used to pass configuration values into a container **without modifying the application code**.

---

## 🔹 2. Passing Environment Variables

Using `-e` (single variable):
docker run -e APP_PORT=8080 nginx env

Explanation:

* `-e` → passes a single environment variable
* `APP_PORT=8080` → key-value pair
* `env` → prints all variables inside container

---

## 🔹 3. Using `.env` File

Example `.env`:
DB_HOST=localhost
DB_USER=root
DB_PASS=secret123

Command:
docker run --env-file .env nginx env

Explanation:

* `--env-file` → loads multiple variables from file
* Cleaner than multiple `-e`
* Used in real-world deployments

---

## 🔹 4. Important Concept

Output includes:

* Default container variables
* * Your custom variables

Final Concept:
Final Environment = Default + User-defined

---

## 🔹 5. Docker Run Syntax

Syntax:
docker run [OPTIONS] IMAGE [COMMAND]

Example:
docker run --env-file .env nginx env

Meaning:

* docker run → Start container
* --env-file → Load variables
* nginx → Image
* env → Command inside container

---

## 🔹 6. Filtering Output (Important)

Windows (PowerShell):
docker run --env-file .env nginx env | findstr DB_

Linux/Mac:
docker run --env-file .env nginx env | grep DB_

Use:

* Filters only required variables
* Reduces clutter

---

## 🔹 7. Pipe Operator `|`

Definition:
Used to pass output of one command as input to another

Syntax:
command1 | command2

---

## 🔹 8. Useful Command-Line Tools

findstr:
findstr DB_
findstr /i db_
findstr /r "^DB_"

type:
type .env

sort:
docker run --env-file .env nginx env | sort

count lines:
docker run --env-file .env nginx env | find /c "DB_"

extract value:
for /f "tokens=2 delims==" %a in ('type .env ^| findstr DB_HOST') do echo %a

---

## 🔹 9. Output Redirection

save output:
docker run --env-file .env nginx env > output.txt

append output:
echo NewLine >> output.txt

---

## 🔹 10. Multiple Commands

run on success:
command1 && command2

run on failure:
command1 || command2

---

## 🔹 11. MySQL Predefined Environment Variables

Used by MySQL Docker Image:

MYSQL_ROOT_PASSWORD=secret123
MYSQL_DATABASE=testdb
MYSQL_USER=user1
MYSQL_PASSWORD=pass123

Explanation:

* These are predefined variables
* Must start with MYSQL_
* Used to configure database automatically

---

## 🔹 12. Custom vs Predefined Variables

Predefined → MYSQL_ROOT_PASSWORD → used by MySQL container
Custom → DB_HOST → used by application

---

## 🔹 13. Important Concept (Docker Networking)

Wrong:
DB_HOST=localhost

Correct:
DB_HOST=mysql-container

Reason:

* localhost = same container
* Use container name to connect services

---

## 🔹 14. Key Takeaways (Exam Ready)

* Environment variables enable dynamic configuration
* `-e` → single variable
* `--env-file` → multiple variables
* `env` → prints all variables inside container
* Output includes default + user-defined variables
* Use findstr / grep to filter output
* MySQL uses predefined MYSQL_* variables
* Containers communicate using container names

---

## 🎯 One-Line Summary

Environment variables in Docker allow flexible, secure, and dynamic configuration of applications without modifying source code.
