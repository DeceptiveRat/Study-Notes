1. Brute force
2. TLS Access
3. Stack canary leak

```c
  char memo[8];
  char name[8];
  
  printf("name : ");
  read(0, name, 64);
  printf("hello %s\n", name);
  
  printf("memo : ");
  read(0, memo, 64);
```

input 9 bytes into name => canary value printed along name
overflow memo using canary value to bypass check