
**Inter-Process Communication (IPC)** allows processes to interact with each other and synchronize their actions, improving efficiency, modularity, and software design.

#### Types of Processes:
1. **Independent Process**: Does not interact with other processes and is unaffected by their execution.
2. **Cooperating Process**: Can be affected by other processes and often relies on communication mechanisms to synchronize actions.

#### IPC Methods:
1. **Shared Memory**:
   - Processes communicate by sharing a memory space. 
   - Example: **Producer-Consumer Problem**
     - Producer generates items and stores them in shared memory (buffer).
     - Consumer consumes items from the buffer.
     - Buffer can be **bounded** (limited size) or **unbounded** (unlimited size).
   
   **Producer-Consumer Pseudo-code Example**:
   ```cpp
   while(1) {
       // Producer checks if space is available in buffer
       while((free_index + 1) % buff_max == full_index);
       shared_buff[free_index] = nextProduced;
       free_index = (free_index + 1) % buff_max;
   }

   while(1) {
       // Consumer waits until an item is available
       while(free_index == full_index);
       nextConsumed = shared_buff[full_index];
       full_index = (full_index + 1) % buff_max;
   }
   ```
   **C++ Implementation**:
   - Uses atomic operations (`std::atomic`) to ensure thread safety.
   - A mutex (`std::mutex`) is used to protect critical sections when accessing the shared buffer.
   
2. **Message Passing**:
   - Processes communicate by sending messages via a communication link.
   - **Direct Communication**: The sender and receiver explicitly identify each other.
   - **Indirect Communication**: The sender and receiver use an intermediary mailbox for communication.
   
   **Communication Link Types**:
   - **Direct**: Requires explicit naming of the recipient (e.g., `send(p1, message)`).
   - **Indirect**: Uses a mailbox where messages are stored, and processes retrieve them.

   **Message Passing Primitives**:
   - **Send**: `send(message, destination)`
   - **Receive**: `receive(message, source)`
   
   **Blocking vs. Non-Blocking**:
   - **Blocking** (Synchronous): The sender/receiver waits until the message is received or sent.
   - **Non-Blocking** (Asynchronous): The sender/receiver does not wait for a response.

   **Mailbox (Port) Implementation**:
   - Multiple processes can send/receive messages via a shared mailbox.
   - Problems arise with multiple processes trying to receive from the same mailbox, which can be solved using **mutual exclusion (mutex)**.

   **Producer-Consumer Example using Message Passing**:
   ```cpp
   void Producer() {
       Message m;
       while(1) {
           receive(Consumer, &m);  // Wait for Consumer to be ready
           item = produce();
           build_message(&m, item);
           send(Consumer, &m);  // Send item to Consumer
       }
   }

   void Consumer() {
       Message m;
       while(1) {
           receive(Producer, &m);  // Wait for Producer to produce an item
           item = extract_item(&m);
           consume_item(item);  // Consume the item
           send(Producer, &m);  // Notify Producer
       }
   }
   ```
   - The producer and consumer exchange messages in the system.

#### IPC Systems:
- **POSIX**: Uses **Shared Memory** for IPC.
- **Mach**: Uses **Message Passing**.
- **Windows XP**: Uses **Message Passing** via local procedure calls.

#### Communication in Client/Server Architecture:
- **Pipe**: A mechanism for sending data between processes. Pipes can be used in both **Anonymous** and **Named** modes.
