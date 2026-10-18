### - new
- usage:
int *foo;
foo = new int[5];

- nothrow can be used to keep it from throwing an exception:
foo = new (nothrow) int[5];

Instead, a null pointer is returned and assigned to foo

### - delete
- usage:
int *p = new int[5];
delete[] p;

## See also
- [[rule of threes|Rule of Three (C++)]]

