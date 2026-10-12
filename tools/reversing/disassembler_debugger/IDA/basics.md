![unnamed_c0613905ff8544f2b5f0b206d0372f84](unnamed_c0613905ff8544f2b5f0b206d0372f84.png)
## 1. Functions
functions in the code are shown here

![unnamed_c2dabc9b235944a09ec26134615ffd99](unnamed_c2dabc9b235944a09ec26134615ffd99.png)![unnamed_c1c2253ae9a64e88890e122b14f5168d](unnamed_c1c2253ae9a64e88890e122b14f5168d.png)
there are a variety of functions that can be found here, even ones I didn't explicitly use in the code

![unnamed_fefab5535cfb444792469a6650110429](unnamed_fefab5535cfb444792469a6650110429.png)
upon expanding the tab or scrolling, you can see there are multiple columns for each function:
- Function name
- Segment
- Start
- Length
- Locals
- Arguments
- R
function returns to the caller
- F
far function
- L
library function
- M
lumina function
- O
outlined code
- S
static function
- B
function used frame pointer (BP)
- T
function has prototype
- =
BP points at the bottom of the stack frame

(1. Functions) further reading:
[1] <https://docs.hex-rays.com/user-guide/user-interface/menu-bar/view/open-subviews#functions-window>

## 2. Subviews
### 2.1. IDA view / Disassembly Window
- graph view
![unnamed_2525ab95631d4eb8ad35751535d665af](unnamed_2525ab95631d4eb8ad35751535d665af.png)
- linear view
![unnamed_cecc09640d1745f18520dc61f3471d98](unnamed_cecc09640d1745f18520dc61f3471d98.png)
- proximity view
![unnamed_32ebebc3fe704560b73ebd0730dd2f0f](unnamed_32ebebc3fe704560b73ebd0730dd2f0f.png)
*space to change between linear view and graph view, proximity view by right clicking and selecting "proximity browser"*

### 2.2. Hex View Window
![unnamed_370996f84d284c8db4a8c899815cf0d8](unnamed_370996f84d284c8db4a8c899815cf0d8.png)
you can see the raw bytes of the instructions

### 2.3. Pseudocode Window
![unnamed_c0867161b6b1480c9f26cf57bb29262f](unnamed_c0867161b6b1480c9f26cf57bb29262f.png)
*use f5 to view*
you can see the C-like pseudocode

### 2.4. Local Types Window

![unnamed_a03f6ba42c904ec2b6c2084a8fbc1d38](unnamed_a03f6ba42c904ec2b6c2084a8fbc1d38.png)![unnamed_33ab47bc986b477487e3a05ce27fe4a9](unnamed_33ab47bc986b477487e3a05ce27fe4a9.png)
shows high-level types, such as structs or enums

(2. Subviews) further reading:
[2] <https://docs.hex-rays.com/8.5/getting-started/basic-usage>

## 3. Command line
can use IDC or Python commands

(3. Command line) further reading:
[3] <https://python.docs.hex-rays.com/?_gl=1*16bm4vn*_ga*MTY1Njg1NDc3MS4xNzQxOTI2Njg1*_ga_Y2G1VBHRDB*MTc0MTkyNjY4NS4xLjEuMTc0MTkyODkxMS4wLjAuMA..>

reference:
[1] <https://docs.hex-rays.com/user-guide/user-interface/menu-bar/view/open-subviews#functions-window>
[2] <https://docs.hex-rays.com/8.5/getting-started/basic-usage>
[3] <https://python.docs.hex-rays.com/?_gl=1*16bm4vn*_ga*MTY1Njg1NDc3MS4xNzQxOTI2Njg1*_ga_Y2G1VBHRDB*MTc0MTkyNjY4NS4xLjEuMTc0MTkyODkxMS4wLjAuMA..>