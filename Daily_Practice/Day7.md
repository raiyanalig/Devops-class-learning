# Docker: Passing Environment Variables from Host

## Step 1: Set Environment Variable on Host (PowerShell)

```powershell
$env:APP_PORT=8080
```

---

## Step 2: Pass Variable to Docker Container

```bash
docker run -e APP_PORT=$env:APP_PORT nginx env
```

---

## Output

```bash
HOSTNAME=ad91b8958118
HOME=/root
APP_PORT=8080
NGINX_VERSION=1.29.7
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
PWD=/
```

---

## Explanation

- `$env:APP_PORT=8080` → Sets environment variable on host (Windows PowerShell)
- `-e APP_PORT=$env:APP_PORT` → Passes variable into container
- `nginx env` → Runs container and prints environment variables

---

## Key Concepts

### 1. Syntax Difference

**PowerShell:**
```powershell
$env:VAR_NAME=value
docker run -e VAR_NAME=$env:VAR_NAME image
```

**Linux/macOS:**
```bash
export VAR_NAME=value
docker run -e VAR_NAME=$VAR_NAME image
```

---

### 2. Direct Passing (Shortcut)

```bash
docker run -e APP_PORT=8080 nginx env
```

---

### 3. Multiple Variables

```bash
docker run -e APP_PORT=8080 -e DB_USER=root nginx env
```

---

### 4. Best Practice (Auto-remove container)

```bash
docker run --rm -e APP_PORT=$env:APP_PORT ubuntu env
```

---

## Summary

- Host → Container environment variable passing works using `-e`
- Use `.env` file for multiple variables
- Use `--rm` to keep system clean