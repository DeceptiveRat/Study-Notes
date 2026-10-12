You’re correct that if you have multiple dynamic allocations in a C program, you need to free all the memory that’s been allocated if you encounter an error. Doing this manually can be cumbersome and error-prone, especially in complex programs with many allocations.

Here are some common techniques to make error handling with multiple allocations easier:

### 1. **Centralized Cleanup Function**
   - Write a single function that frees all the pointers you may allocate across the program, then call this function whenever you need to exit due to an error. For each allocation, set the pointer to `NULL` initially, and in the cleanup function, check if each pointer is `NULL` before freeing it.

   ```c
   void cleanup(int *ptr1, char *ptr2, float *ptr3) {
       if (ptr1) free(ptr1);
       if (ptr2) free(ptr2);
       if (ptr3) free(ptr3);
   }
   ```

### 2. **Goto-Based Cleanup**
   - This pattern, common in C codebases, uses `goto` statements to jump to a cleanup section at the end of a function. Each allocation is checked sequentially, and in case of an error, you jump to the cleanup label to free all the allocated memory.

   ```c
   int *ptr1 = NULL;
   char *ptr2 = NULL;

   ptr1 = malloc(sizeof(int));
   if (!ptr1) goto cleanup;
   
   ptr2 = malloc(10 * sizeof(char));
   if (!ptr2) goto cleanup;

   // Your main code here

   cleanup:
       free(ptr2);
       free(ptr1);
   ```

### 3. **Use an Array of Pointers**
   - You can manage all allocated pointers in an array, then iterate through the array and free each non-null pointer when an error occurs. This approach helps if you have a predictable number of allocations.

   ```c
   void* ptrs[3] = { NULL };

   ptrs[0] = malloc(sizeof(int));
   if (!ptrs[0]) goto cleanup;

   ptrs[1] = malloc(10 * sizeof(char));
   if (!ptrs[1]) goto cleanup;

   cleanup:
       for (int i = 0; i < 3; i++) {
           if (ptrs[i]) free(ptrs[i]);
       }
   ```

### 4. **Use a Memory Manager (Linked List)**
   - You could implement a small memory manager that keeps track of allocated pointers in a linked list or an array. This allows you to free all allocated pointers in one go if needed. Libraries or custom memory managers exist that manage this automatically, though implementing your own can be helpful for learning purposes.

### 5. **Set Pointers to `NULL` After Freeing**
   - Although not a direct solution to shortening code, setting pointers to `NULL` immediately after `free` helps prevent double frees and dangling pointers, which simplifies debugging.