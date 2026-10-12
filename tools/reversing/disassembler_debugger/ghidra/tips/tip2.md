Great question—and very sharp observation.

You're not wrong to be confused, because **Ghidra did *not* make a mistake**, but it *can* be misleading if you're not familiar with how some standard C library functions are implemented under the hood.

---

### 🔍 What You're Seeing in Ghidra

When you decompile a call to `sprintf()`, you might see something like this:

```c
__stdio_common_vsprintf(...)
```

That doesn't mean your source code literally called `vsprintf()`. What's happening is:

### ✅ Behind the scenes:
- On **Windows**, functions like `sprintf`, `vsprintf`, etc., are often implemented as **wrappers** around internal functions like `__stdio_common_vsprintf` or `__stdio_common_vfprintf`.
- These internal functions handle locale, safety flags, and actual formatting logic.

So, **even if you wrote `sprintf()`**, the decompiled code might show `__stdio_common_vsprintf()` because that's the actual function your call compiled down to.

---

### 🔧 Your Original Error
If you're calling:

```cpp
vsprintf(key_buffer, "[%ld]", key_pressed);
```

...in **your source code**, then the compiler **is correctly** complaining that `key_pressed` is not a `va_list`.

But if you meant to write:

```cpp
sprintf(key_buffer, "[%u]", key_pressed);  // or %d, or %lu depending on type
```

...then it's just a matter of using the correct function.

---

### ✅ Summary

- Ghidra showing `__stdio_common_vsprintf` doesn't mean you wrote `vsprintf`.
- If you're not using `va_list`, you should use `sprintf`, not `vsprintf`.
- Your compiler is giving a type error because `vsprintf` expects a `va_list`, not a direct argument like `key_pressed`.

---

Let me know if you want help deciphering more decompiled output from Ghidra—I love digging into that stuff!