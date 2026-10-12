## 1. Structure

```cpp
typedef struct _TEB {
  PVOID Reserved1[12];
  PPEB  ProcessEnvironmentBlock;
  PVOID Reserved2[399];
  BYTE  Reserved3[1952];
  PVOID TlsSlots[64];
  BYTE  Reserved4[8];
  PVOID Reserved5[26];
  PVOID ReservedForOle;
  PVOID Reserved6[4];
  PVOID TlsExpansionSlots;
} TEB, *PTEB;
```

- TlsSlots: data for Thread Local Storage
- TlsExpansionSlots: additional data for Thread Local Storage

reference:
<https://learn.microsoft.com/en-us/windows/win32/api/winternl/ns-winternl-teb>

## 2. Notes
- the !teb command in WinDbg displays a summary of the TEB
- a more detailed version of the TEB structure can be found in the WineHQ project version of winternl.h:
<https://github.com/wine-mirror/wine/blob/1aff1e6a370ee8c0213a0fd4b220d121da8527aa/include/winternl.h#L347>
- can access using __readfsdword()

reference: 
<https://en.wikipedia.org/wiki/Win32_Thread_Information_Block>