
```python3
import struct
from dataclasses import dataclass

# 1. Define the exact order of your fields
BASE_FIELDS = [
    "magic_number",         # 4 bytes (I)
    "block_size",           # 4 bytes (I)
    "total_blocks_fs",      # 8 bytes (Q)
    "num_blocks_rt_device", # 8 bytes (Q)
    "num_extents_rt_device",# 8 bytes (Q)
    "uuid",                 # 16 bytes (16s)
]

# 2. Build the format string matching those exact sizes
# >   : Big-Endian (Standard for XFS)
# I I : magic_number(4), block_size(4)
# Q Q Q: total_blocks(8), rt_blocks(8), rt_extents(8)
# 16s : uuid(16)
BASE_FORMAT = "> I I Q Q Q 16s"

def readSuperblock(superblock_bytes: bytes, is_ver5: bool) -> SUPERBLOCK:
    # Calculate how many bytes the base struct requires
    base_size = struct.calcsize(BASE_FORMAT)
    
    # Unpack the raw bytes into a tuple of values
    # e.g., (1480938306, 4096, 500000, 0, 0, b'...')
    unpacked_base_tuple = struct.unpack(BASE_FORMAT, superblock_bytes[:base_size])
    
    # Zip the field names and the unpacked values together into a dictionary
    base_data = dict(zip(BASE_FIELDS, unpacked_base_tuple))
    
    return SUPERBLOCK(**base_data)
```
