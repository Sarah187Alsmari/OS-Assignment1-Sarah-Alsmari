# Assignment Questions

## Instructions
Answer all 4 questions with detailed explanations. Each answer should be **3-5 sentences minimum** and demonstrate your understanding of the concepts.

---

## Question 1: Thread vs Process

**Question**: Explain the difference between a **thread** and a **process**. Why did we use threads in this assignment instead of creating separate processes?

**Your Answer:**

A process is an independent program in execution that has its own memory space and system resources, while a thread is a smaller unit of execution threads. This means threads are more lightweight and faster to create compared to processes. Processes require more overhead because each one needs its own memory and communication between them is slower. In contrast, threads share the same memory, which makes communication faster and more efficient.

In this assignment, we used threads instead of processes because the simulation requires multiple tasks to run efficiently and frequently switch between them. Threads are more suitable for this because they reduce overhead and improve performance. Also, since all processes in the simulation are part of the same program, using threads makes the implementation simpler and faster.

---

## Question 2: Ready Queue Behavior

**Question**: In Round-Robin scheduling, what happens when a process doesn't finish within its time quantum? Explain using an example from your program output.

**Your Answer:**

In Round-Robin scheduling, if a process does not finish within its time quantum, it is paused and moved to the end of the ready queue. This allows other processes to get CPU time, ensuring fairness among all processes. The process will wait for its next turn in the queue and then resume execution from where it stopped.

Example from my output:
▶ P3 executing quantum [4000ms] 
  ⚡ Quantum progress: [███████████████] 100%
  ⏸ P3 completed quantum 4000ms │ Overall progress: [███████████░░░░░░░░░] 55%
     Remaining time: 3171ms
  ↻ P3 yields CPU for context switch

  ➕ P3 added to ready queue │ Burst time: 7171ms | Priority: 2
┌─ Ready Queue ─────────────────────────────────────────────────────────────────
│ [P5 → P6 → P7 → P8 → P9 → P10 → P11 → P12 → P13 → P14 → P15 → P3]
└───────────────────────────────────────────────────────────────────────────────

**Explanation of example:**
In this example, process P3 was running but did not finish within the 4000ms time quantum. Its remaining time became 3171ms, so it was paused and sent back to the end of the ready queue. Later, it gets another chance to execute when its turn comes again. This behavior ensures that no single process can take over the CPU and all processes are treated fairly.

---

## Question 3: Thread States

**Question**: A thread can be in different states: **New**, **Runnable**, **Running**, **Waiting**, **Terminated**. Walk through these states for one process (P1) from your simulation.

**Your Answer:**

1. **New**: P1 is in the New state when the thread is first created but before it starts execution. This happens when the Process object is created and associated with a Thread.

2. **Runnable**: P1 becomes Runnable when the `Thread.start()` method is called. At this point, it is ready to run and waiting for the CPU scheduler to assign it CPU time.

3. **Running**: P1 enters the Running state when the CPU starts executing it. In the output, P1 runs its full burst time of 3659ms because it is less than the time quantum.

4. **Waiting**: A thread may enter the Waiting state when it is paused, such as during `Thread.sleep()` which simulates execution time. This represents the delay during processing or context switching.

5. **Terminated**: P1 enters the Terminated state after completing its execution. In the output, we see that P1 finishes in one cycle because its burst time is less than the time quantum, so it does not return to the queue.

---

## Question 4: Real-World Applications

**Question**: Give **TWO** real-world examples where Round-Robin scheduling with threads would be useful. Explain why this scheduling algorithm works well for those scenarios.

**Your Answer:**

### Example 1: Web Server

**Description**: 
A web server handles multiple client requests at the same time. Each request can be processed using a separate thread, such as loading a webpage or retrieving data.

**Why Round-Robin works well here**: 
Round-Robin scheduling ensures that each client request gets a fair share of CPU time. This prevents one request from blocking others and improves system responsiveness. It also allows the server to handle many users efficiently without delays.

### Example 2: Media Player

**Description**: 
A media player runs multiple tasks simultaneously, such as playing audio/video, buffering data, and updating the user interface.

**Why Round-Robin works well here**: 
Round-Robin ensures that all tasks receive CPU time regularly, which keeps the media playing smoothly without freezing. It maintains a balance between different tasks and improves user experience by ensuring responsiveness and fairness.

---

## Summary

**Key concepts I understood through these questions:**
1. The difference between threads and processes and why threads are more efficient.
2. How Round-Robin scheduling works and how processes are re-queued.
3. The lifecycle of a thread and how it moves between different states.

**Concepts I need to study more:**
1. Advanced thread synchronization techniques.
2. Other CPU scheduling algorithms like Priority Scheduling and Shortest Job First.
