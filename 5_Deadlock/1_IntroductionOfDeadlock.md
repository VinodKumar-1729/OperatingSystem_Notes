

### Deadlock in Operating Systems  

**What is Deadlock?**  
Deadlock is a situation in computing where two or more processes are unable to proceed because each is waiting for the other to release resources. Key concepts include:  
- **Mutual Exclusion:** Resources cannot be shared.  
- **Hold and Wait:** Processes are holding resources and waiting for others.  
- **No Preemption:** Resources cannot be forcibly taken.  
- **Circular Wait:** A circular chain of processes exists, where each process holds a resource needed by the next.  

**Example:**  
Consider two trains on a single track moving toward each other. Neither can proceed once they are face-to-face—this is a real-world example of deadlock.  

**Extended Note:** Deadlocks can occur in multi-threaded applications, distributed systems, or databases where multiple transactions compete for shared resources.  

---

### How Deadlock Occurs in Operating Systems  
1. **Resource Usage by Processes:**  
   - Request a resource.  
   - Use the resource.  
   - Release the resource.  

2. **Example:**  
   - Process P1 holds Resource R1 and waits for Resource R2 (held by Process P2).  
   - Process P2 holds Resource R2 and waits for Resource R1. This circular dependency causes deadlock.  

**Extended Note:** Deadlock may arise when thread synchronization constructs, like semaphores or locks, are misused.  

---

### Examples of Deadlock  
1. **Tape Drives:**  
   - System with 2 tape drives. Processes P0 and P1 each hold one drive and need the other.  

2. **Semaphores A and B (initialized to 1):**  
   - P0 executes `wait(A)`.  
   - P1 executes `wait(B)`.  
   - P0 and P1 enter deadlock waiting for each other's resources.  

3. **Memory Allocation Example:**  
   - Space available: 200KB.  
   - P0 requests 80KB, then 60KB.  
   - P1 requests 70KB, then 80KB.  
   - Deadlock occurs when both proceed to their second request.  

---

### Necessary Conditions for Deadlock  
Deadlock arises if all these conditions hold simultaneously:  
1. **Mutual Exclusion:** Resources cannot be shared.  
2. **Hold and Wait:** A process holds at least one resource and waits for additional resources.  
3. **No Preemption:** Resources cannot be forcibly taken from processes.  
4. **Circular Wait:** Processes form a circular chain, each waiting for a resource held by the next.  

---

### Deadlock Detection  
Deadlock detection involves identifying processes stuck waiting for each other indefinitely. Algorithms include:  
- **Resource Allocation Graph (RAG):**  
  - Detects circular wait conditions by analyzing resource-request edges and process-holding edges.  
  - Applicable only if there is one instance of each resource.  

- **Banker’s Algorithm:**  
  - Checks resource allocation states for potential deadlock.  
  - Predicts safe/unsafe states before granting resource requests.  

**Additional Note:** Detection requires periodic analysis of the resource allocation state, which can add computational overhead.  

---

### Methods for Handling Deadlock  

#### 1. **Deadlock Prevention:**  
   - Ensure at least one necessary condition for deadlock cannot hold.  
     - **Mutual Exclusion:** Avoid locks for shareable resources.  
     - **Hold and Wait:** Ensure a process requests all resources at once.  
     - **No Preemption:** Preempt resources when needed.  
     - **Circular Wait:** Impose a resource acquisition ordering.  

#### 2. **Deadlock Avoidance:**  
   - Use algorithms like Banker’s Algorithm to decide if resource allocation will lead to a safe state.  
   - Requires prior knowledge of resource needs.  

#### 3. **Deadlock Recovery:**  
   - Detect and recover using:  
     - **Manual Intervention:** Operator resolves deadlock.  
     - **Automatic Recovery:** System aborts processes or preempts resources.  
     - **Process Termination:** Abort all or selective processes.  
     - **Resource Preemption:** Roll back processes and reallocate resources.  

#### 4. **Deadlock Ignorance:**  
   - Allow deadlock to occur and reboot the system (e.g., Ostrich Algorithm).  

---

### Deadlock Recovery Techniques  
1. **Manual Intervention:**  
   - Operator manually resolves deadlock.  

2. **Automatic Recovery:**  
   - System automatically resolves deadlock by aborting or preempting processes.  

3. **Process Termination:**  
   - Abort all or selective processes to break the deadlock cycle.  
   - Factors for process termination:  
     - Process priority.  
     - Resource consumption.  
     - Completion time.  

4. **Resource Preemption:**  
   - Select a victim process and preempt resources.  
   - Rollback the process to a safe state.  
   - Ensure starvation prevention by limiting repeated victim selection.  

---

### Safe and Unsafe States  
- **Safe State:**  
  - No deadlock occurs; processes can wait for unavailable resources until released.  

- **Unsafe State:**  
  - No safe sequence exists for resource allocation.  

**Additional Note:** Safe and unsafe states are analyzed using Banker’s Algorithm in environments with multiple instances of resources.  

---

### Comparison: Deadlock vs. Starvation  
| **Aspect**       | **Deadlock**                                               | **Starvation**                                     |  
|------------------|-----------------------------------------------------------|--------------------------------------------------|  
| **Definition**   | Processes are blocked forever, waiting for each other.     | A process is perpetually denied resources.       |  
| **Resource Availability** | Resources are held by processes in deadlock.             | Resources are available but preferentially allocated. |  
| **Cause**        | Circular dependency between processes.                     | Priority or preference causes indefinite waiting. |  
| **Resolution**   | Requires intervention (e.g., aborting processes).          | Adjust scheduling to ensure fair resource allocation. |  

---

### Key Notes  
- **Prevention and avoidance ensure correctness but reduce performance.**  
- **Detection and recovery allow the system to progress but can be costly.**  
- **Deadlock ignorance improves performance but risks data correctness.**  

---

**GFG Link :** https://www.geeksforgeeks.org/introduction-of-deadlock-in-operating-system/
