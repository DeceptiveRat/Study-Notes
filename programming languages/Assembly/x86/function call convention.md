## 1. cdecl
- parameters pushed from right to left
- caller cleans up the stack
- return value stored in EAX

## 2. stdcall
- similar to cdecl
- callee cleans up the stack
- calling convention for the Windows API

## 3. fastcall
- first few arguments, typically 2, passed in registers, usually EDX and ECX
- additional arguments loaded from right to left
- caller usually cleans up stack

