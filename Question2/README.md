## Question 2: Conceptual Explanations

* **How Process Creation, Waiting, and Signal Handling Work Together:**
  The program uses `fork()` to decouple a distinct worker process from the main sequence, allowing the parent to safely monitor it. By configuring an asynchronous `sigaction` handler to catch `SIGCHLD` loops via non-blocking `waitpid(..., WNOHANG)`, the kernel cleans up dead process records automatically, preventing resource-draining zombie elements from persisting if a process is targeted with a termination metric like `SIGKILL`.