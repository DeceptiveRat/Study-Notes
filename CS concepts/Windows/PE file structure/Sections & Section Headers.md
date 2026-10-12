## Special Sections
- .text: executable code
- .data: initialized data
- .bss: uninitialized data
- .rdata: read-only initialized data
- .edata: export tables
- .idata: import tables
- .reloc: image relocation information
- .rsrc: resources used by the program
- .tls: storage for every executing thread of the program

[complete list](https://learn.microsoft.com/en-us/windows/win32/debug/pe-format#special-sections)

## Section Headers

```c
typedef struct _IMAGE_SECTION_HEADER {
    BYTE    Name[IMAGE_SIZEOF_SHORT_NAME];
    union {
            DWORD   PhysicalAddress;
            DWORD   VirtualSize;
    } Misc;
    DWORD   VirtualAddress;
    DWORD   SizeOfRawData;
    DWORD   PointerToRawData;
    DWORD   PointerToRelocations;
    DWORD   PointerToLinenumbers;
    WORD    NumberOfRelocations;
    WORD    NumberOfLinenumbers;
    DWORD   Characteristics;
} IMAGE_SECTION_HEADER, *PIMAGE_SECTION_HEADER;
```

(IMAGE_SECTION_HEADER from winnt.h)
- Name: name of the section. Name can't be longer than 8 characters
- PhysicalAddress or VirtualSize: total size of the section when loaded in memory
- VirtualAddress: offset of section from image base when loaded in memory for executable images. Offset of section before relocation for object files
- SizeOfRawData: size of section on disk. Multiple of FileAlignment
- PointerToRawData: pointer to first page of the section within the files. Multiple of FileAlignment for executable images
- PointerToLineNumbers: set to 0 because COFF debugging information is deprecated
- NumberOfLineNumbers: set to 0
- Characteristics: flags the describe the characteristics. [Complete list](https://learn.microsoft.com/en-us/windows/win32/debug/pe-format#section-flags)

SizeOfRawData and VirtualSize can be different:
1. SizeOfRawData > VirtualSize
if section size is smaller than FileAlignment, SizeOfRawData is rounded up to the nearest multiple. However, when it is loaded into memory, only the actual size of the section is occupied
2. SizeOfRawData < VirtualSize
if a section contains uninitialized data, it won't use space on the disk, but will use space when loaded into memory

reference:
<https://0xrick.github.io/win-internals/pe5/>