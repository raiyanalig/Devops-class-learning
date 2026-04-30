# Linux Namespaces and cgroups (Used in Containers)

## 1. Namespaces

### Definition

**Namespaces are a Linux kernel feature that provide isolation.**\
They ensure that a process or container can only see its own resources
and not the resources of other containers or the host system.

In simple words:\
\> **Namespaces create a separate view of the system for each
container.**

### Why Namespaces Are Needed

Without namespaces: - Every process could see all other processes in the
system. - Containers would interfere with each other. - There would be
no isolation.

With namespaces: - Each container works like a **separate mini system**.

### Example

Suppose you run a container:

``` bash
docker run -it ubuntu
```

Inside the container:

``` bash
ps
```

Output inside container:

    PID  COMMAND
    1    bash
    7    ps

But on the host system, the same process might actually be:

    PID  COMMAND
    2451 bash
    2460 ps

Because of the **PID namespace**, the container thinks its first process
is **PID 1**.

### Common Types of Namespaces

  Namespace   What It Isolates
  ----------- ----------------------------------
  PID         Process IDs
  Network     Network interfaces, IP addresses
  Mount       File systems
  UTS         Hostname
  IPC         Inter-process communication
  User        User IDs and permissions

------------------------------------------------------------------------

## 2. cgroups (Control Groups)

### Definition

**cgroups are a Linux kernel feature that control and limit the
resources used by processes or containers.**

They control resources like:

-   CPU
-   Memory
-   Disk I/O
-   Network bandwidth
    
In simple words:

> **cgroups ensure that one container cannot use all system resources.**

### Why cgroups Are Needed

Without cgroups: - One container could consume all memory or CPU. -
Other containers or applications could crash.

With cgroups: - Each container gets a **fixed share of system
resources**.

### Example

Run a container with a memory limit:

``` bash
docker run -m 200m ubuntu
```

Meaning:

-   The container can only use **200 MB RAM**.
-   Even if the host system has **16 GB RAM**, the container cannot
    exceed **200 MB**.

If it tries to use more memory → the container will be **stopped or
killed**.

Another example limiting CPU:

``` bash
docker run --cpus=1 ubuntu
```

This container can only use **1 CPU core**.

------------------------------------------------------------------------

## 3. How Containers Use Both

When you run a container:

``` bash
docker run nginx
```

The system uses:

**Namespaces** - Create isolation (separate processes, network,
filesystem).

**cgroups** - Limit resource usage (CPU, memory).

So the container becomes:

    Isolated environment + Controlled resource usage

------------------------------------------------------------------------

## Quick Summary

  Feature      Purpose
  ------------ --------------------------------------
  Namespaces   Provide isolation between containers
  cgroups      Limit and control resource usage

------------------------------------------------------------------------

## One-Line Exam Definitions

**Namespaces:**\
A Linux kernel feature that isolates system resources so that processes
in a container only see their own environment.

**cgroups:**\
A Linux kernel feature that limits and manages resource usage such as
CPU and memory for processes or containers.
