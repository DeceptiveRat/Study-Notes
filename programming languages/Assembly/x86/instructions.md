## 1) lea
- used to put memory address into destination
- useful when calculating values, since it requires less instructions

## 2) xor
- xor eax eax; can quickly set eax to 0, only using 2 bytes

## 3) shr, shl
- CF contains the last bit shifted out of the destination

## 4) pusha, pushad, popa, popad
- pusha(popa) pushes(pops) 16-bit registers on the stack in order:
AX, CX, DX, BX, SP, BP, SI, DI
- pushad(popad) pushes(pops) 32-bit registers on the stack in order:
EAX, ECX, EDX, EBX, ESP, EBP, ESI, EDI
- typically indicates hand-coded assembly or shellcode

## 5) movsx
- x: b(byte), w(word), d(double word)
- syntax:
<prefix> movsx
- prefix:
   - rep: repeat until ECX = 0
   - repe/repz: repeat until ECX = 0 or ZF = 0
   - repne/repnz: repeat until ECX = 0 or ZF = 1
- moves x at ESI and stores it in EDI
- ESI and EDI registers are decremented each time if DF != 0

## 6) cmpsx
- syntax:
<prefix> cmpsx
- compare ESI with EDI

## 7) scasx
- scasb compares byte stored in AL with EDI. The location is stored in ESI

## 8) stosx
- store value in EAX to EDI

