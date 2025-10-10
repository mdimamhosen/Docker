# Operating System Kernel Notes

## What is a Kernel?
- **Kernel** → Core of the Operating System
- The OS runs in two distinct spaces:
  - **Kernel Space**: Where the kernel operates
  - **User Space**: Where user applications run

## Hardware Management
- RAM, hard disk, and other hardware are handled **exclusively by the kernel**
- User applications cannot directly access hardware resources

## CPU Operating Modes

### User Mode
- **Definition**: When the CPU runs user applications
- **Characteristics**: 
  - Limited access to system resources
  - Cannot directly access hardware
  - Restricted instruction set

### Kernel Mode
- **Definition**: When the CPU runs OS code
- **Characteristics**:
  - Full access to all system resources
  - Can execute privileged instructions
  - Direct hardware access

## System Calls
- **Definition**: Interface between user space applications and kernel space
- **Process**: User space applications make system calls to request kernel services
- **Purpose**: Allows controlled access to system resources and hardware

## Key Concepts
- User applications run in user mode for security and stability
- Kernel mediates all hardware access
- System calls provide a controlled way for applications to request kernel services



