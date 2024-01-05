# Basics of Operating System

## Introduction

- program that manages the computer hardware.
- provides a base for application programs and acts as an intermediary between computer `user` and compter `hardware`.
- Examples: Windows, Linux, Mac OS, Android

    <img src="./assets/image-1.png" style="width: 65%; height: auto;">

    - Computer Hardware: Resources like CPU, Memory, I/O devices
    - Operating System: manages allocation of resources, memory, security
    - Programs (System / Application): perform tasks used directly by the users

### Types of OS

- Batch OS: Executes a sequence of jobs without user interaction.
- Time-sharing OS: Allows multiple users to interact with a computer simultaneously.
- Distributed OS: Manages resources across multiple interconnected computers.
- Network OS: Coordinates communication and resource sharing within a network.
- Real-Time OS: Provides predictable and timely responses for time-sensitive tasks.
- Multi-Programming/Processing/Tasking OS: Runs multiple programs concurrently for efficient resource utilization.

## Computer System Operation

  <img src="./assets/image-2.png" style="width: 65%; height: auto;">
  
  - CPU (Central Processing System): Brain of the Computer where computation and calculationg takes place
  - Hardware devices are connected to a `Controller` that takes care of device's I/O Operations
  - These CPU, adapters and controllers are connected by a common bus to a shared MEMORY. 
  - If program needs to be executed, It needs to be loaded to Main memory (finite)
  - CPU and the device controllers can execute concurrently, competing for memory cycles
  - To ensure orderly access to shared memory, a memory controller is provided to synchronize memory access

## Terminology

- **Bootstrap Program**: First program that runs when powered up or rebooted; stored in ROM to load OS Kernel to perform tasks.
- **Interrupt**: occurence of an event signalled by an Interrupt to the CPU via system bus from `Hardware` .
- **System Call**(Monitor call): `Software` may trigger an interrupt by executing a special operation called System Call.
- **Interrupt Service Routine**: contains the intended task to complete after a Interrupt

## Storage Structure

<img src="./assets/image-3.png" style="width: 65%; height: auto;">

## I/O Structure

- `reliability` and `performance` of a system greatly depends on Input, output management
- Device controllers maintain
    - Local Buffer Storage
    - Set of Special Purpose Registers
- operating systems have a device driver for each device controller
- It presents a uniform interface to the device to the rest of the operating system

### Working Principle of I/O Operation

1. device driver loads the appropriate registers within the device controller
2. device controller examines the contents of these registers to determine what action to take
3. controller starts the transfer of data from the device to its local buffer
4. Once data transfer is complete, device controller informs device driver via an interrupt about completion
5. device driver then returns control to the operating system

`Problem`: This is only useful for small amount of data transfer and not for bulk data movement<br>
`Solution`: Direct Access Memory (DMA), device controller transfers entire datablock directly to/from its own buffer storage to memory, with no CPU intervention. 

## Operating System Structure

<img src="./assets/image-4.png" style="width: 65%; height: auto;">

### Multiprogramming

- Multiprogramming increases CPU utilization and throughput by organizing jobs so CPU always has one to execute.
- Multiple programs are loaded into the computer's memory simultaneously, and the CPU switches between them rapidly.

### Time-Sharing / Multitasking

- CPU executes multiple jobs by switching among them
- Switches occur so frequently that the users can interact with each program while it is running
- Time sharing requires an interactive GUI computer system that provides direct communication

## OS Services
1. User interface
2. Program Execution
3. I/O operations
4. File system manipulation
5. Communications
6. Error detection
7. Resource allocation
8. Accounting
9. Protection and Security

