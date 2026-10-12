### **Mutexes in C**
A **mutex (mutual exclusion)** is a synchronization primitive used to protect shared resources from concurrent access by multiple threads. In C, mutexes are commonly implemented using the **POSIX threads (pthreads)** library.

### **Can You Have Multiple Mutexes?**
Yes, you can (and often should) have multiple mutexes. Each mutex is a separate lock, and you can use different mutexes to protect different shared resources. This allows threads to access unrelated resources concurrently without unnecessary blocking.

---

### **Why Multiple Mutexes?**
If you have two or more shared resources, using a separate mutex for each allows finer-grained control. For example:
- Mutex 1 (`mutex_a`) protects **Resource A**.
- Mutex 2 (`mutex_b`) protects **Resource B**.

This reduces contention and improves concurrency, as threads that need different resources can proceed without waiting for each other.

---

### **Using Mutexes in C**
Here’s how you use mutexes with the **pthreads** library:

#### 1. **Declaring and Initializing Mutexes**
Mutexes are declared as `pthread_mutex_t` and must be initialized before use.
```c
#include <pthread.h>

// Declare two mutexes
pthread_mutex_t mutex_a = PTHREAD_MUTEX_INITIALIZER;
pthread_mutex_t mutex_b = PTHREAD_MUTEX_INITIALIZER;
```

Alternatively, you can initialize mutexes dynamically:
```c
pthread_mutex_t mutex;
pthread_mutex_init(&mutex, NULL);  // NULL = default attributes
```

---

#### 2. **Locking and Unlocking a Mutex**
Before accessing a shared resource, lock the associated mutex. Unlock it after you're done.

```c
// Lock the mutex
pthread_mutex_lock(&mutex_a);

// Critical section: Access Resource A
shared_resource_a += 1;

// Unlock the mutex
pthread_mutex_unlock(&mutex_a);
```

---

#### 3. **Multiple Mutexes Example**
Here’s an example where two threads access two shared resources with two mutexes:

```c
#include <pthread.h>
#include <stdio.h>

pthread_mutex_t mutex_a = PTHREAD_MUTEX_INITIALIZER;
pthread_mutex_t mutex_b = PTHREAD_MUTEX_INITIALIZER;

int shared_resource_a = 0;
int shared_resource_b = 0;

void *thread_func_1(void *arg) {
    pthread_mutex_lock(&mutex_a);
    shared_resource_a++;
    printf("Thread 1 updated Resource A: %d\n", shared_resource_a);
    pthread_mutex_unlock(&mutex_a);

    pthread_mutex_lock(&mutex_b);
    shared_resource_b++;
    printf("Thread 1 updated Resource B: %d\n", shared_resource_b);
    pthread_mutex_unlock(&mutex_b);

    return NULL;
}

void *thread_func_2(void *arg) {
    pthread_mutex_lock(&mutex_b);
    shared_resource_b++;
    printf("Thread 2 updated Resource B: %d\n", shared_resource_b);
    pthread_mutex_unlock(&mutex_b);

    pthread_mutex_lock(&mutex_a);
    shared_resource_a++;
    printf("Thread 2 updated Resource A: %d\n", shared_resource_a);
    pthread_mutex_unlock(&mutex_a);

    return NULL;
}

int main() {
    pthread_t thread1, thread2;

    pthread_create(&thread1, NULL, thread_func_1, NULL);
    pthread_create(&thread2, NULL, thread_func_2, NULL);

    pthread_join(thread1, NULL);
    pthread_join(thread2, NULL);

    return 0;
}
```

---

### **Important Considerations**
1. **Deadlocks**:
   - When using multiple mutexes, be cautious of deadlocks.
   - Example of a potential deadlock:
     - Thread 1 locks `mutex_a`, then tries to lock `mutex_b`.
     - Thread 2 locks `mutex_b`, then tries to lock `mutex_a`.
     - Both threads block indefinitely.
   - **Solution**:
     - Always lock mutexes in a consistent order (e.g., always lock `mutex_a` before `mutex_b`).

2. **Mutex Destruction**:
   - If a mutex is no longer needed, destroy it with:
     ```c
     pthread_mutex_destroy(&mutex);
     ```
   - This is especially important for dynamically initialized mutexes.

3. **Trylocks**:
   - Use `pthread_mutex_trylock` if you want to attempt locking without blocking.
   ```c
   if (pthread_mutex_trylock(&mutex_a) == 0) {
       // Lock acquired
       pthread_mutex_unlock(&mutex_a);
   } else {
       // Lock not acquired
   }
   ```

4. **Recursive Mutexes**:
   - If a thread needs to lock the same mutex multiple times, use a **recursive mutex**.
   ```c
   pthread_mutexattr_t attr;
   pthread_mutexattr_init(&attr);
   pthread_mutexattr_settype(&attr, PTHREAD_MUTEX_RECURSIVE);
   pthread_mutex_init(&mutex, &attr);
   ```

---

### **When to Use a Single vs. Multiple Mutexes**
- Use **one mutex** if:
  - The resources are always accessed together as a single critical section.
- Use **multiple mutexes** if:
  - Resources are independent, allowing better concurrency.
  - Different threads access different resources.

---

By managing your mutexes wisely, you can effectively synchronize shared resources and build efficient multithreaded applications. Let me know if you want more advanced examples or help with debugging!