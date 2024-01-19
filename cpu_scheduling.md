# CPU Scheduling

- CPU Scheduling is the process of assigning tasks to the CPU.
- There are two types of CPU scheduling:
    - Non-preemptive scheduling
    - Preemptive scheduling

## CPU and I/O Burst Cycles

- Process execution consists of cycle of `CPU execution` and `I/O wait`. Processes alternate b/w these two states.
    - CPU burst time is the time taken by the process to execute instructions.
    - I/O burst time is the time taken by the process to wait for I/O.
- Process starts with CPU burst followed by I/O burst followed by CPU burst and so on; finally terminated by CPU burst

    <img src="./assets/image-12.png" style="width: 20%; height: 20%;">

## Preemptive / Non-preemptive Scheduling

- `CPU scheduler`: It assigns the CPU from READY queue to the process with the shortest CPU burst time.
- `Dispatcher`: It is the process that takes the control of CPU from the process and executes it.

CPU Scheduling takes place in the following cases:

1. When a process switches from `running` to `waiting` state. **[No choice]**
2. when a process switches from `running` to `ready` state. [choices are made during interrupt]
3. when a process switches from `waiting` to `ready` state. [choices are made during I/O completion]
4. when process terminates. **[No choice]**

- In preemptive scheduling, the process running on the CPU is suspended and the CPU scheduler is called to select another process to run.
- In non-preemptive/cooperative scheduling, once a process starts executing, it cannot be stopped until it completes its execution or voluntarily gives up control.

## Scheduling Criteria

- `CPU Utilisation`: CPU utilization is the percentage of time (0% - 100%) the CPU is busy.
- `Throughput`: Throughput is the number of processes that are completed during a given time period.
- `Turnaround Time`: It is the time taken by a process from the time it enters the ready queue to the time it completes its execution.
- `Waiting Time`: Waiting time is the time taken by a process from the time it enters the ready queue to the time it is assigned to the CPU.
- `Response Time`: Response time is the time taken by a process from the time it enters the ready queue to the time it is assigned to the CPU. (slight delay after opening a video)




