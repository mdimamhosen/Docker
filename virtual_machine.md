
# 🧠 Virtual Machines (VM) & Virtualization

## 📘 Overview
A **Virtual Machine (VM)** is a software-based emulation of a physical computer that allows multiple operating systems to run on a single physical host.  
Each VM operates independently with its own OS, kernel, and applications, sharing underlying hardware resources through a **hypervisor**.

---

## 🏗️ Architecture Overview

### 🧩 Host System
The **Host OS** (e.g., Linux) runs directly on the hardware and manages resources like:
- **CPU** – Physical processor cores (e.g., 6 cores)
- **RAM** – Main memory (e.g., 10 GB)
- **Hard Disk** – Storage (e.g., 100 GB)

It communicates with the hardware using **system calls (syscalls)** handled by the **kernel**.

```

+--------------------------+
|        Applications      |   (Go, Chrome, Hypervisor)
+--------------------------+
↓ Syscall
+--------------------------+
|          Kernel          |   (Manages hardware)
+--------------------------+
↓           ↓          ↓
[CPU]       [RAM]      [HDD]
↓
+--------------------------+
|        Linux OS          |
|        (Host OS)         |
+--------------------------+
↓
[Physical Hardware]

```

---

## ⚙️ Hypervisor

The **hypervisor** is a layer of software that enables virtualization.  
It creates and manages multiple VMs by allocating portions of CPU, memory, and storage to each one.

### 🔸 Types of Hypervisors
1. **Type 1 (Bare Metal)** – Runs directly on physical hardware.  
   _Examples: VMware ESXi, KVM, Microsoft Hyper-V_
2. **Type 2 (Hosted)** – Runs on top of an existing OS.  
   _Examples: VirtualBox, VMware Workstation_

### 🔸 Functions
- Allocates host resources to VMs.
- Isolates each VM’s environment.
- Emulates virtual hardware (CPU, RAM, storage).

---

## 💻 Virtual Machines (VMs)

Each **VM** acts as an independent system with its own:
- **Guest Kernel**
- **Applications**
- **Virtual Hardware (CPU, RAM, Disk)**

Example configuration:
```

VM1:
CPU: 4 cores
RAM: 4 GB
HDD: 50 GB

VM2:
CPU: 4 cores
RAM: 4 GB
HDD: 50 GB

```

Both VMs run under the same host but are fully isolated.

```

```
             +---------------------------+
             |         Hypervisor        |
             +---------------------------+
                 ↓                 ↓
      +----------------+     +----------------+
      |     VM 1       |     |     VM 2       |
      | +------------+ |     | +------------+ |
      | |  Kernel    | |     | |  Kernel    | |
      | +------------+ |     | +------------+ |
      | | Apps: Go,   | |     | | Apps: Go,   | |
      | | Chrome      | |     | | Chrome      | |
      +----------------+     +----------------+
```

```

---

## 🔄 System Call Flow

System calls (syscalls) are the bridge between applications and the kernel.  
In virtualization, these calls go through the **hypervisor** before reaching physical hardware.

```

Application (Go, Chrome)
↓
Syscall
↓
Hypervisor
↓
Host Kernel
↓
Physical Hardware (CPU, RAM, Disk)

```

---

## 🧠 Layered Architecture Summary

| Layer | Description | Examples |
|-------|--------------|----------|
| **Applications** | User-level programs | Chrome, Go |
| **Hypervisor** | Virtualization layer | VMware, VirtualBox |
| **Kernel** | Manages system calls and resources | Linux Kernel |
| **Hardware** | Physical resources | CPU, RAM, Disk |

---

## 🚀 Benefits of Virtualization

- **Efficient Resource Utilization** – Run multiple OSes on one machine.  
- **Isolation** – Each VM is sandboxed; failure in one doesn’t affect others.  
- **Portability** – VMs can be moved or cloned easily.  
- **Testing & Development** – Ideal for sandboxed environments.  
- **Security** – Applications are isolated inside separate VMs.

---

## 💡 Example Use Case

A Linux host system can run multiple isolated environments like:
- **VM1 (Development Environment)**  
  - Node.js server, React frontend  
  - 4 cores, 4 GB RAM  

- **VM2 (Testing Environment)**  
  - MySQL + Nginx setup  
  - 4 cores, 4 GB RAM  

Both share the host’s **6-core CPU**, **10 GB RAM**, and **100 GB storage**.

---

## 🧩 Key Terms

| Term | Definition |
|------|-------------|
| **Host OS** | The main OS running on physical hardware |
| **Guest OS** | The OS running inside a virtual machine |
| **Syscall** | A system call between app and kernel |
| **Hypervisor** | Software managing virtual machines |
| **Ballooning** | Dynamic adjustment of memory between VMs |

---

## 🧱 Full Architecture Diagram (Conceptual)

```

+-----------------------------------------------------------+
|                        Applications                       |
|              (Go, Chrome, Hypervisor, etc.)               |
+-----------------------------------------------------------+
│
▼
+-----------------------------------------------------------+
|                          Syscall                          |
+-----------------------------------------------------------+
│
▼
+-----------------------------------------------------------+
|                          Kernel                           |
|                  (Linux Host Kernel)                      |
+-----------------------------------------------------------+
│                    │                    │
▼                    ▼                    ▼
[CPU: 6 cores]       [RAM: 10 GB]         [Disk: 100 GB]
│
▼
+-----------------------------------------------------------+
|                        Host OS (Linux)                    |
+-----------------------------------------------------------+
│
▼
+-----------------------------------------------------------+
|                    Physical Hardware                      |
+-----------------------------------------------------------+

```

---

## 🏁 Summary

Virtual Machines enable multiple operating systems to coexist on one physical machine through a **hypervisor**.  
Each VM has its own isolated resources, OS, and applications — making it ideal for development, testing, and deployment environments.

---

### ✍️
Topic: *Virtualization & Virtual Machine Architecture*  
Category: *Operating Systems / Cloud Infrastructure*
```

