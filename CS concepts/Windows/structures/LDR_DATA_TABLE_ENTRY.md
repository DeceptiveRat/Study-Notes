
```cpp
typedef struct _LDR_DATA_TABLE_ENTRY {
    PVOID Reserved1[2];
    LIST_ENTRY InMemoryOrderLinks;
    PVOID Reserved2[2];
    PVOID DllBase;
    PVOID EntryPoint;
    PVOID Reserved3;
    UNICODE_STRING FullDllName;
    BYTE Reserved4[8];
    PVOID Reserved5[3];
    union {
        ULONG CheckSum;
        PVOID Reserved6;
    };
    ULONG TimeDateStamp;
} LDR_DATA_TABLE_ENTRY, *PLDR_DATA_TABLE_ENTRY;
```

- offset 0x2C: FullDllName
- offset 0x30: BaseDllName


reference:
<https://learn.microsoft.com/en-us/windows/win32/api/winternl/ns-winternl-peb_ldr_data>

further reading:
<https://www.nirsoft.net/kernel_struct/vista/LDR_DATA_TABLE_ENTRY.html>
<https://sachiel-archangel.medium.com/how-to-analyze-dll-address-acquisition-process-593bc8a54988>