1. Java serialization
- process of converting living object in memory to static stream of bytes
- allows storing object to disk, sending over network, etc
- <=> deserialization

2. attacking serialization
- when rebuilding objects, Java calls internal methods such as **readObject()**
- sending arbitrary code is not possible; instead gadgets in environment have to be used: Property Oriented Programming(POP):
   1. find sequence of code snippets that can be used (gadgets)
   2. link gadgets together into gadget chain
   3. **readObject()** is triggered upon deserialization resulting in RCE