
### What is Process Scheduling?

- **Definition**: Process scheduling is the action performed by the OS to decide the execution order of processes on the CPU.
- **Purpose**: To manage and allocate CPU time among various competing tasks in a multiprogramming environment, ensuring optimal utilization of resources and system responsiveness.
- **Importance**: Crucial for multitasking systems, where multiple processes need CPU time efficiently and fairly.

### Types of Process Scheduling Strategies

1. **Non-Preemptive Scheduling**:
   - Once a process starts using CPU resources, it cannot be interrupted until it completes or enters a waiting state.
   - Ideal for batch systems but can lead to high waiting times for shorter tasks.

2. **Preemptive Scheduling**:
   - The OS can interrupt a process and reallocate CPU resources based on priority or time slicing.
   - Supports real-time applications by ensuring higher-priority tasks receive CPU resources quickly.

---

### Types of Process Schedulers

1. **Long-Term (Job) Scheduler**:
   - **Role**: Selects and loads processes into memory, determining which jobs or processes enter the ready state.
   - **Purpose**: Manages multiprogramming degree (number of processes in memory).
   - **Focus**: Balances **CPU-bound** (use CPU intensively) and **I/O-bound** (spend time waiting for I/O) processes.
   - **Efficiency**: Enhances system efficiency by balancing tasks, commonly used in batch systems.
   - **Competitive Edge**: It’s typically not present in time-sharing systems due to the focus on fast response times.

2. **Short-Term (CPU) Scheduler**:
   - **Role**: Selects processes from the ready queue for CPU allocation.
   - **Responsibility**: Ensures efficient CPU utilization and manages the transition between the ready and running states.
   - **Dispatcher**:
     - Loads the selected process onto the CPU.
     - Handles **context switching** (saving the state of the interrupted process).
     - **Note**: The dispatcher is separate from the short-term scheduler; it implements the scheduling decision.
   - **Competitive Edge**: Effective in minimizing starvation in systems with priority-based scheduling.

3. **Medium-Term Scheduler**:
   - **Role**: Manages process swapping between main memory and disk.
   - **Function**: Controls processes by **suspending** (moving to disk) and **resuming** (loading back to memory) as memory availability changes.
   - **Purpose**: Maintains a balance between I/O and CPU-bound processes and reduces CPU idle time.
   - **Competitive Edge**: Helps maintain optimal multiprogramming levels in real-time and time-sharing systems by suspending processes to manage memory better.

4. **Other Specialized Schedulers**:
   - **I/O Scheduler**: Manages I/O requests by determining their execution order to optimize I/O performance (e.g., **FCFS** and **RR** scheduling).
   - **Real-Time Scheduler**: Ensures critical tasks complete within their required timeframes, using algorithms like **EDF** (Earliest Deadline First) and **RM** (Rate Monotonic).

---

### Process State Transitions

- **Two-State Process Model**:
  - **Running State**: The process actively executes instructions on the CPU.
  - **Not-Running State**: The process waits in a queue, with a pointer to its PCB, awaiting CPU allocation.

- **Multistate Process Model** (common in multiprogramming):
  - **New**: Process is created.
  - **Ready**: Process is prepared for execution.
  - **Running**: Process currently executing on the CPU.
  - **Waiting**: Process waiting for I/O completion.
  - **Terminated**: Process completed and resources are deallocated.

---

### Context Switching

- **Definition**: Mechanism to save and restore the state (context) of a CPU so that a process can resume from the same point later.
- **Significance**: Enables multiple processes to share the CPU efficiently, allowing multitasking.
- **Process**:
  - Saves the current process state to its **Process Control Block (PCB)**.
  - Loads the next process’s state from its PCB into the CPU registers.
  - Requires CPU time and memory, adding **overhead** to the system.
- **Exam Tip**: Understand the importance of minimal overhead in context switching for real-time and high-performance systems.

---

### Categories of Scheduling Algorithms

1. **Non-Preemptive Algorithms**:
   - **First-Come, First-Served (FCFS)**: Processes are executed in the order they arrive, potentially causing **Convoy Effect** (long processes delay short ones).
   - **Shortest Job Next (SJN)**: Executes the process with the shortest burst time first, reducing average waiting time. However, it's susceptible to **starvation** for longer processes.

2. **Preemptive Algorithms**:
   - **Round Robin (RR)**: Each process receives a fixed time slice (quantum); suitable for time-sharing systems and fair CPU time distribution.
   - **Priority Scheduling**: Assigns CPU based on priority levels, allowing preemption for high-priority tasks.
   - **Shortest Remaining Time First (SRTF)**: Preemptive variant of SJN; process with the shortest remaining burst time is executed next.
   - **Multilevel Queue**: Separates processes into different queues based on priority or type (e.g., system vs. user), each with its scheduling algorithm.

---

### Comparison of Scheduler Types

| **Long-Term Scheduler**        | **Short-Term Scheduler**       | **Medium-Term Scheduler**       |
|--------------------------------|--------------------------------|----------------------------------|
| Manages **job scheduling**.    | Manages **CPU scheduling**.    | Manages **process swapping**.    |
| Operates slower than short-term schedulers. | Fastest of all schedulers.        | Speed lies between long and short-term schedulers. |
| Controls **degree of multiprogramming**. | Less control over multiprogramming. | Reduces multiprogramming by suspending processes. |
| Often absent in time-sharing systems. | Essential in time-sharing systems. | Used in time-sharing systems to maintain balance. |

---

### Exam-Oriented Additional Points

- **Starvation**: Occurs in priority-based systems where lower-priority tasks may never get CPU time.
- **Aging**: Technique used to prevent starvation by gradually increasing the priority of waiting processes.
- **Scheduler Efficiency**: Critical for optimizing **turnaround time**, **waiting time**, **throughput**, and **CPU utilization**.
- **Deadlock Prevention**: Real-time schedulers often prioritize avoiding deadlocks to ensure critical processes meet deadlines.

### Conclusion

Process schedulers are essential to OS functioning, managing process execution and resource allocation. A strong understanding of scheduling algorithms, process states, and types of schedulers can enhance exam performance by allowing accurate predictions of CPU behavior and efficient multitasking approaches.

---
