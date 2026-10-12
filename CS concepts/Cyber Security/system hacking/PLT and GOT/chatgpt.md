Great question — understanding how PLT (Procedure Linkage Table) and GOT (Global Offset Table) work is super important for topics like reverse engineering, binary exploitation, and even malware development. Let’s go deep into what happens when a **dynamically linked binary** runs a **library function** (like `printf`) for the **first** and **second time**.

---

### 🧠 Big Picture: Dynamic Linking at Runtime
When a binary is dynamically linked, it doesn't contain the actual code of shared library functions (like `libc`'s `printf`) — instead, it defers resolving them until runtime. This is made efficient and flexible using **PLT** and **GOT**.

---

### 📦 The Key Players
- **PLT (Procedure Linkage Table)**: A jump table in the binary that acts as a stub or gateway for calling external functions.
- **GOT (Global Offset Table)**: A table that holds actual memory addresses of global data — including function pointers used by the PLT.

---

## 🕵️‍♂️ First Call to a Library Function (e.g., `printf`)

Let’s walk through the first time the binary calls `printf()`.

### 1. Code calls `printf()`, which actually goes to an entry in the **PLT**:
```asm
call printf@plt
```

This entry doesn’t directly point to `printf()` in `libc` yet. Instead:

### 2. The PLT entry looks like this:
```asm
jmp QWORD PTR [got+offset]  ; jumps to address stored in GOT
```

### 3. But the **GOT entry for `printf`** currently points to the **next PLT stub**, which calls the **dynamic linker (resolver)**.

In simplified terms, PLT looks like:
```asm
plt_printf:
    jmp [got_printf]         ; GOT entry not resolved yet
    push <index>
    jmp plt[0]               ; Call dynamic linker
```

So it:

- Tries `jmp [got_printf]` → follows to PLT[0]
- Pushes an index into `.rel.plt` (used by the linker to know what to resolve)
- Jumps to `plt[0]` → dynamic linker stub

---

### 4. The dynamic linker (`ld.so`) takes over:

- It reads the `.rel.plt` section to know that the program wants to resolve `printf`.
- It looks up `printf` in the loaded shared libraries (e.g., `libc.so.6`) using ELF symbol tables.
- It finds the actual address of `printf`.
- **It writes this resolved address into the GOT entry for `printf`.**

### 🔁 Execution returns back and finally jumps to the real `printf()` function.

---

## 🧠 Second Call to the Same Function

Now, when the binary calls `printf()` again:

- The PLT stub still does `jmp [got_printf]`.
- **But this time**, `got_printf` **contains the real address of `printf`** (resolved during the first call).
- So it **jumps directly to `printf()`** in `libc`.

✅ No more resolver calls — just a direct call via the GOT.

---

### 📊 Analogy:
| Call Time | What Happens |
|-----------|--------------|
| First     | PLT → GOT (empty) → Resolver → GOT updated → call real function |
| Second+   | PLT → GOT (resolved) → Direct jump to real function |

---

### 🧩 Why Use PLT and GOT?
- **Efficiency**: Only resolve symbols when needed (lazy binding).
- **Flexibility**: Support runtime symbol resolution, dynamic libraries, LD_PRELOAD tricks.
- **Security Insight**: Knowing GOT/PLT helps in exploiting binaries (e.g., GOT overwrite attacks).

---

### 🧰 You Can Try This Yourself
Use `objdump` or `readelf` to see PLT/GOT:

```bash
objdump -d ./your_binary | less   # Look for .plt section
readelf -r ./your_binary          # Look for .rel.plt or .rela.plt
```

Use `gdb` to step through the first and second calls to a function to observe this in action.

---

Let me know if you want a visual diagram of this flow or want to explore **how GOT overwrites lead to control flow hijacking** (e.g., in buffer overflow attacks).