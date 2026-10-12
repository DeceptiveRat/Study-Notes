These codes represent "poisoned" memory markers used by ASAN to detect various types of memory issues. AddressSanitizer (ASAN) places redzones around memory allocations, which act as boundaries. If your code tries to access a redzone, ASAN detects it as a potential memory bug. Each of these redzone markers has a specific purpose, as described below:

### 1. **Heap left redzone (`fa`)**
   - Placed to the **left of a heap-allocated memory block**.
   - Used to detect out-of-bounds writes on the left side of the allocated heap memory (buffer underflows).

### 2. **Freed heap region (`fd`)**
   - Marks **heap memory that has been freed**.
   - If your program tries to access this region, ASAN flags it as a **use-after-free** error.

### 3. **Stack left redzone (`f1`)**
   - Placed to the **left of stack-allocated memory**.
   - Helps detect out-of-bounds writes on the left side of stack memory (buffer underflows).

### 4. **Stack mid redzone (`f2`)**
   - A special redzone that appears **between stack frames**.
   - Helps catch invalid memory accesses that cross into adjacent stack frames.

### 5. **Stack right redzone (`f3`)**
   - Placed to the **right of stack-allocated memory**.
   - Used to catch out-of-bounds writes on the right side of stack memory (buffer overflows).

### 6. **Stack after return (`f5`)**
   - Marks stack memory that was previously in use by a function but is no longer valid because the function returned.
   - Helps catch **use-after-return** errors, where you access local variables after the function has exited.

### 7. **Stack use after scope (`f8`)**
   - Marks memory that goes out of scope in a function (e.g., memory of local variables).
   - Detects **use-after-scope** issues, where a variable is accessed outside its declared scope.

### 8. **Global redzone (`f9`)**
   - Placed around global variables to catch out-of-bounds accesses.

### 9. **Global init order (`f6`)**
   - Marks memory for variables with **initialization order issues** in global scope.
   - Helps catch situations where a global variable is accessed before it has been initialized.

### 10. **Poisoned by user (`f7`)**
   - Custom markers that developers can set in code (manually “poison” certain memory regions).
   - Used to mark memory regions that are intentionally invalid or out of bounds.

### 11. **Container overflow (`fc`)**
   - Marks areas beyond the end of a container’s capacity.
   - Helps catch cases where a data structure (like an array or vector) overflows.

### 12. **Array cookie (`ac`)**
   - Marks the **array cookie area**, used for checking certain allocations for array objects.

### 13. **Intra object redzone (`bb`)**
   - Placed **inside objects** to detect illegal accesses between fields within the same object.

### 14. **ASan internal (`fe`)**
   - Reserved for **internal ASAN structures**.
   - These are ASAN’s own memory regions, and accessing them would interfere with ASAN's own operations.

### 15. **Left alloca redzone (`ca`)**
   - Placed to the left of memory allocated with `alloca` (dynamic stack allocation).
   - Helps catch out-of-bounds writes for dynamically allocated stack memory.

### 16. **Right alloca redzone (`cb`)**
   - Placed to the right of memory allocated with `alloca`.
   - Used to detect out-of-bounds writes on the right side of dynamically allocated stack memory.

### Summary of ASAN Redzones
These redzones act as memory boundaries that ASAN monitors to detect illegal accesses. When your code interacts with any of these poisoned regions, ASAN immediately reports the issue, allowing you to identify and fix memory-related bugs more effectively.

------
Q. Why no right or mid heap redzone
A.
ASAN only defines a **heap left redzone** (`fa`) because of how memory is typically allocated and monitored in the heap. Here’s why:

1. **Heap Allocation Layout**:
   - When allocating memory on the heap (e.g., with `malloc` or `new`), memory blocks are often managed with certain metadata, such as block headers, located to the **left** of the allocated region. This helps ASAN monitor the allocated block boundaries efficiently without needing a right redzone.
   
2. **Freed Heap Region (`fd`)**:
   - Once a heap-allocated block is freed, the entire block (including any left redzone) is marked as **freed** with the marker `fd`. This frees ASAN from needing separate right or mid redzones in the heap because the entire region is poisoned and marked invalid.
   
3. **Dynamic Nature of the Heap**:
   - Unlike the stack, the heap’s dynamic allocation behavior makes it difficult to guarantee a consistent space for "right" or "mid" redzones between allocations. Multiple allocations may be tightly packed in memory, leaving no extra room for redzones between each block.

4. **Security in ASAN’s Design**:
   - By marking the entire region as poisoned upon freeing and setting a left redzone during allocation, ASAN achieves the necessary boundary protections without needing additional markers.

In contrast, stack memory has a more predictable layout, allowing ASAN to place specific left, right, and mid redzones in different parts of the stack frame to protect stack variables.