### Process Management in Operating Systems

#### What is a Process?
A process is a program in execution. For example, when we write a program in C or C++ and compile it, the compiler creates binary code. Both the original code and the binary code are programs. When the binary code is executed, it becomes a process. Unlike a program, which is a ‘passive’ entity, a process is an ‘active’ entity. A single program can create multiple processes when run multiple times. For instance, opening a binary file (.exe) multiple times creates multiple instances (processes).

#### What is Process Management?
Process management is a key function of an operating system (OS) that controls how processes are created, executed, and terminated. It ensures efficient system performance by managing active processes and resources. The OS prevents deadlocks, facilitates inter-process communication, and ensures synchronization among processes.

Key aspects of process management include:
- Starting and stopping processes.
- Scheduling processes to optimize CPU utilization and system responsiveness.
- Ensuring efficient resource allocation and conflict-free execution.
- Supporting multitasking for enhanced system utilization and responsiveness.

#### Process Representation in Memory
A process in memory consists of the following sections:
- **Text Section**: Contains the program code and the current activity represented by the Program Counter.
- **Stack**: Stores temporary data, including function parameters, return addresses, and local variables.
- **Data Section**: Contains global variables.
- **Heap Section**: Dynamically allocated memory during runtime.

#### Characteristics of a Process
A process has the following attributes:
- **Process ID**: A unique identifier assigned by the OS.
- **Process State**: Can be New, Ready, Running, Waiting, or Terminated.
- **CPU Registers**: Includes the Program Counter, which is saved and restored during context switches.
- **Accounts Information**: Includes execution time, CPU usage, and execution ID.
- **I/O Status Information**: Tracks devices allocated to the process and open files.
- **CPU Scheduling Information**: Includes priority and scheduling details.

All these attributes are stored in the Process Control Block (PCB), which is unique to each process.

#### Process States
A process can be in one of the following states:
1. **New**: Process is being created.
2. **Ready**: Process is ready for execution.
3. **Running**: Process is actively being executed by the CPU.
4. **Waiting (Blocked)**: Process is waiting for I/O operations to complete.
5. **Terminated (Complete)**: Process has finished execution.
6. **Suspended Ready**: Ready processes moved to suspended state due to a full ready queue.
7. **Suspended Block**: Waiting processes moved to suspended state due to a full waiting queue.

#### Process Operations
Key operations include:
- **Process Creation**: Generating a new process instance.
- **Scheduling**: Selecting a process from the ready queue for execution.
- **Execution**: CPU works on the selected process.
- **Killing a Process**: Terminating a process and removing its PCB after task completion.

#### Context Switching
Context switching involves saving the current process state and loading another process’s state. It is triggered by:
- Arrival of a high-priority process.
- Interrupts.
- Preemptive CPU scheduling.

#### Mode Switch vs Context Switch
- **Mode Switch**: Occurs when the CPU privilege level changes (e.g., during a system call). It doesn’t necessarily involve switching processes.
- **Context Switch**: Involves switching from one process to another and is initiated by the kernel.

#### CPU-Bound vs I/O-Bound Processes
- **CPU-Bound Processes**: Spend more time in the running state and require extensive CPU resources.
- **I/O-Bound Processes**: Spend more time waiting for I/O operations and require fewer CPU resources.

#### Process Scheduling
The OS determines which process to run next using scheduling algorithms to optimize CPU utilization, minimize execution time, and improve system responsiveness.

**Common Scheduling Algorithms:**
1. **First-Come, First-Served (FCFS)**: Non-preemptive, processes are executed in the order of arrival.
2. **Shortest Job First (SJF)**: Executes the process with the shortest burst time, minimizing average waiting time.
3. **Round Robin (RR)**: Allocates fixed time slices to each process, ensuring fairness and avoiding starvation.
4. **Priority Scheduling**: Executes the highest-priority process first.
5. **Multilevel Queue**: Divides the ready queue into multiple queues, each with its own scheduling algorithm.

#### Advantages of Process Management
- **Concurrent Execution**: Enables running multiple programs simultaneously.
- **Process Isolation**: Prevents interference between programs.
- **Efficient Resource Sharing**: Ensures fair allocation of CPU, memory, and other resources.
- **System Responsiveness**: Handles smooth switching between programs, minimizing delays.

#### Disadvantages of Process Management
- **Overhead**: Requires CPU time and memory for maintaining data structures and queues.
- **Complexity**: Involves designing complex scheduling algorithms and resource allocation methods.
- **Deadlocks**: Risks of processes getting stuck indefinitely while waiting for resources.
- **Context Switching Overhead**: Frequent switching can reduce system efficiency.

#### Conclusion
Process management is a fundamental aspect of operating systems, enabling the efficient execution of multiple programs. It involves process creation, scheduling, and termination, along with resource management and inter-process communication. Effective process management enhances system stability, optimizes resource utilization, and ensures a responsive computing environment.

**GFG Link :** https://www.geeksforgeeks.org/introduction-of-process-management/
