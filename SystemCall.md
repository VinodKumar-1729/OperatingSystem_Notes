### What are System Calls?

**System calls** are the interface between user programs and the operating system. They allow user-level processes to request services from the kernel (OS's core). Since direct hardware access by user programs is not allowed, system calls are used to perform low-level operations such as file manipulation, process control, or memory management, which are executed in kernel mode (with high privileges).

**Why are system calls needed?**
- **Resource protection**: Direct access to hardware resources can compromise system stability and security. System calls allow safe access.
- **Abstraction**: They abstract the underlying hardware, providing a consistent interface across different machines.
- **Privilege separation**: Certain operations like interacting with hardware or accessing memory must be executed with higher privileges (in kernel mode).

### Types of System Calls:

1. **Process Control System Calls**
2. **File Management System Calls**
3. **Device Management System Calls**
4. **Information Maintenance System Calls**
5. **Communication System Calls**

---

### 1. Process Control System Calls

**Process control system calls** manage processes (creation, execution, termination, etc.). Processes need resources like CPU, memory, and I/O for execution, which are handled by these system calls.

- **fork()**: Creates a new process by duplicating the calling process. The new process is called the child process, and the original one is the parent.
  - Example: 
    ```c
    pid_t pid;
    pid = fork(); // if pid == 0, it's the child process, else parent
    ```
  - If the call succeeds, `fork()` returns a non-zero PID to the parent and 0 to the child.

- **exec()**: Replaces the current process memory space with a new program. After a `fork()`, the child process may use `exec()` to run a different program.
  - Example: `execlp("ls", "ls", "-l", NULL);` runs the `ls -l` command in the current process.

- **wait()**: The parent process uses `wait()` to wait for its child to terminate.
  - Example:
    ```c
    int status;
    wait(&status); // Wait for the child to finish
    ```

- **exit()**: Terminates the process.
  - Example: `exit(0);` terminates with an exit status of 0 (success).

- **getpid()**: Returns the process ID of the calling process.
  - Example: `pid_t pid = getpid();`

- **kill()**: Sends a signal to terminate or modify the behavior of a process.
  - Example: `kill(pid, SIGTERM);` terminates a process with the given PID.

---

### 2. File Management System Calls

These system calls deal with file handling, allowing processes to create, delete, read, write, and manipulate files.

- **open()**: Opens a file and returns a file descriptor (an integer used to identify the file).
  - Example: `int fd = open("file.txt", O_RDONLY);` opens a file for reading.

- **read()**: Reads data from an open file.
  - Example: 
    ```c
    char buffer[100];
    read(fd, buffer, 100); // Read 100 bytes into buffer
    ```

- **write()**: Writes data to an open file.
  - Example: 
    ```c
    char buffer[] = "Hello, World!";
    write(fd, buffer, strlen(buffer)); // Write data to the file
    ```

- **close()**: Closes an open file descriptor.
  - Example: `close(fd);`

- **lseek()**: Moves the file pointer to a specified location.
  - Example: `lseek(fd, 0, SEEK_SET);` moves the file pointer to the beginning of the file.

- **stat()**: Retrieves file attributes.
  - Example:
    ```c
    struct stat buf;
    stat("file.txt", &buf); // Get file information like size, permissions
    ```

---

### 3. Device Management System Calls

These manage device-related operations like reading/writing to I/O devices (disks, printers).

- **ioctl()**: Performs a control operation on a device. It's a general system call for device-specific operations not covered by regular read/write.
  - Example: `ioctl(fd, command, argument);` is used for various device control actions.

- **read()**: Reading data from a device. Used for reading from block or character devices.
  - Example: `read(fd, buffer, size);` reads data from the device into the buffer.

- **write()**: Writing data to a device.
  - Example: `write(fd, buffer, size);` writes data from buffer to the device.

- **open()** and **close()**: These are also used for device management to open and close device files.

---

### 4. Information Maintenance System Calls

These system calls provide information about system resources and processes or allow modification of system properties.

- **gettimeofday()**: Returns the current time.
  - Example: `gettimeofday(&tv, NULL);`

- **getpid()**: Returns the process ID of the calling process.

- **getuid() and setuid()**: Get and set user IDs for the current process.
  - Example: 
    ```c
    uid_t uid = getuid(); // Get user ID
    setuid(1001);         // Set new user ID
    ```

- **uname()**: Provides system information like OS name, release number.
  - Example:
    ```c
    struct utsname buffer;
    uname(&buffer); // Get system information
    ```

---

### 5. Communication System Calls

Processes often need to communicate with each other, especially in distributed systems. These system calls facilitate that communication, either between processes on the same machine or across a network.

- **pipe()**: Creates a unidirectional data channel (pipe) between two processes.
  - Example: 
    ```c
    int fd[2];
    pipe(fd); // fd[0] for reading, fd[1] for writing
    ```

- **shmget(), shmat(), shmdt()**: Used to allocate, attach, and detach shared memory.
  - Example: `shmget(IPC_PRIVATE, size, 0666|IPC_CREAT);` allocates a shared memory segment.

- **socket()**: Creates a socket for network communication.
  - Example:
    ```c
    int sockfd = socket(AF_INET, SOCK_STREAM, 0); // Create a TCP socket
    ```

- **send() and recv()**: Send and receive messages over a socket.
  - Example: `send(sockfd, msg, len, 0);`

---

### How System Calls Work (Under the Hood)

1. **Switch from user mode to kernel mode**: A system call switches the execution from user mode to kernel mode (higher privilege) through a special interrupt or trap.
2. **Kernel performs the operation**: The kernel identifies the system call number, looks up the corresponding kernel function, and executes it.
3. **Return to user mode**: Once the operation completes, control returns to the user process.

### Common Issues with System Calls:
- **Blocking**: Some system calls like `read()` and `wait()` can block a process, making it wait until the requested operation completes.
- **Error Handling**: System calls often return error codes (like `-1`) when something goes wrong, and these must be handled carefully using functions like `errno`.

By learning how these different system calls work, you'll understand how the OS interacts with processes, files, and hardware in an organized, controlled manner. Each system call provides a structured way for user applications to perform privileged operations indirectly through the operating system.
