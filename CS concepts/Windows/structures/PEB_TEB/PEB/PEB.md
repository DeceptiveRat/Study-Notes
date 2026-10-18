## 1. Structure

```cpp
typedef struct _PEB {
  BYTE                          Reserved1[2];
  BYTE                          BeingDebugged;
  BYTE                          Reserved2[1];
  PVOID                         Reserved3[2];
  PPEB_LDR_DATA                 Ldr;
  PRTL_USER_PROCESS_PARAMETERS  ProcessParameters;
  PVOID                         Reserved4[3];
  PVOID                         AtlThunkSListPtr;
  PVOID                         Reserved5;
  ULONG                         Reserved6;
  PVOID                         Reserved7;
  ULONG                         Reserved8;
  ULONG                         AtlThunkSListPtr32;
  PVOID                         Reserved9[45];
  BYTE                          Reserved10[96];
  PPS_POST_PROCESS_INIT_ROUTINE PostProcessInitRoutine;
  BYTE                          Reserved11[128];
  PVOID                         Reserved12[1];
  ULONG                         SessionId;
} PEB, *PPEB;
```

- Ldr: a pointer to a [[PEB_LDR_DATA]] structure that contains information about the loaded modules for the process
- ProcessParameters: a pointer to an RTL_USER_PROCESS_PARAMETERS structure that contains process parameter information such as the command line
- PostProcessInitRoutine: pointer to a callback function called after DLL initialization but before main code execution. Not guaranteed to be used on versions after Windows 2000
- SessionId: Terminal Services session id associated with current process

## See also
- [[TEB|Thread Environment Block (TEB)]]
- [[PEB_LDR_DATA]]

reference: 
<https://learn.microsoft.com/en-us/windows/win32/api/winternl/ns-winternl-peb>
<https://en.wikipedia.org/wiki/Process_Environment_Block>

## 2. Notes
- the !peb command in WinDbg displays a summary of the PEB
- a more detailed version of the PEB structure can be found in the WineHQ project version of winternl.h:
<https://github.com/wine-mirror/wine/blob/1aff1e6a370ee8c0213a0fd4b220d121da8527aa/include/winternl.h#L269>
- can access using __readgsqword()
- 
reference:
<https://metehan-bulut.medium.com/understanding-the-process-environment-block-peb-for-malware-analysis-26315453793f>