## loading elf files

```python3
e = ELF('/bin/bash')
# [*] '/bin/bash'
#     Arch:     amd64-64-little
#     RELRO:    Partial RELRO
#     Stack:    Canary found
#     NX:       NX enabled
#     PIE:      No PIE
#     FORTIFY:  Enabled
```


## using symbols
elf files have sets of symbols, each contained in a dictionary of {name: data}

```python3
e = ELF('/bin/bash')

print "%#x -> license" % e.symbols['bash_license']
print "%#x -> execve" % e.symbols['execve']
print "%#x -> got.execve" % e.got['execve']
print "%#x -> plt.execve" % e.plt['execve']
print "%#x -> list_all_jobs" % e.functions['list_all_jobs'].address

#0x4ba738 -> license
#0x41db60 -> execve
#0x6f0318 -> got.execve
#0x41db60 -> plt.execve
#0x446420 -> list_all_jobs
```


## changing base address
