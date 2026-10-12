- io.BytesIO

```sh
import io

# Your initial data array (bytes)
data = b'\x01\x02\x03\x04\x05\x06\x07\x08\x09\x10'

# Wrap it in a buffer
buffer = io.BytesIO(data)

# Read sequentially
chunk1 = buffer.read(4)  # Returns b'\x01\x02\x03\x04'
chunk2 = buffer.read(2)  # Returns b'\x05\x06'
chunk3 = buffer.read(4)  # Returns b'\x07\x08\x09\x10'
```
