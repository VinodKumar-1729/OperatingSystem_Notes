### **Process Scheduling and Types of Schedulers:**

---

### **1. Definition of Process Scheduling**
- **Process Scheduling** is the method used by the operating system to allocate the CPU and other resources to processes.
- It ensures efficient utilization of the CPU, maximizes throughput, and provides fairness among processes.
- In multitasking and multi-user systems, the scheduler decides:
  - **Which process to run?**
  - **When to run a process?**
  - **For how long to run a process?**

---

### **2. Objectives of Process Scheduling**
1. **Maximize CPU Utilization:** Keep the CPU as busy as possible.
2. **Maximize Throughput:** Complete the maximum number of processes in the shortest time.
3. **Minimize Turnaround Time:** Reduce the time a process takes from submission to completion.
4. **Minimize Waiting Time:** Reduce the time a process spends in the ready queue.
5. **Minimize Response Time:** Provide quick feedback to interactive processes.
6. **Fairness:** Ensure all processes are treated equally without starvation.

---

### **3. Process Scheduling Levels**
Process scheduling is divided into three levels, based on the type of decisions being made:

#### **(i) High-Level Scheduling (Long-Term Scheduler)**
- Determines **which processes should enter the ready queue** for execution.
- Runs infrequently (e.g., when a new process is created).
- Controls the degree of **multiprogramming** (number of processes in memory at a time).
  
##### **Characteristics:**
- Focuses on admission control to balance the load on the system.
- Affects system performance and throughput.
  
##### **Example:**
- Admitting a new batch job in a batch-processing system.

---

#### **(ii) Mid-Level Scheduling (Medium-Term Scheduler)**
- Manages **process swapping** between memory and secondary storage.
- Suspends or resumes processes based on system conditions (e.g., freeing memory).
- Typically used in **time-sharing systems**.

##### **Characteristics:**
- Temporarily removes processes from memory to reduce the load (swapping out).
- Resumes suspended processes when resources are available (swapping in).

##### **Example:**
- Suspending a background process to prioritize an interactive process.

---

#### **(iii) Low-Level Scheduling (Short-Term Scheduler)**
- Determines **which process in the ready queue should execute next** on the CPU.
- Runs frequently, typically at every CPU time slice or event.
- Also called the **CPU Scheduler**.

##### **Characteristics:**
- Very fast decision-making as it operates frequently.
- Uses CPU scheduling algorithms (e.g., FCFS, Round Robin, Priority Scheduling).

##### **Example:**
- Allocating CPU to the next process in a Round Robin scheduling system.

---


### **5. CPU Scheduling Criteria**
The short-term scheduler selects processes based on the following criteria:
1. **CPU Utilization:** Maximize CPU usage.
2. **Throughput:** Number of processes completed per unit time.
3. **Turnaround Time:** Total time taken from submission to completion.
4. **Waiting Time:** Time spent in the ready queue.
5. **Response Time:** Time between request submission and first response.

---

### **6. Scheduling Algorithms**
Scheduling algorithms determine the behavior of the short-term scheduler. Examples include:
1. **First-Come, First-Served (FCFS):** Executes processes in the order they arrive.
2. **Shortest Job Next (SJN):** Selects the process with the shortest execution time.
3. **Round Robin (RR):** Allocates CPU in time slices, cycling through processes.
4. **Priority Scheduling:** Assigns priority levels; higher-priority processes execute first.
5. **Multilevel Queue Scheduling:** Segregates processes into different queues based on priority.
6. **Multilevel Feedback Queue Scheduling:** Allows dynamic queue adjustments based on behavior.

---

### **7. Summary Table**

| **Type of Scheduler**  | **Primary Role**                                     | **Frequency**       | **Focus**                          |
|------------------------|-----------------------------------------------------|---------------------|------------------------------------|
| **Long-Term Scheduler** | Determines admission of processes into the system.  | Low (infrequent)    | Balances system load.              |
| **Medium-Term Scheduler** | Swaps processes in/out of memory.                  | Moderate            | Reduces memory load.               |
| **Short-Term Scheduler** | Allocates CPU to processes in the ready queue.      | High (frequent)     | Minimizes response/waiting time.   |

---

### **8. Additional Key Points**
- **Preemptive Scheduling:** The CPU can be forcibly taken from a running process (e.g., Round Robin, Priority with preemption).
- **Non-Preemptive Scheduling:** The CPU is not taken from a running process until it finishes (e.g., FCFS, SJF without preemption).
- The efficiency of the scheduler impacts overall system performance significantly.

---
