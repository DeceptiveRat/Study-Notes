1. Low-Rank Adaptation(LoRA)
- instead of updating whole parameter matrix, store 2 small matrices that can be multiplied to approximate weight update matrix, ΔW
![unnamed_f33dec13f3c545eea1ee7e9f15d3eccd](unnamed_f33dec13f3c545eea1ee7e9f15d3eccd.png)

2. core concept - matrix factorization
![unnamed_eaa0625aa49a4fc99a92ce070578cd23](unnamed_eaa0625aa49a4fc99a92ce070578cd23.png)

3. advantages
- cost reduction: trainable parameters shrunk to about 1/10000
- performance retention: similar performance achieved
- modularization: parameters are only MB in size, easily switched 
![unnamed_1464304fb3a94ef68444518021fa3b1b](unnamed_1464304fb3a94ef68444518021fa3b1b.png)

reference:
- 가천대 인공지능입문 Lecture 5 강의 자료 