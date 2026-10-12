To read and parse DNS messages, especially if you’re building a packet sniffer, it’s essential to understand the structure of the DNS message format and how offsets work in the DNS protocol. Here’s a detailed breakdown of each component of a DNS message, including how to handle offsets in domain names:

### 1. **DNS Message Structure Overview**

A DNS message, whether a query or a response, consists of these main sections:

- **Header (12 bytes)**
- **Question Section** (in queries)
- **Answer Section** (in responses)
- **Authority Section** (in responses)
- **Additional Section** (in responses or EDNS-enabled queries)

Each section may have multiple resource records (RRs), and each RR has its own format.

### 2. **Reading the DNS Header**

The DNS header is always 12 bytes, with the following fields:

| Field            | Size   | Description                                                                                  |
|------------------|--------|----------------------------------------------------------------------------------------------|
| Transaction ID   | 2 bytes | Unique identifier for matching queries and responses.                                       |
| Flags            | 2 bytes | Contains flags for the message type, error codes, recursion, etc.                           |
| Questions        | 2 bytes | Number of entries in the Question Section.                                                  |
| Answer RRs       | 2 bytes | Number of entries in the Answer Section.                                                    |
| Authority RRs    | 2 bytes | Number of entries in the Authority Section.                                                 |
| Additional RRs   | 2 bytes | Number of entries in the Additional Section.                                                |

This header provides the structure of the message and tells you how many records to expect in each section.

### 3. **Parsing the Question Section**

Each question in this section has three fields:

- **Name**: The domain name being queried, which can include offsets (more on this below).
- **Type**: The type of DNS record requested (e.g., `A`, `AAAA`, `MX`).
- **Class**: Usually `IN` (Internet).

#### Domain Name Encoding with Labels and Offsets

Domain names in DNS messages are encoded as **labels**. Each label is a length-prefixed string, ending with a zero-length label (0x00) indicating the end of the domain name. However, **offsets** (or **pointers**) are also used for compression to save space in DNS messages, especially for longer domain names.

#### How Offsets Work

- **Labels**: Each segment of a domain name (e.g., `www`, `example`, `com`) is represented as a length-prefixed string. For example, `www.example.com` would look like `3www7example3com0`.
  - Each label starts with a length byte, followed by the string data.
  - The domain ends with a single byte of `0x00`, which marks the end.

- **Offsets (or Pointers)**: If a domain name is repeated or partially repeated elsewhere in the message, DNS uses a **two-byte offset** to point back to the first occurrence.
  - The first two bits of an offset are set to `11` (binary), indicating that the next 14 bits are the offset from the beginning of the DNS message.
  - For example, if a pointer is `0xC00C`, you’d skip to byte `0x000C` (12 bytes in from the start) to find the rest of the domain name.

Using offsets makes parsing tricky because you need to recognize when an offset is being used and then follow the pointer to the correct location in the message to read the domain name.

### Example of Domain Name Parsing with Offsets

Let’s say you have a DNS message containing the name `www.example.com` in the Question Section, and in the Answer Section, it appears again but with an offset.

1. **In the Question Section**:
   - You’ll see `3www7example3com0`, which translates to `www.example.com`.

2. **In the Answer Section**:
   - Instead of repeating `3www7example3com0`, it might contain an offset like `0xC00C`, meaning "jump to byte 12 and read the domain name from there."
   - This allows the DNS message to be shorter by not duplicating data.

### 4. **Reading the Answer, Authority, and Additional Sections**

Each resource record in these sections has a format like this:

| Field           | Size    | Description                                                                                 |
|-----------------|---------|---------------------------------------------------------------------------------------------|
| Name            | Variable | The domain name or a pointer to it, as described above.                                     |
| Type            | 2 bytes  | The type of DNS record (e.g., `A`, `AAAA`, `CNAME`, `NS`).                                 |
| Class           | 2 bytes  | Usually `IN` for Internet.                                                                  |
| TTL             | 4 bytes  | Time-to-live for caching purposes.                                                          |
| Data Length     | 2 bytes  | Length of the data field.                                                                   |
| Data            | Variable | The actual data (e.g., IP address for `A` record, hostname for `CNAME`).                   |

Each record may use offsets to reference domain names, which means you’ll often encounter `0xC0` as the first byte in the `Name` field.

### Example Code for Parsing a DNS Message

Here’s a pseudocode outline for handling offsets in domain names:

```python
def parse_domain_name(data, offset):
    labels = []
    while True:
        length = data[offset]
        
        # Check if it's an offset
        if (length & 0xC0) == 0xC0:
            # Get the pointer and resolve it
            pointer = ((length & 0x3F) << 8) | data[offset + 1]
            labels.append(parse_domain_name(data, pointer))
            offset += 2
            break
        elif length == 0:
            # End of the domain name
            offset += 1
            break
        else:
            # Read a label
            offset += 1
            labels.append(data[offset:offset + length].decode("utf-8"))
            offset += length

    return ".".join(labels), offset
```

### 5. **Putting It All Together**

1. **Read the Header** to get the number of Questions, Answers, Authority, and Additional Records.
2. **Parse the Question Section** by reading each domain name, checking for offsets, and decoding accordingly.
3. **Parse the Answer/Authority/Additional Sections** by:
   - Checking each name field for offsets.
   - Reading the Type, Class, TTL, Data Length, and Data based on the record’s type (IP for `A`, hostname for `CNAME`, etc.).

By understanding the structure and using a recursive function like `parse_domain_name` to handle offsets, you can parse DNS packets efficiently, similar to how Wireshark does it. Let me know if you’d like any specific implementation details in code!