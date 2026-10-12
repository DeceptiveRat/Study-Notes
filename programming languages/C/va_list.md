
```c
va_list arguments;
va_start(arguments, variable_count);
// logic
variable = va_arg(arguments, <data type>);
va_end(arguments);
```
