## Overview
- data between DOS stub and NT headers
- only present in executables built using the Microsoft Visual Studio toolset

## Structure

| name | meaning | size |
| --- | --- | --- |
| DanS ID | DanS | 4 bytes (DWORD) |
| padding | 0 | 12 bytes<br>(3 DWORD) |
| comp ID | data entry | 8 bytes each |
| rich ID | Rich | 4 bytes<br>(DWORD) |
| checksum | XOR key | 4 bytes<br>(DWORD) |

![unnamed_7c4bd84cf7b94157a74bf66f29bf3979](unnamed_7c4bd84cf7b94157a74bf66f29bf3979.png)

reference:
<https://0xrick.github.io/win-internals/pe3/>