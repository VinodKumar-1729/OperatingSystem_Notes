### Process Scheduling

#### What is Process Scheduling?
Process scheduling is a key activity of the process manager in an operating system. It involves removing a running process from the CPU and selecting another process for execution based on a particular strategy. This activity is critical in multiprogramming operating systems, where multiple processes share the CPU using time multiplexing.

#### Importance of Process Scheduling
Process schedulers are integral to operating systems as they decide the order in which processes compete for CPU time. Effective scheduling ensures:
- Efficient utilization of CPU resources.
- Fair allocation of resources among processes.
- Improved system performance and responsiveness.

### Categories of Scheduling

1. **Non-Preemptive Scheduling:**
   - Resources assigned to a process cannot be taken away until the process has finished.
   - Switching of resources occurs only when a process transitions to a waiting state or completes execution.

2. **Preemptive Scheduling:**
   - The operating system allocates resources to a process for a predefined time period.
   - A process can be moved from a running state to a ready state to give priority to higher-priority processes.

### Types of Process Schedulers

1. **Long-Term (Job) Scheduler:**
   - Brings new processes to the ready state.
   - Controls the degree of multiprogramming by balancing I/O-bound and CPU-bound processes.
   - Operates at a high level, typically in batch-processing systems.

2. **Short-Term (CPU) Scheduler:**
   - Selects processes from the ready queue for execution on the CPU.
   - Uses various scheduling algorithms such as FCFS, Round Robin, Priority Scheduling, etc.
   - Prevents starvation by ensuring that high-burst-time processes do not block others.
   
3. **Medium-Term Scheduler:**
   - Responsible for suspending and resuming processes.
   - Performs swapping—moving processes between main memory and disk to optimize the process mix.
   - Helps maintain balance between CPU-bound and I/O-bound processes.

### Additional Schedulers

1. **I/O Schedulers:**
   - Manage execution of I/O operations such as disk or network access.
   - Use algorithms like FCFS or Round Robin for optimal performance.

2. **Real-Time Schedulers:**
   - Used in real-time systems to ensure tasks meet their deadlines.
   - Algorithms include EDF (Earliest Deadline First) and RM (Rate Monotonic Scheduling).

### Comparison of Process Schedulers
| **Feature**               | **Long-Term Scheduler** | **Short-Term Scheduler** | **Medium-Term Scheduler** |
|---------------------------|--------------------------|---------------------------|---------------------------|
| **Function**              | Job scheduling          | CPU scheduling            | Process swapping          |
| **Speed**                 | Slow                    | Fast                      | Moderate                  |
| **Degree of Multiprogramming Control** | High                    | Low                       | Moderate                  |
| **Presence in Time-Sharing Systems** | Rarely used            | Always used              | Commonly used             |
| **Action on Processes**   | Moves new processes to memory | Selects processes for execution | Suspends and resumes processes |

### Two-State Process Model

The two-state process model uses the terms "running" and "non-running" states:

1. **Running:**
   - Processes currently being executed by the CPU.

2. **Non-Running:**
   - Processes waiting in a queue for execution. These processes are managed using linked lists, with the dispatcher selecting processes for execution.

### Role of the Dispatcher
The dispatcher is a critical component of the short-term scheduler, responsible for:
- Switching context.
- Switching the CPU to user mode.
- Jumping to the proper location in the newly loaded program.

### Conclusion
Process scheduling is a fundamental aspect of operating systems, enabling efficient and fair allocation of CPU resources. By managing the execution order of tasks, schedulers optimize performance, ensure system responsiveness, and maintain fairness among processes.

**GFG Link :** https://www.geeksforgeeks.org/process-schedulers-in-operating-system/
