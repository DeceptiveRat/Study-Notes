1. backpropagation
- efficient way to compute derivatives for neural network loss

2. simple example
- f(x,y,z) = (x+y)z
	![unnamed_4c57547e98e744ca86f5b9bf522febc3](unnamed_4c57547e98e744ca86f5b9bf522febc3.png)
   - if x = -2, y = 5, z = -4
   - f(x,y,z) = -12
   - 𝜕𝑓/𝜕𝑧 = (x+y) = 3
   - where q = x+y, 𝜕𝑓/𝜕𝑦 = 𝜕𝑓/𝜕𝑞 * 𝜕𝑞/𝜕𝑦 = z*𝜕𝑞/𝜕𝑦 = z*1 = -4; f() is linearly sensitive to y, scaled by z
   - 𝜕𝑓/𝜕𝑥 = 𝜕𝑓/𝜕𝑞 * 𝜕𝑞/𝜕𝑥 = z*1 = -4; f() is linearly sensitive to x, scaled by z
	![unnamed_2e9c9b0f570b499ea990bb8f8330fc6e](unnamed_2e9c9b0f570b499ea990bb8f8330fc6e.png)

3. upstream, local, and downstream gradients

![unnamed_ab603dd3203c49cabfe21043bff7d0af](unnamed_ab603dd3203c49cabfe21043bff7d0af.png)

![unnamed_9a035bb7f4e24e44821a56ba64acc259](unnamed_9a035bb7f4e24e44821a56ba64acc259.png)