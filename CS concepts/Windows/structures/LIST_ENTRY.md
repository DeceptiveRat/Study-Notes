
```cpp
typedef struct _LIST_ENTRY {
  struct _LIST_ENTRY *Flink;
  struct _LIST_ENTRY *Blink;
} LIST_ENTRY, *PLIST_ENTRY, PRLIST_ENTRY;
```


reference:
<https://learn.microsoft.com/en-us/windows/win32/api/ntdef/ns-ntdef-list_entry>