In C++, formatting output can be controlled using various features of the C++ Standard Library, including:

### 1. **Basic Output Using `cout`**
`std::cout` is the most common way to output to the console in C++. It belongs to the `<iostream>` header.

#### Example:
```cpp
#include <iostream>

int main() {
    int age = 25;
    std::cout << "I am " << age << " years old." << std::endl;
    return 0;
}
```
- `std::endl` inserts a newline character and flushes the output buffer.
- You can chain multiple values with `<<` to print them sequentially.

### 2. **Formatting Output Using `iomanip`**

For more advanced formatting, the `<iomanip>` library provides several manipulators for controlling the appearance of the output.

#### 2.1 **Width (`setw`)**
`std::setw(n)` sets the width of the field for the next output item.

#### Example:
```cpp
#include <iostream>
#include <iomanip>

int main() {
    std::cout << std::setw(10) << 123 << std::endl;
    std::cout << std::setw(10) << 456 << std::endl;
    return 0;
}
```
Output:
```
       123
       456
```
- **Note**: `std::setw` only affects the next value printed.

#### 2.2 **Fill Character (`setfill`)**
By default, the width is padded with spaces, but you can change this using `std::setfill()`.

#### Example:
```cpp
#include <iostream>
#include <iomanip>

int main() {
    std::cout << std::setfill('0') << std::setw(5) << 42 << std::endl;
    return 0;
}
```
Output:
```
00042
```

#### 2.3 **Floating Point Precision (`setprecision`)**
`std::setprecision(n)` sets the number of significant digits for floating-point numbers.

#### Example:
```cpp
#include <iostream>
#include <iomanip>

int main() {
    double pi = 3.14159;
    std::cout << std::setprecision(2) << pi << std::endl;  // Rounds to 2 significant digits
    std::cout << std::setprecision(5) << pi << std::endl;  // Rounds to 5 significant digits
    return 0;
}
```
Output:
```
3.1
3.1416
```

#### 2.4 **Fixed Decimal Precision (`fixed`)**
When you want to control the number of decimal places (not significant digits), use `std::fixed`.

#### Example:
```cpp
#include <iostream>
#include <iomanip>

int main() {
    double pi = 3.14159;
    std::cout << std::fixed << std::setprecision(2) << pi << std::endl;  // Exactly 2 decimal places
    return 0;
}
```
Output:
```
3.14
```

#### 2.5 **Show Decimal Point (`showpoint`)**
By default, integers won’t show a decimal point. You can force a decimal to appear with `std::showpoint`.

#### Example:
```cpp
#include <iostream>
#include <iomanip>

int main() {
    int a = 42;
    std::cout << std::showpoint << a << std::endl;
    return 0;
}
```
Output:
```
42.000
```

### 3. **Formatting Numbers**

#### 3.1 **Scientific Notation (`scientific`)**
To print floating-point numbers in scientific notation, use `std::scientific`.

#### Example:
```cpp
#include <iostream>
#include <iomanip>

int main() {
    double pi = 3.14159;
    std::cout << std::scientific << pi << std::endl;
    return 0;
}
```
Output:
```
3.141590e+00
```

#### 3.2 **Hex, Octal, and Decimal Base Formatting**
You can change the base of numbers using `std::hex`, `std::oct`, or `std::dec` manipulators.

#### Example:
```cpp
#include <iostream>

int main() {
    int num = 255;
    std::cout << "Decimal: " << num << std::endl;
    std::cout << "Hexadecimal: " << std::hex << num << std::endl;
    std::cout << "Octal: " << std::oct << num << std::endl;
    return 0;
}
```
Output:
```
Decimal: 255
Hexadecimal: ff
Octal: 377
```

#### 3.3 **Show Base Prefix (`showbase`)**
You can use `std::showbase` to show the base prefix (0x for hex, 0 for octal).

#### Example:
```cpp
#include <iostream>
#include <iomanip>

int main() {
    int num = 255;
    std::cout << std::showbase;
    std::cout << "Hexadecimal: " << std::hex << num << std::endl;
    std::cout << "Octal: " << std::oct << num << std::endl;
    return 0;
}
```
Output:
```
Hexadecimal: 0xff
Octal: 0377
```

### 4. **Flags for Adjusting Alignment**
#### 4.1 **Left, Right, and Internal**
- `std::left` and `std::right` control the alignment of the text inside the field.
- `std::internal` can be used to position the sign (if any) on the left and the number on the right.

#### Example:
```cpp
#include <iostream>
#include <iomanip>

int main() {
    std::cout << std::left << std::setw(10) << 123 << "Left aligned" << std::endl;
    std::cout << std::right << std::setw(10) << 123 << "Right aligned" << std::endl;
    std::cout << std::internal << std::setw(10) << -123 << "Internal aligned" << std::endl;
    return 0;
}
```
Output:
```
123       Left aligned
       123Right aligned
-       123Internal aligned
```

### 5. **Combining Manipulators**
You can combine multiple manipulators to get the desired effect. Remember that some manipulators (like `setw`) only apply to the next value, while others (like `setfill` or `fixed`) stay active until changed.

#### Example:
```cpp
#include <iostream>
#include <iomanip>

int main() {
    std::cout << std::fixed << std::setprecision(2) << std::setw(10) << std::setfill('*') << 3.14159 << std::endl;
    return 0;
}
```
Output:
```
****3.14
```

### 6. **Conclusion**
To format output in C++, you use manipulators from the `<iomanip>` and `<iostream>` libraries, which allow you to control field width, alignment, precision, and number formats. By mastering these tools, you can create clean and professional output for your C++ programs.