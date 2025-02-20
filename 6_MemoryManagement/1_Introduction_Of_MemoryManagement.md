**Memory Management**

### **Introduction to Memory**
Memory can be defined as a collection of data stored in a specific format. It is used to store instructions and process data. Memory comprises a large array of words or bytes, each with its own unique location. The primary purpose of a computer system is to execute programs. Programs and the information they access must reside in main memory during execution. The CPU fetches instructions from memory according to the program counter’s value.

Effective memory management is essential to achieve multiprogramming and proper utilization of memory. Various memory management methods exist, and their effectiveness depends on the situation.

**Topics Covered:**
- What is Main Memory?
- What is Memory Management?
- Why Memory Management is Required?
- Logical Address Space and Physical Address Space
- Static and Dynamic Loading and Linking
- Swapping
- Contiguous Memory Allocation
- Memory Allocation
- Fragmentation
- Paging

---

### **What is Main Memory?**
Main memory is central to the operation of modern computers. It is a large array of words or bytes, ranging from hundreds of thousands to billions. Main memory serves as a repository of rapidly available information shared by the CPU and I/O devices. It holds programs and data actively utilized by the processor.

**Key Features:**
- **Volatility:** RAM (Random Access Memory) is volatile and loses data during power interruptions.
- **Speed:** Associated closely with the processor, allowing extremely fast data transfer.

---

### **What is Memory Management?**
In a multiprogramming environment, the operating system resides in a portion of memory, while the rest is allocated to multiple processes. Memory management involves managing operations between the main memory and the disk during process execution. Its primary aim is efficient memory utilization.

**Responsibilities:**
- Allocate and de-allocate memory before and after process execution.
- Track memory usage by processes.
- Minimize fragmentation.
- Ensure optimal memory utilization.
- Maintain data integrity during execution.

---

### **Logical Address Space and Physical Address Space**
1. **Logical Address Space:**
   - Address generated by the CPU.
   - Known as a virtual address.
   - Defines the size of a process and is subject to change.

2. **Physical Address Space:**
   - Address seen by the memory unit (loaded into the memory address register).
   - Known as a real address and remains constant.
   - Computed by the Memory Management Unit (MMU).

**Key Point:** The MMU handles run-time mapping from virtual to physical addresses.

---

### **Static and Dynamic Loading**
- **Static Loading:** Loads the entire program into a fixed address in memory. Requires more space.
- **Dynamic Loading:** Loads routines only when they are called. Saves memory and ensures unused routines are not loaded.

---

### **Static and Dynamic Linking**
- **Static Linking:** Combines all necessary program modules into a single executable file with no runtime dependencies.
- **Dynamic Linking:** Uses a “stub” to check if a library routine is already in memory. If not, the routine is loaded.

---

### **Swapping**
Swapping temporarily moves processes between main memory and secondary memory to accommodate higher-priority processes.

**Advantages:**
- Allows multiple processes to run.
- Increases CPU utilization.

**Key Point:** Total swap time depends on the amount of memory swapped.

---

### **Memory Management Approaches**
1. **Monoprogramming (Without Swapping):**
   - Memory is divided into two sections: OS and user program.
   - Fence register protects the OS from user programs.

   **Advantages:** Simple.
   **Disadvantages:** Wastes memory, does not support multiprogramming.

2. **Fixed Partitioning (Without Swapping):**
   - Memory is divided into fixed partitions.
   - Each partition is a contiguous block of memory.
   - Uses a partition table to track memory status.

   **Advantages:** Supports multiprogramming.
   **Disadvantages:** Internal fragmentation.

---

### **Logical vs Physical Address Mapping**
- **Logical Address:** Generated by the CPU.
- **Physical Address:** Actual address in memory.
- **Dynamic Relocation:** Hardware maps logical addresses to physical addresses using a base register.

**Example Partition Table:**
| Starting Address | Size  | Status    |
|------------------|-------|-----------|
| 0k               | 200k  | Allocated |
| 200k             | 100k  | Free      |
| 300k             | 150k  | Free      |
| 450k             | 250k  | Allocated |

---

**Contiguous Memory Allocation and Related Concepts**

### **Introduction**
The main memory in a computer system is shared between the operating system and user processes. The allocation of this memory plays a critical role in ensuring efficient resource utilization. Memory is typically divided into two partitions:
1. **Operating System Partition**: Reserved for the OS.
2. **User Partition**: Holds the user processes.

