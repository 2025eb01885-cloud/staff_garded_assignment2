## Question 5: Thread Synchronization Demo

### Overview
This example demonstrates how multiple threads safely update a shared counter using POSIX threads and a mutex lock. The program shows how `pthread_mutex_t` prevents race conditions by allowing only one thread to enter the critical section at a time.

### Files included
- `thread_sync.c` - C program using `pthread_create`, `pthread_join`, and `pthread_mutex_t`
- `README.md` - explanation and usage instructions
- `Screenshot 2026-07-24 173817.png` - screenshot of program output or result

### How to compile
```bash
gcc Question5/thread_sync.c -o Question5/thread_sync -pthread
```

### How to run
```bash
./Question5/thread_sync
```

### What the program does
1. Initializes a global mutex lock.
2. Creates 3 threads.
3. Each thread acquires the mutex before reading and updating the shared counter.
4. Each thread prints its progress while holding the lock.
5. Threads release the lock so the next thread can enter the critical section.
6. The main thread waits for all worker threads to finish.

### Expected behavior
- The counter is updated sequentially.
- No thread reads or writes the counter while another thread is inside the critical section.
- The final counter value is `3`.

### Key concepts
- `pthread_mutex_init` initializes the mutex.
- `pthread_mutex_lock` locks the mutex and blocks if another thread holds it.
- `pthread_mutex_unlock` releases the mutex so another thread can acquire it.
- `pthread_join` waits for a thread to complete before the program exits.

### Notes
This example is useful for demonstrating mutual exclusion in multithreaded programs and preventing race conditions on shared data.
