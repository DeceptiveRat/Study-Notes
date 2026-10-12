When you compile assembly code, the process happens in two main steps: **assembling** and **linking**.

---

### **Step 1: Assemble the .asm file into an object file (.o)**
**Command:**  
```bash
nasm -f elf64 program.asm -o program.o
```
or (for 32-bit code):
```bash
nasm -f elf program.asm -o program.o
```

#### **What Happens Here?**
1. **Preprocessing:**  
   - NASM reads the assembly file (`program.asm`) and processes any preprocessor directives (e.g., `%include`).
   
2. **Lexical Analysis & Parsing:**  
   - NASM reads each line and breaks it into tokens (mnemonics, operands, labels, etc.).
   
3. **Instruction Encoding:**  
   - NASM translates each assembly instruction into its corresponding machine code (binary opcodes).  
   - Example:  
     ```assembly
     mov eax, 1
     ```
     - Encoded as: `b8 01 00 00 00` (in x86-64).

4. **Symbol Table Generation:**  
   - If labels (jump targets, function names, etc.) exist, NASM stores them in a symbol table for later resolution.

5. **Relocation Information Creation:**  
   - If your code references external functions (e.g., `printf` from libc), NASM adds relocation entries indicating that these symbols need to be resolved later by the linker.

6. **Output Generation:**  
   - NASM produces a `.o` object file in **ELF format** (Executable and Linkable Format) containing:
     - Machine code instructions
     - Symbol table (if applicable)
     - Relocation information (if applicable)
     - Section headers (e.g., `.text` for code, `.data` for initialized data, etc.)

---

### **Step 2: Link the .o file into an executable**
**Command:**  
```bash
ld program.o -o program
```

#### **What Happens Here?**
1. **Read the Object File (`program.o`)**  
   - `ld` reads the ELF file and extracts the relevant sections (`.text`, `.data`, `.bss`, symbol table, relocation entries, etc.).

2. **Resolve Symbols**  
   - If your assembly code refers to external symbols (e.g., functions like `printf`), `ld` searches for these in standard libraries (e.g., `libc.so`).
   - If a function is missing, the linker throws an **"undefined reference"** error.

3. **Apply Relocations**  
   - If addresses of labels or external function calls are unknown, `ld` replaces placeholders with actual addresses.
   - Example: If your code calls `printf`, `ld` updates the jump/call instruction with the correct memory address.

4. **Arrange Sections in Memory Layout**  
   - `ld` arranges different sections (`.text`, `.data`, `.bss`) based on the executable format and operating system requirements.

5. **Generate the Final Executable (`program`)**  
   - The linker produces an **ELF executable**, which the OS can load and run.

---

### **Summary**
1. **Assembling (NASM)**
   - Translates assembly code → machine code (`.o` file)
   - Creates symbol table & relocation info
   - Produces an ELF object file

2. **Linking (ld)**
   - Resolves symbols
   - Applies relocations
   - Creates an executable ELF file

After these steps, you can run the program with:
```bash
./program
```

Let me know if you need a breakdown of a specific part!