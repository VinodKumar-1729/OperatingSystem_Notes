### CPU Scheduling

---

**CPU Scheduling Overview**  
CPU scheduling is a crucial part of operating system functionality. It determines which process gets access to the CPU at any given time to ensure efficient use of the processor. Since multiple programs may run simultaneously, the operating system manages CPU time to maximize system performance and fairness.

The primary goals of CPU scheduling are:  
1. **Efficiency**: Ensuring optimal utilization of the CPU.  
2. **Fairness**: Giving each process a reasonable chance to execute.  
3. **Responsiveness**: Providing prompt execution of user requests.

---

**Why is CPU Scheduling Needed?**  
1. **Efficient Resource Utilization**: In multiprogramming environments, if too many I/O-bound processes are selected, the CPU may remain idle. Proper scheduling ensures better resource utilization.  
2. **Prevent Deadlocks**: A well-designed scheduling algorithm minimizes idle time and reduces the risk of system deadlock caused by prolonged waiting states.  
3. **Concurrency Management**: Helps the operating system manage multiple processes effectively by prioritizing tasks.  

---

**Key Terminologies in CPU Scheduling**  

1. **Arrival Time**: Time when a process enters the ready queue.  
2. **Burst Time**: The CPU time required for process execution.  
3. **Completion Time**: The time at which a process finishes execution.  
4. **Turnaround Time (TAT)**: The total time taken from process arrival to completion.  
   **Formula**:  
   \[
   TAT = Completion \, Time - Arrival \, Time
   \]
5. **Waiting Time (WT)**: Time a process spends waiting in the ready queue.  
   **Formula**:  
   \[
   WT = Turnaround \, Time - Burst \, Time
   \]
6. **Response Time (RT)**: Time from when a process enters the ready queue to when it receives its first response.  

---

**Key Metrics for CPU Scheduling Algorithm Design**  

1. **CPU Utilization**:  
   - Objective: Maximize CPU usage (ranges from 40% to 90% in real systems).  
2. **Throughput**:  
   - Number of processes completed per unit time.  
   - Higher throughput indicates better CPU performance.  
3. **Turnaround Time**:  
   - Total time taken for a process to complete, including waiting and execution.  
   - **Optimization Goal**: Minimize turnaround time.  
4. **Waiting Time**:  
   - Time spent by processes in the ready queue before execution.  
   - **Optimization Goal**: Minimize waiting time.  
5. **Response Time**:  
   - Time taken to respond to a process's request for the first time.  
   - Crucial for interactive systems where prompt user feedback is required.  

---

**Design Considerations for CPU Scheduling Algorithms**  

- **Nature of Processes**: Balance between CPU-bound and I/O-bound processes.  
- **System Goals**: Focus on maximizing throughput and CPU utilization while minimizing turnaround, waiting, and response times.  
- **Fairness**: Ensure no process is indefinitely postponed (avoiding starvation).  
- **Preemption**: Decide whether processes can be interrupted to switch to higher-priority tasks.  

---

### CPU Scheduling Algorithms:

#### 1. **First Come First Serve (FCFS)**
**Description:**
- Simplest CPU scheduling algorithm.
- Processes are executed in the order they arrive (FIFO queue).

**Characteristics:**
- Supports both non-preemptive and preemptive scheduling.
- Simple and easy to implement.
- High waiting time due to the Convoy Effect.

**Advantages:**
- Easy to implement.
- Follows a straightforward first-come, first-serve approach.

**Disadvantages:**
- Suffers from the Convoy Effect.
- Higher average waiting time compared to other algorithms.

---

#### 2. **Shortest Job First (SJF)**
**Description:**
- Executes processes with the smallest burst time first.
- Can be preemptive or non-preemptive.

**Characteristics:**
- Minimum average waiting time among all scheduling algorithms.
- Associated with each task’s time-to-completion unit.
- Starvation possible for longer jobs; resolved with aging.

**Advantages:**
- Lower average waiting time.
- Efficient for long-term scheduling.

**Disadvantages:**
- Predicting burst time is challenging.
- Prone to starvation for longer jobs.

---

#### 3. **Longest Job First (LJF)**
**Description:**
- Opposite of SJF; processes with the largest burst time are executed first.
- Non-preemptive by default.

**Characteristics:**
- Ties resolved using FCFS.
- Can be both preemptive and non-preemptive.

**Advantages:**
- Maximizes throughput for long jobs.
- Reduces context switching.

**Disadvantages:**
- High average waiting time and turnaround time.
- Can lead to the Convoy Effect.

---

#### 4. **Priority Scheduling**
**Description:**
- CPU is allocated based on process priority.
- Lower priority numbers indicate higher importance.

**Characteristics:**
- Can be preemptive or non-preemptive.
- Preemption occurs if a higher-priority process arrives during execution.

