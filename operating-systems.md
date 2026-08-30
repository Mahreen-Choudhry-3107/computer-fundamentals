# Operating Systems (OS)

> One of the most frequently asked topics in SWE interviews. Focus on processes, memory, scheduling, and concurrency.

---

## 1. What is an Operating System?

An OS is system software that acts as an **intermediary between hardware and the user/applications**. It manages resources like CPU, memory, storage, and I/O devices.

### Core Functions
- Process Management
- Memory Management
- File System Management
- Device Management
- Security & Access Control

---

## 2. Process vs Thread

### Process
An independent program in execution, with its own memory space.

### Thread
A lightweight unit of execution within a process; threads share the same memory space.

| Process | Thread |
|---|---|
| Heavyweight | Lightweight |
| Separate memory space | Shares memory with other threads in same process |
| Context switch is costly | Context switch is cheaper |
| Communication needs IPC | Communication via shared memory |
| Crash doesn't affect other processes | Crash can affect entire process |

### Multithreading Benefits
- Better CPU utilization
- Faster execution for I/O-bound and parallel tasks
- Responsive UI applications

---

## 3. Process States

```
   New → Ready → Running → Terminated
              ↑      ↓
            Ready ← Waiting
```

- **New** – process being created
- **Ready** – waiting for CPU allocation
- **Running** – currently executing
- **Waiting/Blocked** – waiting for I/O or event
- **Terminated** – execution finished

---

## 4. CPU Scheduling Algorithms

| Algorithm | Description |
|---|---|
| **FCFS** (First Come First Serve) | Executes processes in arrival order |
| **SJF** (Shortest Job First) | Executes shortest burst time first |
| **Round Robin** | Each process gets a fixed time slice (quantum) |
| **Priority Scheduling** | Higher priority processes run first |
| **Multilevel Queue** | Processes grouped into queues by type/priority |

**Key Metrics:**
- **Turnaround Time** = Completion Time − Arrival Time
- **Waiting Time** = Turnaround Time − Burst Time
- **Response Time** = Time from arrival to first CPU response

---

## 5. Memory Management

### 5.1 Virtual Memory
Allows a process to use more memory than physically available by using disk space as an extension of RAM.

- **Paging** – memory divided into fixed-size blocks (pages); avoids external fragmentation
- **Segmentation** – memory divided into variable-size segments based on logical divisions (code, stack, heap)

### 5.2 Page Fault
Occurs when a program accesses a page not currently in RAM — OS fetches it from disk.

### 5.3 Thrashing
Excessive paging activity causing the system to spend more time swapping than executing — a performance disaster.

---

## 6. Deadlocks

A deadlock occurs when two or more processes are stuck waiting for each other indefinitely.

### 4 Necessary Conditions (Coffman Conditions)
1. **Mutual Exclusion** – resource held exclusively by one process
2. **Hold and Wait** – process holds a resource while waiting for another
3. **No Preemption** – resource can't be forcibly taken away
4. **Circular Wait** – a cycle of processes waiting on each other

### Handling Deadlocks
- **Prevention** – break one of the 4 conditions
- **Avoidance** – Banker's Algorithm
- **Detection & Recovery** – detect cycle, kill/rollback a process
- **Ignore** – (used by many OSes, assuming deadlocks are rare — "Ostrich Algorithm")

---

## 7. Process Synchronization

Used to coordinate access to shared resources among multiple threads/processes.

### Race Condition
When multiple threads access/modify shared data concurrently, causing unpredictable results.

### Synchronization Tools
| Tool | Description |
|---|---|
| **Mutex (Lock)** | Ensures only one thread accesses critical section at a time |
| **Semaphore** | Counter-based signal mechanism to control access to resources |
| **Monitor** | High-level synchronization construct (used in Java `synchronized`) |

### Classic Synchronization Problems
- Producer-Consumer Problem
- Reader-Writer Problem
- Dining Philosophers Problem

---

## 8. Concurrency vs Parallelism

| Concurrency | Parallelism |
|---|---|
| Multiple tasks make progress (may not run simultaneously) | Multiple tasks execute at the exact same time |
| Single-core can be concurrent (via context switching) | Requires multi-core hardware |
| "Dealing with lots of things at once" | "Doing lots of things at once" |

---

## 9. File Systems

- Organizes and stores data on disk (files & directories)
- Examples: **NTFS** (Windows), **ext4** (Linux), **APFS** (macOS)

### Key Concepts
- **Inode** – data structure storing metadata about a file (Unix-based systems)
- **File Allocation Table (FAT)** – maps file blocks on disk

---

## 10. Quick Revision Summary

- OS manages CPU, memory, I/O, and files
- Process = program in execution; Thread = lightweight execution unit within process
- Scheduling algorithms decide which process runs next on the CPU
- Virtual memory allows execution beyond physical RAM limits using paging/segmentation
- Deadlocks require 4 conditions simultaneously; can be prevented, avoided, or detected
- Synchronization tools (mutex, semaphore) prevent race conditions

---

## 11. Interview-Style Questions

1. What is the difference between a process and a thread?
2. Explain the 4 necessary conditions for a deadlock.
3. What is a race condition? How do you prevent it?
4. Explain paging vs segmentation.
5. What is thrashing, and how can it be avoided?
6. Difference between mutex and semaphore?
7. Explain the producer-consumer problem and how to solve it.
8. What happens internally when you run a program (OS-level view)?

---

**Previous file ←** `number-systems.md`
**Next file →** `computer-networks.md`
