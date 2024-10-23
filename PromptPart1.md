Here’s the first set of detailed prompts, ensuring every concept under your "Infra Support" exam preparation is covered thoroughly, including topics like CPU scheduling algorithms and subtopics that were previously missing.

---

### 1. **System Calls**

#### a) **Basics of System Calls**
- What are system calls? Explain their purpose in an operating system.
- Differentiate between user mode and kernel mode.
- Discuss the various types of system calls (Process Control, File Management, Device Management, Information Maintenance, Communication).
- MCQs on system call types and functions.
  
#### b) **System Call Implementations**
- How are system calls implemented? Explain the process of handling system calls through the interrupt mechanism.
- Practice questions on the role of system calls in context switching and process creation.

---

### 2. **Processes and Threads**

#### a) **Processes**
- What is a process in an operating system? How is it different from a program?
- Explain the process states (New, Ready, Running, Waiting, Terminated).
- What is a Process Control Block (PCB)? Discuss its role in process management.
  
#### b) **Threads**
- What is a thread? Differentiate between single-threaded and multi-threaded processes.
- Discuss user-level vs kernel-level threads.
- What are the advantages of multi-threading? Explain with examples.
  
#### c) **Multithreading Models**
- Explain the different multithreading models (Many-to-One, One-to-One, Many-to-Many).
- MCQs on processes, threads, and multithreading models.
  
---

### 3. **Inter-Process Communication (IPC)**

#### a) **Basics of IPC**
- What is Inter-Process Communication (IPC)? Why is it important?
- Discuss various IPC mechanisms (Shared Memory, Message Passing, Pipes, Semaphores, Sockets).
  
#### b) **Message Passing vs Shared Memory**
- Compare the message-passing model with the shared-memory model.
  
#### c) **Practical Examples**
- What is the role of IPC in client-server communication?
- Solve numerical questions on the speed and efficiency of IPC methods.
- MCQs on IPC mechanisms and scenarios.

---

### 4. **Concurrency and Synchronization**

#### a) **Basics of Concurrency**
- What is concurrency in operating systems? How does it differ from parallelism?
  
#### b) **Process Synchronization**
- What is the critical section problem? Explain why process synchronization is important.
  
#### c) **Peterson’s Solution**
- Explain Peterson’s solution for the critical section problem. Discuss its limitations.
  
#### d) **Semaphores and Mutexes**
- What is a semaphore? How is it used for process synchronization?
- Compare semaphores with mutexes.
  
#### e) **Monitors**
- What are monitors in the context of synchronization? Explain how they differ from semaphores.
  
#### f) **Producer-Consumer Problem**
- What is the producer-consumer problem? Explain the solution using semaphores.
- Solve numerical questions on semaphore values during process execution.

#### g) **Dining Philosophers Problem**
- What is the dining philosophers problem? Explain a solution using semaphores or monitors.
  
#### h) **Readers-Writers Problem**
- What is the readers-writers problem? How do you prevent writer starvation?
- Solve MCQs and scenario-based questions on process synchronization.

---

### 5. **Deadlock**

#### a) **Basics of Deadlock**
- What is deadlock? Explain the four necessary conditions for deadlock.
  
#### b) **Deadlock Prevention**
- How can deadlock be prevented? Discuss different methods (Mutual Exclusion, Hold and Wait, No Preemption, Circular Wait).
  
#### c) **Deadlock Avoidance**
- What is deadlock avoidance? Explain the Banker’s Algorithm in detail.
- Solve numerical problems using the Banker’s Algorithm.
  
#### d) **Deadlock Detection**
- How is deadlock detected? Discuss the role of resource allocation graphs.
- MCQs and problems on deadlock prevention, detection, and avoidance.

---

### 6. **Memory Management and Virtual Memory**

#### a) **Memory Management Basics**
- What is memory management? Discuss the role of the operating system in memory allocation and deallocation.
  
#### b) **Contiguous vs Non-Contiguous Allocation**
- What is the difference between contiguous and non-contiguous memory allocation? Discuss fixed and dynamic partitioning.
  
#### c) **Paging and Segmentation**
- Explain paging and segmentation. How do they help in memory management?
- MCQs and problems on paging and segmentation.

#### d) **Virtual Memory**
- What is virtual memory? Explain the concepts of demand paging and page swapping.
- How do operating systems manage virtual memory using page tables?
- Solve numerical problems on virtual memory and address translation.
  
#### e) **Page Fault Handling**
- What is a page fault? How does the operating system handle page faults?
- Practice questions on page faults and their impact on system performance.

---

### 7. **CPU Scheduling Algorithms**

#### a) **First-Come, First-Served (FCFS)**
- What is the FCFS scheduling algorithm? Discuss its advantages and disadvantages.
- Numerical problems on average wait time and turnaround time using FCFS.

#### b) **Shortest Job First (SJF)**
- Explain the Shortest Job First (SJF) algorithm. Discuss preemptive and non-preemptive versions.
- Numerical problems on average waiting time using SJF (with and without preemption).
  
#### c) **Shortest Remaining Time First (SRTF)**
- What is Shortest Remaining Time First (SRTF)? How does it work compared to SJF?
- Solve numerical problems on SRTF with process arrival times.
  
#### d) **Round Robin (RR)**
- What is the Round Robin (RR) scheduling algorithm? How does time quantum impact performance?
- Numerical problems on average waiting time using RR.
  
#### e) **Priority Scheduling**
- What is priority scheduling? How does it handle processes with different priorities?
- Discuss priority inversion and ways to prevent it.
- Solve numerical problems on priority scheduling with preemption.
  
#### f) **Multilevel Queue Scheduling**
- What is multilevel queue scheduling? Explain how different processes are handled in separate queues.
  
#### g) **Multilevel Feedback Queue Scheduling**
- What is multilevel feedback queue scheduling? How does it dynamically adjust process priority?
- Solve numerical problems on multilevel feedback queue scheduling.
- MCQs on CPU scheduling algorithms and their real-world applications.

---

### 8. **Types of Memories: Cache, Main Memory, and Secondary Storage**

#### a) **Cache Memory**
- What is cache memory? Explain its importance in improving CPU performance.
- Discuss the different levels of cache (L1, L2, L3) and their roles.
  
#### b) **Main Memory (RAM)**
- What is main memory? Explain the role of RAM in storing data during execution.
  
#### c) **Secondary Storage**
- What is secondary storage? Compare HDDs and SSDs in terms of performance, reliability, and cost.
- MCQs on memory types and their characteristics.
  
#### d) **Memory Hierarchy**
- What is the memory hierarchy in computing systems? Discuss the speed, cost, and size trade-offs in the hierarchy.

---

### 9. **Paging and Page Replacement Algorithms**

#### a) **FIFO Page Replacement**
- What is the FIFO page replacement algorithm? Discuss its advantages and disadvantages.
- Solve numerical problems using FIFO to calculate page faults.
  
#### b) **Optimal Page Replacement**
- What is the optimal page replacement algorithm? Why is it considered optimal?
- Numerical problems using Optimal Page Replacement.
  
#### c) **Least Recently Used (LRU)**
- What is the LRU page replacement algorithm? How does it track page usage?
- Solve numerical problems on page faults using LRU.
  
#### d) **Additional Algorithms**
- Explain Clock, Second Chance, and Counting-Based page replacement algorithms.
- Compare FIFO, LRU, and Optimal algorithms in real-world scenarios.
- Solve MCQs and numerical problems on page replacement algorithms.

---

I will provide the remaining prompts in the second response, which will cover I/O scheduling, virtualization, storage solutions, networking, and additional topics.

Let me know if you are ready for the next set!
