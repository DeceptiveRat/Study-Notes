Your understanding is mostly correct, but there are nuances:

### Why Free Memory Manually?
1. **Memory Savings:**  
   In long-running programs (e.g., servers), not freeing unused memory leads to memory leaks, which can accumulate over time and exhaust the system's resources.

2. **Security:**  
   Not freeing memory leaves sensitive data (e.g., passwords, encryption keys) in memory, which might be accessible to malicious actors or debugging tools.

3. **Best Practices & Code Hygiene:**  
   Properly freeing memory reflects good programming practice and avoids dependencies on implementation details of the operating system.

---

### During Immediate Termination
If your program encounters an unrecoverable error and terminates:
- The operating system **reclaims all memory** allocated by your process when it exits, so there’s no memory leak from the OS's perspective.
- **Manually freeing memory in this scenario is unnecessary**, as the program will not continue running.

However, there are exceptions:
- If you’re debugging with tools (e.g., AddressSanitizer or Valgrind), they might report memory leaks because they don't distinguish between planned and unplanned termination.
- If your program runs in environments where resources might not be fully released (e.g., embedded systems or unusual runtime environments), manual freeing could still be relevant.

---

### AddressSanitizer (ASAN)
ASAN does not require you to free memory before program termination to avoid false positives for memory leaks. However:
- ASAN **will warn** about **memory leaks** regardless of termination cause (e.g., `exit()` or crash).
- It will not treat memory leaks as fatal errors but as warnings to encourage better memory management.

---

### Takeaway
1. In short-lived programs, there’s typically no need to free memory explicitly if the program is terminating.
2. For debugging, prioritize proper memory management in normal execution paths to maintain clean reports.
3. Use tools like ASAN or Valgrind to catch leaks during development, but remember they might flag leaks that aren't problematic in production.

### Reference
- [Should I free memory before exit? - Stack Overflow](https://stackoverflow.com/questions/36584062/should-i-free-memory-before-exit)