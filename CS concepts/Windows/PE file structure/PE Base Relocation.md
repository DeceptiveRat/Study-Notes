## Relocation
A list of all hardcoded values that need fixing when the image is loaded is saved in the relocation table

## Relocation Table
- located in the .reloc section
- divided into blocks representing the base relocations for a 4K page. Each block must start on a 32-bit boundary
- each block starts with an IMAGE_BASE_RELOCATION structure followed by any number of offset field entries

```c
typedef struct _IMAGE_BASE_RELOCATION {
    DWORD   VirtualAddress;
    DWORD   SizeOfBlock;
} IMAGE_BASE_RELOCATION;
typedef IMAGE_BASE_RELOCATION UNALIGNED * PIMAGE_BASE_RELOCATION;
```

- each offset field entry is a WORD
   - first 4 bits define relocation type. [Complete list](https://learn.microsoft.com/en-us/windows/win32/debug/pe-format#base-relocation-types)
   - last 12 bits store an offset from the RVA

reference:
<https://0xrick.github.io/win-internals/pe7/>