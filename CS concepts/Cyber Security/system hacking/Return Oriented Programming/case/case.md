2024/12/17 - 11:16
while penetrating the machine "Venus" by [SirFlash](https://www.vulnhub.com/author/sirflash,731/)
(Make sure to set ASLR to 0)

1. tried exactly as the [walkthrough](https://medium.com/@mcl0x90/the-planets-venus-vulnhub-write-up-f6727d08bafb) said, but gdb-peda kept getting crashing for me
2. created python functions for gdb to create and find patterns
3. found offset of 1040, same as walkthrough
4. found location of "pop %rdi; ret" with objdump => 0x4015e3
![unnamed_8663bc1f897a4fe0b360e6da9ee4d016](unnamed_8663bc1f897a4fe0b360e6da9ee4d016.png)
objdump -d ./venus_messaging | grep -B 4 5f


5. found location of "/bin/sh" => 0x7ffff7dcb42f

![unnamed_983cd22b71fe44369b0a4d8c5a699232](unnamed_983cd22b71fe44369b0a4d8c5a699232.png)info proc mappings
find <address>, <address>, <string>

6. found location of system() function => 0x7ffff7c58740

![unnamed_765e162468e54d07adb4fff44bf39a06](unnamed_765e162468e54d07adb4fff44bf39a06.png)print system

7. created python script to launch the payload (exploit 1)

![unnamed_2c14b4492eba4d30903edfdd52af0105](unnamed_2c14b4492eba4d30903edfdd52af0105.png)![unnamed_9a5c0e3fe8074e448777521628d7c4a6](unnamed_9a5c0e3fe8074e448777521628d7c4a6.png)
kept segfaulting

8. set breakpoints and watchpoints to see what was wrong
![unnamed_c09e5211d5824174a0dde5a9f929a627](unnamed_c09e5211d5824174a0dde5a9f929a627.png)
when it segfaults, rsp is not aligned to 16 bytes

9. to make it align to 16 bytes, added one more payload that does nothing, which would make the rsp 8 bytes smaller(or is it bigger?) and align it to 16 bytes when the system() function runs (exploit 2)
![unnamed_4c08794aab544c5ca3bc5c1b55ce6121](unnamed_4c08794aab544c5ca3bc5c1b55ce6121.png)