This page covers benefits and risks of using threads.

## Benefits of Threads
* Exploiting processor(s) to achieve better system thoughput
    * Exploiting **multiple processors/cores**. A program with only one thread can run at most one processing unit at a time.
    * Achieving better **throughput for each processor**. In a multithreaded program, another thread can still run while the first thread is still waiting for a synchronous IO operation to complete, allowing application to still make progress during the blocking IO.
* Simplicity of modeling
    * A program that processes **one type of task sequentially in a thread is simpler to write**, less error-prone, and easier to test than one managing multiple different types of tasks at once.
    * Assigning a thread to each type of task **insulates domain logic from the details of multithreaded environment** such as scheduling, interleaved operations, asynchronous IO and resource waits.
* Simplified handling of asynchronous events
    * With a **single-threaded** application you have to choose between **stalling** on IO and doing **non-blocking IO in a single thread** which is complicated.
    * With threads you can either assign **a thread per IO activity** or use **non-blocking IO** (`java.nio` with `poll`, `select` system calls) and still handle tasks sequentially in threads.
