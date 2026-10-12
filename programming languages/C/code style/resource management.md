1. resource types
- memory
- file descriptor
- mutex
- etc

2. management
an RB-tree can be used to manage open resources
each node of the tree should contain:
- type of resource
- unique way of identifying resource

3. exceptions
in cases where there are few resources, it might be easier to individually track and free resources