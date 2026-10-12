## Structure

```c
typedef struct _IMAGE_NT_HEADERS64 {
    DWORD Signature;
    IMAGE_FILE_HEADER FileHeader;
    IMAGE_OPTIONAL_HEADER64 OptionalHeader;
} IMAGE_NT_HEADERS64, *PIMAGE_NT_HEADERS64;

typedef struct _IMAGE_NT_HEADERS {
    DWORD Signature;
    IMAGE_FILE_HEADER FileHeader;
    IMAGE_OPTIONAL_HEADER32 OptionalHeader;
} IMAGE_NT_HEADERS32, *PIMAGE_NT_HEADERS32;
```

(IMAGE_NT_HEADERS structure from winnt.h)

## Signature
always has fixed value 0x50450000

## File Header
a.k.a The COFF File Header

```c
typedef struct _IMAGE_FILE_HEADER {
    WORD    Machine;
    WORD    NumberOfSections;
    DWORD   TimeDateStamp;
    DWORD   PointerToSymbolTable;
    DWORD   NumberOfSymbols;
    WORD    SizeOfOptionalHeader;
    WORD    Characteristics;
} IMAGE_FILE_HEADER, *PIMAGE_FILE_HEADER;
```

(IMAGE_FILE_HEADER from winnt.h)

- Machine: CPU architecture. Most notably, 0x8864 for AMD64 and 0x14c for i386
- PointerToSymbolTable & NumberOfSymbols: file offset to the COFF symbol table and number of entries, respectively. Set to 0 because the COFF debugging information is deprecated
- Characteristics: flag that indicates attributes of the file. [Complete list](https://learn.microsoft.com/en-us/windows/win32/debug/pe-format#characteristics)

## Optional Header
Specific information required to load and run the executable is stored here

difference between the 2 versions
- structure size: the 32-bit version has an additional member BaseOfData, with a total of 31 members
- data type of some members: DWORD for 32-bit, ULONGLONG for 64-bit
   - ImageBase
   - SizeOfStackReserve
   - SizeOfStackCommit
   - SizeOfHeapReserve
   - SizeOfHeapCommit


```c
typedef struct _IMAGE_OPTIONAL_HEADER {
    //
    // Standard fields.
    //

    WORD    Magic;
    BYTE    MajorLinkerVersion;
    BYTE    MinorLinkerVersion;
    DWORD   SizeOfCode;
    DWORD   SizeOfInitializedData;
    DWORD   SizeOfUninitializedData;
    DWORD   AddressOfEntryPoint;
    DWORD   BaseOfCode;
    DWORD   BaseOfData;

    //
    // NT additional fields.
    //

    DWORD   ImageBase;
    DWORD   SectionAlignment;
    DWORD   FileAlignment;
    WORD    MajorOperatingSystemVersion;
    WORD    MinorOperatingSystemVersion;
    WORD    MajorImageVersion;
    WORD    MinorImageVersion;
    WORD    MajorSubsystemVersion;
    WORD    MinorSubsystemVersion;
    DWORD   Win32VersionValue;
    DWORD   SizeOfImage;
    DWORD   SizeOfHeaders;
    DWORD   CheckSum;
    WORD    Subsystem;
    WORD    DllCharacteristics;
    DWORD   SizeOfStackReserve;
    DWORD   SizeOfStackCommit;
    DWORD   SizeOfHeapReserve;
    DWORD   SizeOfHeapCommit;
    DWORD   LoaderFlags;
    DWORD   NumberOfRvaAndSizes;
    IMAGE_DATA_DIRECTORY DataDirectory[IMAGE_NUMBEROF_DIRECTORY_ENTRIES];
} IMAGE_OPTIONAL_HEADER32, *PIMAGE_OPTIONAL_HEADER32;

typedef struct _IMAGE_OPTIONAL_HEADER64 {
    WORD        Magic;
    BYTE        MajorLinkerVersion;
    BYTE        MinorLinkerVersion;
    DWORD       SizeOfCode;
    DWORD       SizeOfInitializedData;
    DWORD       SizeOfUninitializedData;
    DWORD       AddressOfEntryPoint;
    DWORD       BaseOfCode;
    ULONGLONG   ImageBase;
    DWORD       SectionAlignment;
    DWORD       FileAlignment;
    WORD        MajorOperatingSystemVersion;
    WORD        MinorOperatingSystemVersion;
    WORD        MajorImageVersion;
    WORD        MinorImageVersion;
    WORD        MajorSubsystemVersion;
    WORD        MinorSubsystemVersion;
    DWORD       Win32VersionValue;
    DWORD       SizeOfImage;
    DWORD       SizeOfHeaders;
    DWORD       CheckSum;
    WORD        Subsystem;
    WORD        DllCharacteristics;
    ULONGLONG   SizeOfStackReserve;
    ULONGLONG   SizeOfStackCommit;
    ULONGLONG   SizeOfHeapReserve;
    ULONGLONG   SizeOfHeapCommit;
    DWORD       LoaderFlags;
    DWORD       NumberOfRvaAndSizes;
    IMAGE_DATA_DIRECTORY DataDirectory[IMAGE_NUMBEROF_DIRECTORY_ENTRIES];
} IMAGE_OPTIONAL_HEADER64, *PIMAGE_OPTIONAL_HEADER64;
```

(IMAGE_OPTIONAL_HEADER from winnt.h)

- magic: identifies the state of the image:
   - 0x10b: PE32
   - 0x20b: PE32+
   - 0x107: ROM
- ImageBase: preferred base address
- SectionAlignment: sections are aligned in memory boundaries that are multiples of this value
- FileAlignment: value that gets used for section raw data alignment on disk
- Win32VersionValue: reserved field set to 0
- SizeOfImage: size of image file rounded up to a multiple of SectionAlignment. Used when loading image into memory
- SizeOfHeaders: combined size of the DOS stub, PE header, and section headers rounded up to a multiple of FileAlignment
- Subsystem: specifies the Windows subsystem that is required to run the image. [Complete list](https://learn.microsoft.com/en-us/windows/win32/debug/pe-format#windows-subsystem)
- DLLCharacteristics: characteristics of the executable image file. [Complete list](https://learn.microsoft.com/en-us/windows/win32/debug/pe-format#dll-characteristics)
- LoaderFlags: reserved field set to 0
- NumberOfRvaAndSizes: size of the DataDirectory array
- DataDirectory: array of IMAGE_DATA_DIRECTORY structures. IMAGE_NUMBEROF_DIRECTORY_ENTRIES has the value 16

reference:
<https://0xrick.github.io/win-internals/pe4/>