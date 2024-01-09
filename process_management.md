# Process Management

- Process: program in execution
- Thread: unit of execution within a process.

## Process states

- As a process executes, it changes state. The state of a process is defined in part by the current activity of that process.

<img src="./assets/image-9.png" style="width: 65%; height: auto;">

## Process Control Block (PCB)

Each process is represented in the operating system by a Process Control Block (PCB) - also called a task control block.

1. **Process ID (PID):** Unique identifier assigned to distinguish different processes.

2. **Program Counter (PC):** Memory address of the next instruction to be executed.

3. **Register Set:** Collection of CPU registers storing the current state of the process.

4. **Process State:** Indicates the current state, such as "running," "ready," or "blocked."

5. **Memory Management Details:** Information about the process's memory usage, including base and limit registers or page tables.

6. **CPU Scheduling Information:** Data related to the process's position in the CPU scheduling queue, priority, or scheduling parameters.

7. **I/O Status:** Keeps track of I/O requests and status, including open files and pending I/O operations.

8. **Accounting Information:** Records resource usage statistics, execution time, and CPU time.

9. **Link to Next PCB:** Enables the creation of a linked list of PCBs for efficient management by the operating system.

## Process Scheduling

- **Job Queue** - As processes enter the system, they are put into a job queue, which consists of all processes in the system.
- **Ready Queue** - The processes that are residing in main memory and are ready and waiting to execute 

Job Queue -> Ready Queue -> CPU

1. completes the process and ends
2. if process with higher priority approached, existing running process will be moved to "partially executed swapped-out
processes" area
3. if running process needs I/O operation, it is moved to I/O waiting queues to get its turn.

<img src="./assets/image-10.png" style="width: 65%; height: auto;">

## Context Switching

- Interrupts cause the operating system to change a CPU from its current task and to run a kernel routine.
- During an interrupt, the system must save the current process's context on the CPU to later restore it, effectively pausing and then resuming the process.
- Context-switch time is pure overhead, because the system does no useful work while switching.
- **Analogy**: Reading a book, bookmarking it, Resuming it later.

## Process Creation & Deletion

### Creation

- Process created using a system call called, `create-process`
- creating process - **parent** process
- new processes - **child/children**  process.

Two execution possibilities when parent process creates child process:

1. The parent continues to execute concurrently with its children.
2. The parent waits until some or all of its children have terminated.


Two address space possibilities when parent process creates child process:

1. The child process is a `duplicate` of the parent process
2. The child process has a new program loaded into it.

### Deletion

- A process terminates after executing its final statement and return using `exit()` system call.
- the process may return a status value (typically an integer)
- Resources (physical, virtual memory, open files, I/O buffers) are deallocated
- process can cause the termination of another process via an appropriate system call (parent -> child)
    - The child has exceeded its usage of some of the resources that it has been allocated.
    - The task assigned to the child is no longer required.
    - OS does not allow a child to continue if its parent terminates.

## Interprocess Communication

Processes executing concurrently in the operating system may be either `independent` or `cooperating` processes.

- Cooperating processes require an interprocess communication (IPC) mechanism that allows to exchange data.
- Two Types: `Shared Memory` and `Message Passing`
    - In the shared-memory model, information exchange takes plces in a common memory region through reading and writing data.
    - In the message passing model, communication takes place by messages exchanged through kernels.

### Shared Memory

- Shared-memory interprocess communication involves creating a shared-memory region. 
- It resides in the initiating process's address space, and other processes attach to it for communication. 
- Operating systems typically restrict direct access between processes, but shared memory requires mutual agreement to remove this restriction.

**Producer-Consumer** - A producer process produces information that is consumed by a consumer process.
- Analogy: 
    - `Compiler`(Producer) -> Compile code -> `Assembler`(Consumer)
    - `Assembler`(Producer) -> produce objects -> `Loader`(Consumer)
- **Problem**: conflicts between producers and consumers, especially when accessing a data.
- **Solution**: Shared Memory (Buffer Sharing, Synchronization)

- Types of Buffer:
    - `Unbounded` Buffer (No limit in Buffer size; producers can always produce items)
    - `Boundeed` Buffer (fixed Buffer size; producers wait if full; consumer wait if empty)

### Message Passing