1. Living Off The Land (LOL)
- exploits legitimate system tools
- reduces risk of detection

2. Bring Your Own Land (BYOL)
- emulate LOL via .NET assemblies executed entirely in memory
- an illustration of this is the execute-assembly command in CobaltStrike
   - allows user to execute .NET assemblies directly from memory
- can be detected by scrutinizing the activity related to the loading of .NET associated DLLs, such as clr.dll and mscoree.dll

references:
- HTB academy Windows Event Logs & Finding Evil module
<https://academy.hackthebox.com/module/216/section/2325>