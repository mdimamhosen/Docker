 
# 🐧 Linux Namespaces, cgroups & Containers

## 📘 Overview
In Linux, **containers** provide process isolation and resource control without the need for full virtual machines.  
They are built on two key kernel features:
- **Namespaces** → Control *what a process can see*  
- **cgroups (Control Groups)** → Control *how much a process can use*  

Together, they form the foundation for modern container technologies like **Docker**, **Podman**, and **Kubernetes**.

---

## 🧠 1. Process Modes & Kernel Interaction

Every process in Linux operates either in:
- **User Mode (User Space)** – Where applications like Chrome, Spotify, and Node.js run.
- **Kernel Mode (Kernel Space)** – Where the kernel manages system resources (CPU, RAM, Disk, Network).

```

USER MODE
├── go
├── chrome
│      ↓  (system call)
KERNEL MODE
├── Kernel → interacts with:
│     ├── CPU
│     ├── RAM
│     └── Hard Disk

```

The **system call (syscall)** acts as a bridge between user space and kernel space.

---

## 🌐 2. Namespaces — “What a Process Can See”

**Namespaces** isolate the **view** of the system for a set of processes.  
Each namespace provides its own instance of global system resources.

### 🧩 Examples of Namespaces:
| Namespace | Isolates | Example |
|------------|-----------|----------|
| **PID** | Process IDs | Process IDs appear unique within a container |
| **NET** | Network interfaces | Each container can have its own network stack |
| **MNT** | Mount points | Different file system views per container |
| **UTS** | Hostname | Containers can have their own hostname |
| **IPC** | Interprocess communication | Isolates message queues & shared memory |
| **USER** | User IDs | Containers can map root user inside, non-root outside |

### Example:
```

Namespace 1:

* python, go, node, chrome
* Sees its own files, network, PIDs

Namespace 2:

* python, shopify
* Sees only its own resources

```

Thus, **namespaces isolate what a process can see** — its environment.

---

## ⚙️ 3. cgroups (Control Groups) — “How Much a Process Can Use”

**cgroups** limit, account, and isolate the resource usage (CPU, memory, disk I/O, network, etc.) of process groups.

### 🧩 Example Configurations:

| Group | Resources | Description |
|--------|------------|-------------|
| **Group A** | 4 CPU cores, 10 GB RAM, 50 GB Disk, full network access | High-resource service |
| **Group B** | 1 CPU core, 500 MB RAM, 5 GB Disk | Lightweight app |

This means:
- Processes in **Group A** can use more resources.
- Processes in **Group B** are restricted — preventing overuse.

### Concept:
```

cgroups  →  "How much resources can a process use?"
namespaces → "What can a process see?"

```

---

## 🧱 4. Containers = cgroups + namespaces

A **container** combines both:
- **Namespaces** → isolate what processes can see  
- **cgroups** → limit how much they can use  

```

Container = Namespace + cgroup

```

This allows multiple isolated environments to run on the same OS kernel — each behaving like its own mini operating system.

---

## 🧩 5. Container Example (Conceptual Flow)

```

+--------------------------------------------------+

| Container A                                          |
| ---------------------------------------------------- |
| Namespace → isolates process view (PID, FS, NET)     |
| cgroup → limits CPU=4, RAM=10GB, Disk=50GB           |
| --------------------------------------------------   |
| Apps: python, go, node, chrome                       |
| +--------------------------------------------------+ |

+--------------------------------------------------+

| Container B                                          |
| ---------------------------------------------------- |
| Namespace → isolates files, PIDs, and network        |
| cgroup → limits CPU=1, RAM=500MB, Disk=5GB           |
| --------------------------------------------------   |
| Apps: python, shopify                                |
| +--------------------------------------------------+ |

```

Both containers share the same **Linux kernel**, but are isolated in both *view* and *resource usage*.

---

## 🧩 6. Example with Kernel & System Calls

```

User Space:
├── spotify  → go 1.16
├── nodejs   → go 1.25
↓ (system calls)
Kernel Space:
├── Kernel manages system resources
└── Interacts with CPU, RAM, Hard Disk

```

Each app in a separate namespace interacts with the same kernel through syscalls, but the kernel ensures isolation using namespaces and cgroups.

---

## 🧰 7. Key Terms Recap

| Term | Description |
|------|--------------|
| **Namespace** | Defines what a process can see (isolation of environment) |
| **cgroup** | Defines how much a process can use (resource control) |
| **Container** | Lightweight isolated environment built using namespaces + cgroups |
| **Syscall** | Interface between user space and kernel space |
| **Kernel Space** | Privileged memory area managing hardware |
| **User Space** | Where user applications run |

---

## 🧩 8. Visualization

```

USER SPACE
├── Namespace 1 (python, node, go, chrome)
├── Namespace 2 (python, shopify)
↓
SYSTEM CALL
↓
KERNEL SPACE
├── Kernel
│     ├── cgroup A (CPU:4, RAM:10GB, Disk:50GB)
│     └── cgroup B (CPU:1, RAM:500MB, Disk:5GB)
↓
HARDWARE (CPU, RAM, Disk, Network)

```

---

## 🏁 9. Summary

- **Namespaces** → Isolate *what* processes can see.  
- **cgroups** → Restrict *how much* resources they can use.  
- **Container = Namespace + cgroup** → A lightweight, isolated environment.  
- Unlike VMs, containers share the same kernel, making them faster and more efficient.  

---

### ✍️ Author
Generated by **GPT-5**  
Topic: *Linux Containers, Namespaces & cgroups*  
Category: *Operating Systems / Containerization / DevOps*
```

 