Contiguous memory allocation ensures that each process occupies a single, continuous block of memory. This method is straightforward but can suffer from fragmentation issues.

---

### **Memory Allocation Methods**

#### **1. Multiple Partition Allocation**
- Memory is divided into fixed-sized partitions.
- Each partition holds exactly one process.
- Degree of multiprogramming depends on the number of partitions.
- When a process terminates, its partition is freed for another process.

#### **2. Fixed Partition Allocation**
- The OS maintains a memory table to track available and occupied memory.
- Free memory is represented as "holes."
- Dynamic storage allocation methods are used to allocate memory efficiently:
  - **First Fit**: Allocates the first hole that is large enough.
  - **Best Fit**: Allocates the smallest hole that can satisfy the process’s requirements.
  - **Worst Fit**: Allocates the largest available hole.

---

### **Dynamic Storage Allocation Techniques**

#### **First Fit**
- Allocates the first sufficiently large hole.
- Simple and fast.
- Example: A process requiring 25 KB is allocated to the first 40 KB hole.

#### **Best Fit**
- Allocates the smallest hole that can fulfill the process requirements.
- Requires searching the entire list of holes.
- Maximizes memory utilization.
- Example: A 25 KB process is allocated to a 25 KB hole.

#### **Worst Fit**
- Allocates the largest available hole.
- Often results in inefficient memory utilization.
- Example: A 25 KB process is allocated to a 60 KB hole, leaving a large unused space.

---

### **Fragmentation**
Fragmentation occurs due to inefficient memory allocation, leading to wasted memory:

#### **Internal Fragmentation**
- Happens when a process is allocated more memory than it requests.
- Example: A 2 MB process allocated a 3 MB block leaves 1 MB unused.

#### **External Fragmentation**
- Free memory exists, but it is non-contiguous and cannot satisfy process requirements.
- Example: Several small free blocks exist, but none are large enough to meet a process’s needs.

#### **Solutions to Fragmentation**
1. **Compaction**: Combines all free memory into one large block.
2. **Non-Contiguous Allocation**: Allows logical address space to be spread across multiple non-contiguous physical memory locations.

---

### **Paging**
Paging eliminates the need for contiguous allocation by dividing memory into fixed-size blocks:
- **Frames**: Fixed-size blocks of physical memory.
- **Pages**: Fixed-size blocks of logical memory.
- **Page Size = Frame Size**.

#### **Address Translation**
1. **Logical Address (Virtual Address)**: Generated by the CPU.
2. **Physical Address**: Mapped from the logical address by the Memory Management Unit (MMU).
3. **Page Table**: Maps logical pages to physical frames.

#### **Address Components**
- **Logical Address**: Divided into:
  - **Page Number (p)**: Identifies the page.
  - **Page Offset (d)**: Identifies the specific location within the page.
- **Physical Address**: Divided into:
  - **Frame Number (f)**: Identifies the frame.
  - **Frame Offset (d)**: Identifies the specific location within the frame.

#### **Translation Lookaside Buffer (TLB)**
- A small, high-speed cache used to reduce page table lookup time.
- Stores recently used page-to-frame mappings.
- Access mechanism:
  - If the page is found in TLB, the frame number is retrieved directly.
  - If not, the page table in main memory is accessed.

#### **Effective Access Time (EAT)**
If the page table is in main memory:
- **EAT = m (page table access time) + m (data access time)**.

---

### **Advantages of Paging**
- Eliminates external fragmentation.
- Allows processes to use non-contiguous memory.
- Simplifies memory management.

### **Disadvantages of Paging**
- Internal fragmentation may still occur if the process size is not an exact multiple of the page size.
- Page table overhead increases with the size of logical address space.
- TLB misses can lead to performance degradation.

---

### **Summary**
Contiguous memory allocation provides simplicity but suffers from fragmentation. Dynamic allocation methods like First Fit, Best Fit, and Worst Fit help manage memory but have trade-offs. Paging addresses many limitations of contiguous allocation by allowing non-contiguous memory usage but introduces its own set of challenges like overhead and potential internal fragmentation. Techniques like compaction and TLBs further enhance memory management efficiency.

**Gfg Link :** https://www.geeksforgeeks.org/memory-management-in-operating-system/
