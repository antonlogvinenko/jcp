This page covers benefits and risks of using threads.

## Benefits of Threads
* Exploiting processor(s) to achieve better system thoughput
    * Exploiting **multiple processors/cores**. A program with only one thread can run at most one processing unit at a time.
    * Achieving better **throughput for each processor**. In a multithreaded program, another thread can still run while the first thread is still waiting for a synchronous IO operation to complete, allowing application to still make progress during the blocking IO.
* Simplicity of modeling
    * A program that processes **one type of task sequentially in a thread is simpler** to write, less error-prone, and easier to test than one managing multiple different types of tasks at once.
    * Assigning a thread to each type of task **insulates domain logic from the details of multithreaded environment** such as scheduling, interleaved operations, asynchronous IO and resource waits.
* Simplified handling of asynchronous events
    * With a **single-threaded** application you have to choose between **stalling** on IO and doing **non-blocking IO in a single thread** which is complicated.
    * With threads you can either assign **a thread per IO activity** or use **non-blocking IO** (`java.nio` with `poll`, `select` system calls) and still handle tasks sequentially in threads.
* More responsive user interfaces. Long running tasks can be delegated to separate threads not to freeze UI.

## Risks of Threads
* Safety hazards.
    * Threads can be **confused by having data change unexpectedly**. Allowing multiple threads to access and modify the same variables introduces an element of non sequentiality into an otherwise sequential programming model, which can be confusing and difficult to reason about.
    * In the absence of synchronization, **the compiler, hardware, and runtime are allowed to take substantial liberties with the timing and ordering of actions**, such as caching variables in registers or processor local caches where they are temporarily (or even permanently) invisible to other threads.
* Liveness hazards. A liveness failure occurs when an activity gets into a state such that it is permanently **unable to make forward progress**.
* Performance hazards
    * **Context switches** when the scheduler suspends the active thread temporarily so another thread can run are more frequent in applications with many threads, and have significant costs.
    * When **threads share data**, they must use synchronization mechanisms that can inhibit compiler optimizations, flush or invalidate memory caches, and create synchronization traffic on the shared memory bus.