Q. https://devblogs.microsoft.com/oldnewthing/20220919-00/?p=107195

A. 
This paragraph discusses the performance implications of accessing per-thread data (like the **Thread Environment Block (TEB)**) using **segment registers** (like `FS` on x86 or `GS` on x86-64) versus using **general-purpose registers**.

---

### **Breaking It Down**
1. **Absolute Selector-Relative Load vs. General-Purpose Register Load**
   - Accessing memory via a **segment register** (e.g., `FS:[offset]` or `GS:[offset]`) requires a **32-bit offset**.
   - In contrast, accessing memory using a **general-purpose register** (e.g., `mov eax, [rbx+offset]`) can use a much smaller offset (as little as **8 bits**, depending on the instruction encoding).
   - Smaller offsets mean smaller instruction sizes, which can improve **code density** and execution efficiency.

2. **Segment-Register-Based Access is Slower**
   - **Segment registers like FS and GS are not optimized for frequent access**. CPUs optimize for **flat memory addressing** (i.e., using general-purpose registers like `RBX` or `RBP` for memory access).
   - Accessing memory through a **segment register with a non-zero base** (like `GS` pointing to the TEB) incurs a **performance penalty**.
   - The CPU has to **resolve the segment base + offset**, which is more complex than a flat memory access.

3. **Extra Instruction Prefix Byte**
   - Instructions that use `FS:` or `GS:` require an **extra prefix byte** to specify the segment override.
   - This increases instruction size and can lead to **worse instruction cache utilization**.

4. **Execution Path Optimization**
   - Modern processors optimize execution paths for **common** instructions.
   - Since most code doesn’t frequently access `FS:` or `GS:`, execution paths involving them might not be as well-optimized as normal memory accesses.

5. **Caching in a General-Purpose Register is More Efficient**
   - If a function needs to access **per-thread data multiple times**, it may be **faster to store the TEB base address in a general-purpose register** (like `RAX` or `RBX`).
   - Instead of repeatedly accessing `GS:[offset]`, the function could **load the TEB pointer once into a register** and use regular memory accesses.
   - This allows **smaller, faster instructions** that take advantage of **flat memory addressing**.

---

### **Key Takeaways**
- Directly accessing `FS:[offset]` or `GS:[offset]` **incurs extra overhead** compared to normal memory accesses.
- Using segment registers like `FS:` or `GS:` requires a **larger offset** (32-bit) and an **instruction prefix byte**, making it **less efficient**.
- If a function needs **multiple accesses**, it's **better to cache the TEB address in a general-purpose register** to avoid repeated segment register access.
- The CPU **optimizes flat memory access better**, making it preferable when performance is a concern.

Would you like an example of how caching the TEB in a register improves performance?