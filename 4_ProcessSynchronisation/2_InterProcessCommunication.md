### Interprocess Communication (IPC) – Complete Notes

Interprocess Communication (IPC) refers to the mechanisms that allow processes to exchange data and coordinate their activities. IPC is fundamental in operating systems to ensure efficient and coherent execution of multiple processes.

---

### **Key Concepts in IPC**

1. **Process**  
   - A process is an instance of a program in execution. Each process operates in its own address space and may need to communicate with other processes.

2. **Communication Mechanisms**  
   IPC provides several methods for processes to communicate, including shared memory, message passing, signals, and sockets.

3. **Synchronization**  
   Processes must coordinate access to shared resources to avoid conflicts, achieved using synchronization primitives like semaphores and mutexes.

---

### **Types of IPC Mechanisms**

1. **Shared Memory**  
   - Definition: A portion of memory that can be accessed by multiple processes for reading and writing.  
   - Key Points:
     - Fast communication as memory access is quicker than system calls.
     - Requires synchronization to manage concurrent access.

2. **Message Passing**  
   - Definition: A mechanism where processes communicate by sending and receiving messages.  
   - Key Points:
     - Suitable for distributed systems.
     - Can be synchronous (blocking) or asynchronous (non-blocking).

3. **Pipes**  
   - Definition: Unidirectional communication channels allowing data flow between processes.  
   - Key Points:
     - Two types: Named pipes (FIFO) and unnamed pipes.
     - Used for parent-child process communication.

4. **Sockets**  
   - Definition: An endpoint for communication between processes, often over a network.  
   - Key Points:
     - Supports bidirectional communication.
     - Commonly used in client-server architectures.

5. **Signals**  
   - Definition: Notifications sent to a process to indicate an event or interrupt its execution.  
   - Key Points:
     - Examples: SIGKILL (terminate), SIGSTOP (pause).
     - Limited data transfer capability.

6. **Semaphores**  
   - Definition: Synchronization primitives that control access to shared resources using counters.  
   - Key Points:
     - Types: Binary semaphore (mutex) and counting semaphore.
     - Prevents race conditions and ensures mutual exclusion.

7. **Message Queues**  
   - Definition: A data structure maintained by the OS to store messages until the receiving process retrieves them.  
   - Key Points:
     - Allows asynchronous communication.
     - Supports prioritization of messages.

8. **Mmap (Memory Mapping)**  
   - Definition: A method of mapping files or devices into memory.  
   - Key Points:
     - Allows multiple processes to access the same memory-mapped file.

---

### **Examples of IPC in Real-World Scenarios**

1. **Operating Systems:** Shared memory is used for communication between user applications and the kernel.  
2. **Distributed Systems:** Message passing enables communication between nodes in a network.  
3. **Web Servers:** Sockets facilitate data transfer between clients and servers.

---

### **Advantages of IPC**

1. Allows modular programming by enabling separate processes to communicate.  
2. Improves resource utilization through shared access.  
3. Facilitates distributed computing and parallelism.

---

### **Disadvantages of IPC**

1. Complexity in synchronization and error handling.  
2. Potential performance overhead in mechanisms like message passing.  
3. Susceptibility to deadlocks and race conditions.

---

### **Synchronization Tools in IPC**

1. **Mutex (Mutual Exclusion Object)**  
   - Ensures that only one process accesses a shared resource.  
2. **Condition Variables**  
   - Used to block a process until a particular condition is true.  
3. **Spinlocks**  
   - Busy-wait locks that repeatedly check a condition without sleeping.

---

### **Key Points for Competitive Exams**

1. **Shared Memory vs. Message Passing**  
   - Shared memory is faster but requires synchronization, while message passing is simpler but incurs kernel overhead.

2. **FIFO in Pipes**  
   - First-In-First-Out (FIFO) ensures order of message delivery in named pipes.

3. **POSIX IPC**  
   - A standard for IPC mechanisms including semaphores, message queues, and shared memory.

4. **Sockets in IPC**  
   - Essential for networking-based IPC, supporting TCP and UDP communication.

---
