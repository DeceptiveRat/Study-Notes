## Import Directory Table
a data directory located at the beginning of .idata

consists of an array of IMAGE_IMPORT_DESCRIPTOR structures, each for a DLL. It doesn't have a fixed size so the last structure is zeroed-out to indicate the end

```c
typedef struct _IMAGE_IMPORT_DESCRIPTOR {
    union {
        DWORD   Characteristics;
        DWORD   OriginalFirstThunk;
    } DUMMYUNIONNAME;
    DWORD   TimeDateStamp;
    DWORD   ForwarderChain;
    DWORD   Name;
    DWORD   FirstThunk;
} IMAGE_IMPORT_DESCRIPTOR;
typedef IMAGE_IMPORT_DESCRIPTOR UNALIGNED *PIMAGE_IMPORT_DESCRIPTOR;
```

- OriginalFirstThunk: RVA of the ILT
- TimeDateStamp: initially set to 0 if not bound and set to -1 if bound. Stays -1 in case of a bound import
- ForwarderChain: index of the first forwarder chain 
- Name: RVA of name of the DLL
- FirstThunk: RVA of the IAT

## Bound Imports
- import table contains fixed addresses for the imported functions
- Calculated and written during compile time by the linker
- reduced the time needed by the loader to resolve function addresses and fill the IAT

## Bound Import Data Directory
consists of an array of IMAGE_BOUND_IMPORT_DESCRIPTOR structures, with the last one zeroed-out

```c
typedef struct _IMAGE_BOUND_IMPORT_DESCRIPTOR {
    DWORD   TimeDateStamp;
    WORD    OffsetModuleName;
    WORD    NumberOfModuleForwarderRefs;
// Array of zero or more IMAGE_BOUND_FORWARDER_REF follows
} IMAGE_BOUND_IMPORT_DESCRIPTOR,  *PIMAGE_BOUND_IMPORT_DESCRIPTOR;
```

- OffsetModuleName: offset to name of imported DLL from the first IMAGE_BOUND_IMPORT_DESCRIPTOR
- NumberOfModuleForwarderRefs: number of IMAGE_BOUND_FORWARDER_REF structures that immediately follow this structure. IMAGE_BOUND_FORWARDER_REF structures are identical to IMAGE_BOUND_IMPORT_DESCRIPTOR, but with this member reserved

## Import Lookup Table
- a.k.a. Import Name Table
- consists of an array of 32-bit (PE32) or 64-bit (PE32+) numbers with the last one zeroed-out
   - bit 31/63 (MSB): Ordinal/Name flag. Specified whether to import by name or ordinal
   - bits 15 - 0: if Ordinal/Name flag is set to 1, holds the 16-bit ordinal number used to import the function. Bits 30/62 - 16 must be set to 0
   - bits 30 - 0: if the Ordinal/Name flag is set to 0, holds an RVA to a Hint/Name table

## Hint/Name Table

```c
typedef struct _IMAGE_IMPORT_BY_NAME {
    WORD    Hint;
    CHAR   Name[1];
} IMAGE_IMPORT_BY_NAME, *PIMAGE_IMPORT_BY_NAME;
```

(IMAGE_IMPORT_BY_NAME from winnt.h)
- Hint: contains a number used to look-up the function
- Name: contains name of function to import

## Import Address Table
identical to the ILT on disk. Entries get overwritten with the addresses of the functions when the binary is loaded into memory

reference:
<https://0xrick.github.io/win-internals/pe6/>