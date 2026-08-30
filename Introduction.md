# Introduction to Computer Fundamentals

> Goal: Build a strong base in how computers work internally — essential for every software engineer, and a common area probed in technical interviews.

---

## 1. What is a Computer?

A computer is an electronic device that takes **input**, processes it according to a set of **instructions (program)**, and produces **output**. It works on the basic cycle:

```
INPUT → PROCESS → OUTPUT
          ↑
       STORAGE
```

### Key Characteristics
- **Speed** – executes billions of instructions per second
- **Accuracy** – performs calculations with very high precision
- **Storage** – can store huge amounts of data
- **Automation** – once programmed, runs without manual intervention
- **Versatility** – can perform diverse tasks (math, graphics, networking, etc.)

---

## 2. Basic Components of a Computer

### 2.1 Hardware
Physical parts of a computer.

| Component | Function |
|---|---|
| **CPU (Central Processing Unit)** | The "brain" — executes instructions (fetch, decode, execute) |
| **RAM (Memory)** | Temporary, volatile storage for running programs/data |
| **Storage (HDD/SSD)** | Permanent, non-volatile storage |
| **Motherboard** | Connects all components together |
| **Input Devices** | Keyboard, mouse, scanner |
| **Output Devices** | Monitor, printer, speaker |
| **GPU** | Handles graphics/parallel computation |

### 2.2 Software
Set of instructions that tell hardware what to do.

- **System Software** – OS, device drivers (e.g., Windows, Linux, macOS)
- **Application Software** – Browsers, editors, games, business apps
- **Programming Software** – Compilers, interpreters, IDEs

---

## 3. CPU Architecture Basics

### 3.1 The Fetch-Decode-Execute Cycle
1. **Fetch** – CPU retrieves an instruction from memory
2. **Decode** – Instruction is decoded into control signals
3. **Execute** – The operation is performed
4. **Store** – Result is written back to memory/register

### 3.2 Key CPU Components
- **ALU (Arithmetic Logic Unit)** – performs arithmetic & logical operations
- **CU (Control Unit)** – directs operation of the processor
- **Registers** – small, super-fast storage locations inside the CPU
- **Cache (L1, L2, L3)** – fast memory between CPU and RAM to reduce latency

### 3.3 Clock Speed & Cores
- **Clock Speed (GHz)** – number of cycles per second
- **Cores** – independent processing units; multi-core allows parallelism
- **Hyper-threading** – simulates extra cores using a single physical core

---

## 4. Memory Hierarchy

Memory is organized in layers based on speed, cost, and size:

```
Registers  →  Cache  →  RAM  →  SSD/HDD  →  Cloud/Network Storage
(fastest,          (slowest,
 smallest,          largest,
 costliest)         cheapest)
```

| Type | Volatile? | Speed | Approx. Size |
|---|---|---|---|
| Registers | Yes | Fastest | Bytes |
| Cache | Yes | Very Fast | KB–MB |
| RAM | Yes | Fast | GB |
| SSD/HDD | No | Slow | TB |

**Why it matters for SWEs:** Understanding memory hierarchy explains *why* cache-friendly code, data locality, and algorithmic complexity (Big-O) impact real-world performance.

---

## 5. Number Systems

Computers operate internally using **binary (base 2)**.

| System | Base | Digits Used |
|---|---|---|
| Binary | 2 | 0, 1 |
| Octal | 8 | 0–7 |
| Decimal | 10 | 0–9 |
| Hexadecimal | 16 | 0–9, A–F |

### Conversions
- **Decimal → Binary:** Repeated division by 2
- **Binary → Decimal:** Multiply each bit by 2^position and sum
- Example: `1011` (binary) = `1×2³ + 0×2² + 1×2¹ + 1×2⁰` = `11` (decimal)

### Why Binary?
Transistors have two stable states: **ON (1)** and **OFF (0)** — mapping naturally to binary logic.

---

## 6. Data Representation

- **Bit** – smallest unit (0 or 1)
- **Byte** – 8 bits
- **Word** – group of bytes processed together by CPU (e.g., 32-bit, 64-bit)

### Storage Units
```
1 Byte = 8 Bits
1 KB = 1024 Bytes
1 MB = 1024 KB
1 GB = 1024 MB
1 TB = 1024 GB
```

### Character Encoding
- **ASCII** – 7-bit encoding for English characters (128 symbols)
- **Unicode / UTF-8** – supports characters from all languages worldwide

---

## 7. Operating System (Brief Intro)

The OS is software that manages hardware and provides services to applications.

Core Responsibilities:
- **Process Management** – scheduling, multitasking
- **Memory Management** – allocation, paging, virtual memory
- **File System Management** – organizing data on disk
- **Device Management** – drivers, I/O
- **Security** – permissions, user access

*(Covered in depth in a dedicated `operating-systems.md` file.)*

---

## 8. How a Program Runs (High-Level Flow)

```
Source Code (.c, .java, .py)
        ↓
   Compiler / Interpreter
        ↓
  Machine Code (Binary)
        ↓
   Loaded into RAM
        ↓
   Executed by CPU
        ↓
       Output
```

### Compiler vs Interpreter
| Compiler | Interpreter |
|---|---|
| Translates entire code at once | Translates line-by-line |
| Faster execution | Slower execution |
| Errors shown after full compilation | Errors shown immediately |
| e.g., C, C++, Go | e.g., Python, JavaScript (traditionally) |

---

## 9. Networking Basics (Preview)

- **IP Address** – unique identifier for a device on a network
- **Client-Server Model** – client requests, server responds
- **Protocols** – rules for communication (HTTP, TCP/IP, DNS)

*(Covered in depth in a dedicated `networking.md` file.)*

---

## 10. Why This Matters for Software Engineers

| Concept | Real-World Relevance |
|---|---|
| Memory hierarchy | Writing cache-efficient, performant code |
| Number systems | Bitwise operations, low-level programming, debugging |
| CPU architecture | Understanding concurrency, multithreading |
| OS concepts | Debugging processes, memory leaks, deadlocks |
| Compilers/Interpreters | Choosing the right language/tool for the job |
| Networking | Building APIs, distributed systems, debugging latency |

---

## 11. Quick Revision Summary

- Computer = Input + Process + Output + Storage
- CPU works on Fetch-Decode-Execute cycle
- Memory hierarchy: Registers > Cache > RAM > Disk
- Computers use binary internally
- OS manages hardware resources for applications
- Programs move from source code → machine code → execution

---

## 12. Interview-Style Questions to Revisit

1. Explain the Fetch-Decode-Execute cycle.
2. Why is cache memory faster than RAM?
3. Convert `45` (decimal) to binary and hexadecimal.
4. Difference between compiler and interpreter?
5. What happens when you run a program, step-by-step, from OS perspective?
6. Why do computers use binary instead of decimal?
7. What is the difference between volatile and non-volatile memory?

---

**Next file →** `data-representation.md` or `operating-systems.md` (recommended progression)