**Advantages:**
- Lower average waiting time compared to FCFS.
- Less complex.

**Disadvantages:**
- Prone to starvation of lower-priority processes.

---

#### 5. **Round Robin (RR)**
**Description:**
- Processes are cyclically assigned a fixed time slice (time quantum).
- Preemptive version of FCFS.

**Characteristics:**
- Simple, starvation-free.
- Fair allocation of CPU time.

**Advantages:**
- Fair as all processes receive equal time.
- Starvation-free.

**Disadvantages:**
- Performance depends on the choice of time quantum.

---

#### 6. **Shortest Remaining Time First (SRTF)**
**Description:**
- Preemptive version of SJF.
- Process with the shortest remaining time is executed next.

**Characteristics:**
- Frequent context switching.
- Fast processing for short jobs.

**Advantages:**
- Faster execution for shorter processes.
- Minimal overhead due to fewer decision points.

**Disadvantages:**
- Starvation of longer processes.
- High context switching overhead.

---

#### 7. **Longest Remaining Time First (LRTF)**
**Description:**
- Preemptive version of LJF.
- Processes with the longest remaining time are prioritized.

**Characteristics:**
- Ties resolved using FCFS.
- Prioritizes long tasks for completion.

**Advantages:**
- Maximizes throughput for long processes.
- Simpler to implement.

**Disadvantages:**
- High average waiting and turnaround times.
- Prone to the Convoy Effect.

---

#### 8. **Highest Response Ratio Next (HRRN)**
**Description:**
- Non-preemptive algorithm that selects processes based on the highest response ratio.
- Response Ratio = (Waiting Time + Burst Time) / Burst Time

**Characteristics:**
- Reduces starvation compared to SJF.
- Balances shorter and longer jobs effectively.

**Advantages:**
- Better performance than SJF.
- Encourages balance between short and long jobs.

**Disadvantages:**
- Requires knowledge of burst times in advance.
- Overhead in response ratio calculation.

---

#### 9. **Multilevel Queue Scheduling (MLQ)**
**Description:**
- Divides processes into multiple classes with distinct scheduling needs.
- Each class has a separate queue with its own scheduling algorithm.

**Characteristics:**
- Common division: foreground (interactive) and background (batch) processes.
- Fixed assignment of processes to queues.

**Advantages:**
- Low scheduling overhead.
- Tailored scheduling for different types of processes.

**Disadvantages:**
- Starvation possible for lower-priority queues.
- Inflexible due to static queue assignments.

---

#### 10. **Multilevel Feedback Queue Scheduling (MLFQ)**
**Description:**
- Similar to MLQ but processes can move between queues based on execution.
- Dynamically adapts to process behavior.

**Characteristics:**
- Flexible and efficient.
- Balances response time and throughput.

**Advantages:**
- Dynamic queue adjustment reduces starvation.
- Better resource utilization compared to MLQ.

**Disadvantages:**
- High CPU overhead.
- Complex to implement.

---

### Comparison of CPU Scheduling Algorithms
| Algorithm            | Allocation Basis              | Complexity       | Average Waiting Time (AWT)   | Preemption | Starvation | Performance                       |
|----------------------|-------------------------------|------------------|------------------------------|------------|------------|-----------------------------------|
| FCFS                | Arrival time (FIFO)          | Simple           | High                         | No         | No         | Slow                             |
| SJF                 | Shortest burst time          | Moderate         | Low                          | No         | Yes        | Efficient                        |
| LJF                 | Longest burst time           | Moderate         | High                         | No         | Yes        | Inefficient                      |
| LRTF                | Longest remaining time       | High             | High                         | Yes        | Yes        | Preferential to long jobs        |
| SRTF                | Shortest remaining time      | High             | Low                          | Yes        | Yes        | Preferential to short jobs       |
| RR                  | Time quantum                 | Moderate         | Moderate                     | Yes        | No         | Fair                             |
| Priority Scheduling | Process priority             | Low (preemptive) | Moderate                     | Yes/No     | Yes        | Efficient but may starve         |
| MLQ                 | Queue priority               | High             | Moderate                     | No         | Yes        | Good for specialized systems     |
| MLFQ                | Dynamic queue priority       | Very High        | Low                          | Yes        | No         | Flexible and efficient           |
| HRRN                | Highest response ratio       | Moderate         | Low                          | No         | No         | Balances short and long processes|

---

### Key Notes:
1. **Starvation** occurs primarily in Priority and SJF/SRTF algorithms.
2. **Convoy Effect** is prominent in FCFS and LJF/LRTF.
3. **Time Quantum** in Round Robin significantly affects performance and fairness.
4. **Dynamic Adjustment** in MLFQ reduces starvation but increases complexity.

**GFG Link :** https://www.geeksforgeeks.org/cpu-scheduling-in-operating-systems/
