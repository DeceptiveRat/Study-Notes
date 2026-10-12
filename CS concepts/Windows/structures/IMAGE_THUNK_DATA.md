
```cpp
typedef struct _IMAGE_THUNK_DATA {
    union {
        uint32_t* Function;             // address of imported function
        uint32_t  Ordinal;              // ordinal value of function
        PIMAGE_IMPORT_BY_NAME AddressOfData;        // RVA of imported name
        DWORD ForwarderStringl              // RVA to forwarder string
    } u1;
} IMAGE_THUNK_DATA, *PIMAGE_THUNK_DATA;
```
