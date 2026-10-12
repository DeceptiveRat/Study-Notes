Here's a simplified version of the **Microsoft x64 calling convention** for your notes:  

### **Microsoft x64 Calling Convention (Simplified)**  

1. **Registers Used for Arguments**:  
   - The first **four** integer or pointer arguments are passed in **RCX, RDX, R8, R9** (in order).  
   - Floating-point arguments are passed in **XMM0, XMM1, XMM2, XMM3**.  
   - Additional arguments are passed **on the stack** (right to left).  

2. **Stack and Shadow Space**:  
   - The caller **allocates 32 bytes** (shadow space) on the stack before the call.  
   - The shadow space is for **RCX, RDX, R8, R9**, even if not all are used.  
   - The stack must be **16-byte aligned** before a `CALL`.  

3. **Return Values**:  
   - Integer/pointer return values are in **RAX**.  
   - Floating-point return values are in **XMM0**.  

4. **Caller-Saved (Volatile) Registers** (May be clobbered by the function):  
   - **RAX, RCX, RDX, R8, R9, R10, R11**  

5. **Callee-Saved (Non-Volatile) Registers** (Must be preserved if used):  
   - **RBX, RBP, RDI, RSI, R12, R13, R14, R15**  
   - **RSP** must be restored to its original value.  

6. **Function Prologue/Epilogue** (Typical example):  
   ```assembly
   push rbp            ; Save old base pointer
   mov rbp, rsp        ; Set up new base pointer
   sub rsp, <space>    ; Allocate local variables (if needed)

   ; Function body

   mov rsp, rbp        ; Restore stack pointer
   pop rbp             ; Restore old base pointer
   ret
   ```

This keeps it compact while covering the essentials. Let me know if you want further simplifications!