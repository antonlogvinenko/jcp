This page covers benefits and risks of using threads.

## Benefits of Threads
* Exploiting processors
    * **Exploiting multiple processors/cores.** --- A program with only one thread can run at most one processing unit at a time.
    * **Achieving better throughput on a single-processor system.** --- In a multithreaded program, another thread can still run while the first thread is still waiting for a synchronous IO operation to complete, allowing application to still make progress during the blocking IO.
