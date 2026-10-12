## packing/unpacking integers
- pack
- unpack

```python3
pack(1)
# '\x01\x00\x00\x00'

pack(-1)
# '\xff\xff\xff\xff'

pack(2**32 - 1)
# '\xff\xff\xff\xff'

pack(1, endian='big')
# '\x00\x00\x00\x01'

p16(1)
# '\x01\x00'

hex(unpack('AAAA'))
# '0x41414141'

hex(u16('AA'))
# '0x4141'
```


## file I/O
- write()
- read()

```python3
write('filename', 'data')
read('filename')
# 'data'
read('filename', 1)
# 'd'
```


## hashing and encoding
- b64d()
- b64e()
- md5sumhex()
- md5filehex()
- sha1sumhex()
- urlencode()
- enhex()
- unhex()
- bits()
- unbits()

```python3
bits(0b1000001) == bits('A')
# [0, 0, 0, 1, 0, 1, 0, 1]
unbits([0,1,0,1,0,1,0,1])
# 'U'
```

- hexdump()

## pattern generation
- cyclic_gen()
- cyclic()
- cyclic_find()

```python3
g = cyclic_gen()
io.send(cyclic(512))
cyclic_find(0x61616178)
# 92
```
