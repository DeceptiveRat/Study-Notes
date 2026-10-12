1. windows.info plugin
- extracts basic OS metadata

2. output
- kernel base:
   - virtual address of Windows Kernel(ntoskrnl.exe)
- Directory Table Base(DTB):
   - page table root (CR3 register)
   - use to translate virtual memory to physical address
- architecture information
- IsPAE:
   - Physical Address Extension(PAE) allows 32-bit windows to address 4GB RAM with 36-bit physical addresses
- MachineType:
   - 332 = IMAGE_FILE_MACHINE_I386
- NTBuildLab
- NTMajorVersion
- NTMinorVersion
- KdDebuggerDataBlock:
   - address of KDDEBUGGER_DATA64 struct
   - stores pointers to many important kernel lists
- KdVersionBlock
- KeNumberProcessors
- NtSystemRoot
- Symbols file:
   - PDB debug symbols downloaded
