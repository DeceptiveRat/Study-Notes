
```cpp
typedef struct _UNICODE_STRING {
  USHORT Length;
  USHORT MaximumLength;
  PWSTR  Buffer;
} UNICODE_STRING, *PUNICODE_STRING;
```


reference:
<https://learn.microsoft.com/en-us/windows/win32/api/subauth/ns-subauth-unicode_string>