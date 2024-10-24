

### I/O Scheduling Overview

**I/O scheduling** is crucial for improving the performance of a system, especially when handling multiple I/O requests simultaneously. It determines the order in which the operating system processes these requests, balancing fairness and efficiency.

#### Key Components in Disk I/O:

1. **Seek Time**:
   - The time taken for the disk's read/write head to move to the track containing the requested data.
   
   **Formula**:
   \[
   \text{Seek Time} = \text{Number of tracks crossed} \times \text{Time per track}
   \]
   - Where the time per track is the time it takes the head to move from one track to an adjacent track.

2. **Rotational Latency**:
   - The time it takes for the disk to rotate and position the correct sector under the read/write head.
   
   **Formula**:
   \[
   \text{Rotational Latency} = \frac{1}{2 \times \text{Rotational Speed}}
   \]
   - Typically, rotational latency is calculated as half the time for one complete rotation, assuming the disk may be anywhere during its rotation when the request arrives.
   - **Example**: If the disk spins at 7200 RPM (rotations per minute):
     \[
     \text{Rotational Speed} = \frac{7200}{60} = 120 \text{ rotations per second}
     \]
     So, the rotational latency will be:
     \[
     \text{Rotational Latency} = \frac{1}{2 \times 120} = 4.17 \text{ milliseconds}
     \]

3. **Data Transfer Time**:
   - The time taken to actually transfer the data once the head is in position.

   **Formula**:
   \[
   \text{Transfer Time} = \frac{\text{Data Size}}{\text{Transfer Rate}}
   \]
   - Where the transfer rate is typically given in megabytes per second (MBps).

4. **Total I/O Time**:
   - The total time to complete an I/O operation is the sum of seek time, rotational latency, and transfer time.
   
   **Formula**:
   \[
   \text{Total I/O Time} = \text{Seek Time} + \text{Rotational Latency} + \text{Transfer Time}
   \]

---

### I/O Scheduling Algorithms

1. **First-Come, First-Served (FCFS) Scheduling**:
   #### Concept:
    - The simplest I/O scheduling algorithm.
    - It processes I/O requests in the order they arrive without reordering or prioritizing.
    - This can be inefficient, especially for disk-based operations, as it may result in high seek time.

     - **Advantages**: Simple to implement, fair in terms of request order.
     - **Disadvantages**: Long seek times due to random head movements.
   
   **Example**:
   - Requests: 98, 183, 37, 122, 14, 124, 65, 67
   - Initial head position: 53
   - Head movement path: 53 → 98 → 183 → 37 → 122 → 14 → 124 → 65 → 67
   - Total head movement (seek time): (98 - 53) + (183 - 98) + (183 - 37) + ... = High total seek time due to random movement.

---

2. **Shortest Seek Time First (SSTF) Scheduling**:

   - Always processes the I/O request closest to the current head position to minimize seek time.
   - **Advantages**: Lower seek time compared to FCFS.
   - **Disadvantages**: Starvation risk for faraway requests (they may never get serviced).
   
   **Formula for Seek Time**:
   \[
   \text{Seek Time} = |\text{current head position} - \text{request position}|
   \]

   **Example**:
   - Requests: 98, 183, 37, 122, 14, 124, 65, 67
   - Initial head position: 53
   - Closest request: 65 (so the disk services this request first)
   - Head movement: 53 → 65 → 67 → 37 → 14 → 98 → 122 → 124 → 183
   - Total seek time is reduced compared to FCFS.

---

3. **SCAN (Elevator Algorithm)**:

   #### Concept:
  - The disk head moves in one direction, fulfilling requests until it reaches the end of the disk, then reverses direction.
  - It works like an elevator: it goes in one direction picking up all requests, then reverses and picks up requests in the opposite direction.
   - **Advantages**: Prevents starvation and reduces the back-and-forth head movement.
   - **Disadvantages**: Long wait time for requests just behind the head after it starts moving in one direction.
   
   **Formula for Seek Time** (in one direction):
   \[
   \text{Total Seek Time} = |\text{start position} - \text{furthest request in direction}|
   \]
   
   **Example**:
   - Requests: 98, 183, 37, 122, 14, 124, 65, 67
   - Initial head position: 53
   - Head moves in one direction, servicing requests until it reaches the furthest (183 in this case).
   - Movement: 53 → 65 → 67 → 98 → 122 → 124 → 183, then reverses back to service requests like 37, 14.
   - Total head movement is more efficient than FCFS.

---

4. **C-SCAN (Circular SCAN)**:
   #### Concept:
  - Similar to SCAN, but instead of reversing direction, the disk head returns to the beginning of the disk (the lowest-numbered cylinder) and then starts servicing requests in one direction again.

   - **Advantages**: More uniform wait times, as the head always services requests in one direction.
   - **Disadvantages**: Jumping back to the start introduces a delay.
   
   **Example**:
   - Requests: 98, 183, 37, 122, 14, 124, 65, 67
   - Initial head position: 53
   - Head services: 65 → 67 → 98 → 122 → 124 → 183, then jumps back to 0 and continues.
   - This reduces the inefficiencies of reversing direction.

---

5. **LOOK Scheduling**:
   #### Concept:
  - LOOK is similar to SCAN, but instead of going to the end of the disk, it only goes as far as the last request in each direction before reversing.

   - **Advantages**: More efficient than SCAN since it doesn't travel to the edge of the disk if there are no requests.
   - **Disadvantages**: Long wait times for requests near the beginning if the head has just passed them.

   **Example**:
   - Requests: 98, 183, 37, 122, 14, 124, 65, 67
   - Initial head position: 53
   - Head only moves as far as the furthest request in the current direction, servicing: 65 → 67 → 98 → 122 → 124 → 183, then reverses to service 37 → 14.

---

6. **C-LOOK Scheduling**:
   #### Concept:
  - C-LOOK is a variation of LOOK, where the head only moves to the last request in one direction, then jumps back to the start and services requests in one direction again.
  - Like C-SCAN, it avoids unnecessary movement, but doesn’t return to the first cylinder.

   - **Advantages**: Offers more fairness in scheduling requests, especially for those closer to the start of the disk.
   - **Disadvantages**: Introduces delays when the head jumps back to the start.

   **Example**:
   - Requests: 98, 183, 37, 122, 14, 124, 65, 67
   - Initial head position: 53
   - Head services: 65 → 67 → 98 → 122 → 124 → 183, then jumps back to the smallest request and continues with 14 → 37.

---

### Summary of Important Formulas:

1. **Seek Time**:
   \[
   \text{Seek Time} = \text{Number of tracks crossed} \times \text{Time per track}
   \]

2. **Rotational Latency**:
   \[
   \text{Rotational Latency} = \frac{1}{2 \times \text{Rotational Speed (in rotations per second)}}
   \]

3. **Transfer Time**:
   \[
   \text{Transfer Time} = \frac{\text{Data Size}}{\text{Transfer Rate}}
   \]

4. **Total I/O Time**:
   \[
   \text{Total I/O Time} = \text{Seek Time} + \text{Rotational Latency} + \text{Transfer Time}
   \]

---

### Summary of Key Points:
- **FCFS**: Simplest, processes in order of arrival.
- **SSTF**: Shortest seek time first, prioritizes closer requests.
- **SCAN**: Elevator-like, moves in one direction then reverses.
- **C-SCAN**: Moves in one direction, jumps back to start.
- **LOOK**: Like SCAN but doesn’t go to the edge of the disk.
- **C-LOOK**: Like C-SCAN, only goes as far as the last request, then jumps back.

These are the key formulas and explanations for I/O scheduling and its algorithms. 
