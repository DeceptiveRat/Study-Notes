# 1. Caller rules
- save contents of caller-saved registers (r10, r11, registers with parameters put into)
- up to 6 parameters in registers (in order: rdi, rsi, rdx, rcx, r8, r9)
- rest on stack
- remove additional parameters after returning
- return value stored in rax
- restore caller-saved registers from the stack

# 2. Callee rules
- allocate local variables using the stack or registers
- callee-saved registers must be saved by being pushed onto the stack (rbx, rbp, r12 ~ r15)
- return value in rax
- restore callee-saved registers that were modified
- restore rsp by adding offset of local variables
- ret instruction => find and remove appropriate return address from stack