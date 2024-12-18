**Process Lifecycle in Operating Systems**

When a program is executed, it transforms into a process and passes through various phases before completion. These phases, or states, may vary depending on the operating system, but they generally fall into two, five, or seven states.

### **The Two-State Model**
The simplest model of a process’s lifecycle includes two states:

1. **Running**: The process is actively using the CPU for execution.
2. **Not Running**: The process is not currently using the CPU. It may be waiting for input, data, or other resources, or simply paused.

**Steps in the Two-State Model:**
- **Not Running State**: Processes begin in this state after creation.
- **Dispatcher Role**: A dispatcher checks if the CPU is free and assigns it to processes.
- **Moving to Running State**: When the CPU is available, the dispatcher transitions the process to the running state.
- **CPU Scheduler Role**: The CPU scheduler selects the next process to run based on a scheduling scheme specific to the operating system.

### **The Five-State Model**
To better handle processes waiting for resources, the two-state model is expanded into five states:

1. **New**: A newly created process with its Process Control Block (PCB) initialized but not yet loaded into memory.
2. **Ready**: The process is in memory and waiting for CPU allocation.
3. **Running**: The process is actively being executed by the CPU.
4. **Blocked/Waiting**: The process is waiting for an event, such as I/O completion.
5. **Exit/Terminated**: The process has finished execution or been stopped.

### **The Seven-State Model**
For more detailed process management, the seven-state model includes additional states:

1. **New State**: The program exists in secondary storage and is picked up by the OS to create a process.
2. **Ready State**: The process is loaded into main memory and awaits CPU allocation. Processes are queued in a **Ready Queue**.
3. **Run State**: The process’s instructions are executed by the CPU.
4. **Blocked/Wait State**: The process requests I/O or waits for a critical region’s lock to be released.
5. **Terminated/Completed State**: The process is killed or finishes execution, and its resources are deallocated.
6. **Suspend Ready**: A ready process moved to secondary storage due to lack of memory. It re-enters the ready state when swapped back into memory.
7. **Suspend Wait/Suspend Blocked**: A blocked process swapped out due to memory constraints. It transitions back to suspend ready after I/O completion.

### **Process Transitions**
Processes move between states based on execution and resource availability:
- **New to Ready**: Upon allocation of resources.
- **Ready to Running**: CPU is allocated by the scheduler.
- **Running to Blocked**: Process awaits an event or resource.
- **Running to Ready**: Process preempted by a higher-priority task.
- **Blocked to Ready**: Event/resource becomes available.
- **Running to Terminated**: Execution completes or process is killed.

### **Multiprogramming and Process Scheduling**
- **Preemption**: The CPU forcibly switches processes (time-sharing).
- **Non-Preemption**: Processes run to completion without interruption.
- **Degree of Multiprogramming**: The maximum number of processes that can reside in the ready state.

### **Key Operations on Processes**
1. **Creation**: A new process is created and enters the ready state.
2. **Scheduling**: The OS selects a process from the ready queue for execution.
3. **Execution**: The process runs; it may block or wait during execution.
4. **Termination**: The OS ends the process, releasing its resources.
5. **Blocking**: A process waits for a resource or event, entering the blocked state.
6. **Resumption**: A blocked process returns to the ready state when the event/resource is available.

### **Process Communication and Synchronization**
- **Inter-Process Communication (IPC)**: Processes share data or coordinate actions via shared memory, message passing, or synchronization primitives.
- **Process Synchronization**: Ensures that shared resources or critical sections are accessed safely using synchronization mechanisms like semaphores or mutexes.

### **Features of Process States**
- Processes can transition between ready, running, and waiting states multiple times.
- New and terminated states occur only once in a process’s lifecycle.
- The **Process Control Block (PCB)** stores details like process state, priority, and resource allocation.
- The **Process State Diagram** visually represents state transitions, aiding in process management.

### **Conclusion**
The lifecycle of a process, encompassing states like new, ready, running, waiting, and terminated, is pivotal to efficient process management in operating systems. By managing transitions effectively, the operating system optimizes resource allocation and system performance. Understanding this lifecycle reveals the complexity and efficiency underlying modern computing.

**GFG Link :** https://www.geeksforgeeks.org/states-of-a-process-in-operating-systems/
