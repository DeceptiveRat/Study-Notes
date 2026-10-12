
```cpp
typedef struct _IMAGE_IMPORT_DESCRIPTOR {
    union {
        DWORD   Characteristics;            
        DWORD   OriginalFirstThunk;       // INT(Import Name Table) address (RVA)
    };
    DWORD   TimeDateStamp;
    DWORD   ForwarderChain;
    DWORD   Name;                         // library name string address (RVA)
    DWORD   FirstThunk;                   // IAT(Import Address Table) address (RVA)
} IMAGE_IMPORT_DESCRIPTOR;
```


reference:
<https://gutte.tistory.com/113>