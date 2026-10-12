When running a Python script interactively or from a single file without generating a `.pyc` file, Python still uses a **compiler** internally, but the intermediate bytecode isn't saved to disk—it resides only in memory. Here's a breakdown:

---

### **Steps in Execution Without `.pyc` Files**
1. **Parsing**:
   - The Python interpreter reads the source code (`.py` file) and converts it into an Abstract Syntax Tree (AST).

2. **Compilation to Bytecode**:
   - The AST is compiled into bytecode. Even when no `.pyc` file is generated, this step happens in memory.
   - Bytecode is the intermediate representation that the Python Virtual Machine (PVM) can execute.

3. **Execution by the PVM**:
   - The Python Virtual Machine (PVM) takes the bytecode and interprets it, translating it into machine instructions for the CPU.

---

### **Machine Code Translation**
The PVM doesn’t translate bytecode directly into native machine code (as a traditional compiler like GCC would). Instead:
- The PVM is a **software-based interpreter**.
- It executes bytecode instructions by interpreting them into a series of low-level operations supported by the host operating system and CPU.

For example:
- A bytecode operation like `LOAD_FAST` (loading a variable) might result in the PVM performing a sequence of CPU instructions to fetch the variable's value from memory.

---

### **Why No `.pyc` File?**
When running a script directly (`python script.py`):
- Python skips saving the compiled bytecode as `.pyc` unless the script is imported as a module.
- This avoids unnecessary file I/O for one-time execution.

---

### **Comparison to Saved `.pyc` Files**
- **With `.pyc`**: Python reuses precompiled bytecode from disk, saving the overhead of recompiling source code.
- **Without `.pyc`**: The bytecode is compiled in memory for immediate execution but discarded afterward.

---

### **Key Takeaways**
- A compiler **is used**, but bytecode may only exist temporarily in memory.
- The Python Virtual Machine interprets bytecode and performs operations on the CPU, bypassing the need to generate native machine code.
- `.pyc` files primarily serve as a caching mechanism, not a requirement for running Python code.