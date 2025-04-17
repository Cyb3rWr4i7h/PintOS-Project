# PintOS Project

This repository contains the implementation of **Project 1: Threads** for the **PintOS** operating system, as part of my Operating Systems Lab.

## Overview

PintOS is a simple, educational operating system developed as part of the Stanford Operating Systems course. This repository specifically addresses the **Threading System** as part of the first project of the PintOS lab. The goal of this project is to understand and implement a basic thread system, as well as to experiment with multi-level feedback queues (MLFQS) and priority scheduling in the operating system.

### Features Implemented
- **Thread Creation** and **Scheduling**.
- **Priority Scheduling** for threads.
- **MLFQS (Multi-Level Feedback Queue Scheduler)** – preemptive thread scheduling based on system load.
- Thread **yielding** for time-sharing.
- **Synchronization** mechanisms, including blocking and unblocking threads.

## Purpose of the Project

The purpose of this project was to implement a simple **threading system** and **preemptive scheduling** in PintOS. The main tasks include:
- Implementing a **round-robin** scheduling mechanism.
- Implementing a **pre-emptive priority-based scheduling** algorithm.
- Experimenting with **multi-level feedback queues (MLFQS)** to implement a more complex scheduler.
- Developing synchronization mechanisms to prevent race conditions.

## How to Build and Run

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/Cyb3rWr4i7h/PintOS-Project
    cd /PintOS-Project/src
    ```

2. **Installing PintOS**:
    Follow the installation steps from this [doc](https://piazza.com/class_profile/get_resource/itgbdzpqj6417o/iuzt04qzagh40p).


4. **Build PintOS**:
    ```bash
    make
    ```

5. **Run Tests**:
    After building, you can run tests to verify your implementation.

    - To run the default tests:
      ```bash
      make check
      ```

    - To run only the **MLFQS tests**:
      ```bash
      make run MLFQS
      ```

    - To check the grading tests:
      ```bash
      make grade
      ```

## Implementation Details

### 1. Thread Scheduling
- The thread scheduler uses **priority scheduling** by default, where each thread is assigned a priority, and the highest priority thread is scheduled first.
- **MLFQS** is enabled by a kernel command-line option (`-o mlfqs`) and uses a multi-level feedback queue to adjust the priority of threads based on their recent CPU usage.

### 2. Priority Donation
- **Priority donation** ensures that a thread holding a lock with a lower priority can donate its priority to the thread that is waiting for the lock, preventing **priority inversion**.

### 3. Timer and Preemption
- The system uses a timer interrupt (`TIMER_FREQ`) to simulate **time slices**. The **`thread_tick()`** function is invoked each time the timer interrupts, which checks if the current thread has exhausted its time slice and, if so, preempts it by invoking **`thread_yield()`**.


## Credits
- **Stanford University** for providing the PintOS project as part of the Operating Systems course.
- **PintOS** contributors for providing the base code and documentation for educational purposes.
