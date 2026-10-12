
```cpp
void UndefinedFunction_140011456(int param_1,WPARAM param_2,uint *param_3,undefined8 param_4)
{
...
thunk_FUN_140012060(acStack_110,"[%ld]",(ulonglong)uStack_134,param_4);
...
}
```

UndefinedFunction => LowLevelKeyboardProc(int nCode, WPARAM wParam, LPARAM lParam)
FUN_140012060 => vsprintf(char *buffer, const char *format, va_list argptr)

param_4 was put on R9 for whatever reason
=> it wasn't touched 
=> function call to vsprintf
=> R9 is still there, so ghidra thinks it's being passed again