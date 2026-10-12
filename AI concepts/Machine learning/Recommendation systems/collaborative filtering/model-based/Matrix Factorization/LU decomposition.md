1. LU decomposition
![unnamed_04bf515bd3484820be2bb29c2ce06246](unnamed_04bf515bd3484820be2bb29c2ce06246.png)
L:
- lower triangular matrix
U:
- upper triangular matrix

2. demonstration
![unnamed_77dc8ad003f7423f8a618573d181df5e](unnamed_77dc8ad003f7423f8a618573d181df5e.png)
- divide a~21~ by a~11~ and multiply with R1. Subtract it from R2

![unnamed_1f3134b2163e4697aacec67535fb086d](unnamed_1f3134b2163e4697aacec67535fb086d.png)![unnamed_82516dd052c24e22ab6052354af90c61](unnamed_82516dd052c24e22ab6052354af90c61.png)
multiplier: 2

- replace a~31~ the same way
R~3~ = <-2|5|5> - (-2/2)*<2|1|3>
![unnamed_7ff42b682b1c4226b0d6bc0f19a242b3](unnamed_7ff42b682b1c4226b0d6bc0f19a242b3.png)
multiplier: -1

- replace a~32~ the same way

![unnamed_f6532d8056b641c9ac55364bd44d2e48](unnamed_f6532d8056b641c9ac55364bd44d2e48.png)![unnamed_8fdeda366c904828865bf892cd39ab27](unnamed_8fdeda366c904828865bf892cd39ab27.png)
multiplier: -2

- L matrix use multipliers from the U matrix in the same indices
![unnamed_f293ab64e57b4071acb190e49bf0554a](unnamed_f293ab64e57b4071acb190e49bf0554a.png)

reference:
- Gachon University - Machine learning lecture