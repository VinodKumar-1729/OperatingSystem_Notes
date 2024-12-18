**Context Switching in an Operating System**


### What is Context Switching in an Operating System?
**Context switching** in an operating system involves saving the current state (context) of a running process so it can be resumed later, and loading the context of another process to execute it. This mechanism allows multiple processes to share the CPU and other resources efficiently.

#### Key Aspects of Context Switching:
- **Context:** Includes CPU register values, program counter, and other process-specific data stored in the Process Control Block (PCB).
- **Process Change:** The system uses CPUs to transition a process from one state to another.

### Example of Context Switching
In an OS, multiple processes (N) are stored in Process Control Blocks (PCBs). When a process is running, other high-priority processes may queue up to use the CPU. During a context switch:
1. The kernel saves the context of the current process into its PCB.
2. It restores the saved context of the next process from its PCB.

#### Performance Consideration:
- Context-switch time is **pure overhead** because no useful computation is done during this period.
- The speed depends on:
  - Memory access speed.
  - Number of registers to copy.
  - Hardware support (e.g., processors with multiple register sets).
- Example: In processors like Sun UltraSPARC, context switching may only involve changing a pointer to a register set.

### Need for Context Switching
Context switching ensures efficient CPU usage and process management. It:
1. **Shares a Single CPU:** Allows multiple processes to share CPU resources without requiring additional processors.
2. **Resumes Execution Seamlessly:** Restores process execution from where it was interrupted.
3. **Handles Multitasking:** Manages multiple processes in a single system.

### Triggers of Context Switching
1. **Interrupts:** Context switching occurs when an interrupt (e.g., I/O requests) redirects the CPU to handle the event.
2. **Multitasking:** Enables the CPU to switch between processes, retaining the state of the preempted process.
3. **User/Kernel Switch:** Necessary when switching between user mode and kernel mode to access privileged operations.

### Process Control Block (PCB)
The **Process Control Block (PCB)** represents a process in the OS. It stores process-related information such as:
- Process ID (PID).
- Process state (running, waiting, etc.).
- CPU registers.
- Program counter.
- Memory allocation.
- I/O status.

### State Diagram of Context Switching
A typical state diagram for context switching includes:
1. **Running State:** The process currently using the CPU.
2. **Ready State:** Processes waiting in the queue for CPU allocation.
3. **Waiting State:** Processes waiting for I/O or other events.

### Steps in Context Switching
1. **Save Current State:** Save the context of the current process in its PCB.
2. **Store PCB:** Keep the PCB in memory or a custom OS file.
3. **Select New Process:** Use the scheduler to pick the next process from the ready queue.
4. **Restore New State:** Load the program counter and CPU registers of the selected process.
5. **Resume Execution:** Continue execution from the point saved in the new process’s PCB.

### Factors Affecting Process Selection
- **Priority-based Scheduling:** Higher-priority processes are selected first.
- **Thread Values:** Specific thread conditions may influence process scheduling.

### Additional Notes
- **Hardware Dependency:** Modern CPUs optimize context switching using advanced hardware features.
- **Minimizing Overhead:** Efficient scheduling algorithms and hardware support reduce the time spent on context switching.
- **Complexity and Overhead:** As the OS becomes more complex, the overhead of context switching increases due to additional tasks performed during the switch.

---

**GFG Link :** https://www.geeksforgeeks.org/context-switch-in-operating-system/
