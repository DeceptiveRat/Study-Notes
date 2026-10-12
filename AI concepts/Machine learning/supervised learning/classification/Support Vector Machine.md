1. Support Vector Machine (SVM)
- usage:
   - text categorization
   - image classification
   - bioinformatics
   - hand writing recognition
- adapted to regression
- advantages:
   - works well when margin of separation is clear
   - effective in high dimensional spaces
   - memory efficient
- disadvantages:
   - doesn't perform well for a large dataset
   - weak against noise
   - doesn't provide probability estimates

2. SVM illustration
- plot dataset
![unnamed_31a8d096ff5f41c99ae74806aaf26871](unnamed_31a8d096ff5f41c99ae74806aaf26871.png)
- find lines(planes) that correctly classify training data and pick the one with the widest margin - [1]
![unnamed_ca3d39c7d99044f9ad1600e90bdf9726](unnamed_ca3d39c7d99044f9ad1600e90bdf9726.png)

[1]: line is called separating line or classifier
closest data points that identify the line are called support vectors

3. soft margin
- more narrow margin
- allow data points inside margin
- tradeoff between wide margin and correctly classifying the dataset
- uses penalty parameter called "C"

4. C
- high value means high penalty for classification error
=> narrow margin, lower errors on training data
- value determined through cross validation
![unnamed_ba13dee994324979adadbf77df70f3d0](unnamed_ba13dee994324979adadbf77df70f3d0.png)

5. Kernel Trick
- use kernel (mapping or transformation) function to project dataset into higher dimension where it is linearly separable
- kernel is one of the hyperparameters

6. kernel trick illustration
- original data
![unnamed_b139aa51b4174b309690e7075c938581](unnamed_b139aa51b4174b309690e7075c938581.png)
- after transformation
![unnamed_65132333530340c0b5039977b82a7150](unnamed_65132333530340c0b5039977b82a7150.png)
- map hyperplane back to 2d
![unnamed_47edf0b14c2f45aa8839910f0c5a2626](unnamed_47edf0b14c2f45aa8839910f0c5a2626.png)
- with margins
![unnamed_d22eee49581c4cbaa6ea4b27a0836fb5](unnamed_d22eee49581c4cbaa6ea4b27a0836fb5.png)

7. popular kernel functions
- linear kernel
- polynomial kernel with degree d
![unnamed_a26014e2e3a8493fafd298f8d3d9038d](unnamed_a26014e2e3a8493fafd298f8d3d9038d.png)
- gaussian kernel a.k.a Radial Basis Function (RBF) kernel with width σ
![unnamed_cf9cf51f476e4604a0574f9575da39eb](unnamed_cf9cf51f476e4604a0574f9575da39eb.png)
- sigmoid kernel with parameters κ and θ


![unnamed_d1776b24a8a8491db6a4c60f2718bfb5](unnamed_d1776b24a8a8491db6a4c60f2718bfb5.png)![unnamed_12362e9f02124736987546563510ba87](unnamed_12362e9f02124736987546563510ba87.png)

8. ploynomial kernel function illustration
- X: (-2, -1, 0, 1, 2) => X^2^: (4, 1, 0, 1, 4)
![unnamed_12912974ada54a2da7c9d2737826bf99](unnamed_12912974ada54a2da7c9d2737826bf99.png)

9. RBF kernel function
- gamma = 0.1, two centers (-1, 0) and (2, 0)
- X: (-2, -1, 0, 1, 2) => X1: (0.9, 1.0, 0.9, 0.67, 0.4) and X2: (0.2, 0.4, 0.67, 0.9, 1.0)
![unnamed_be20aa9a775e43389586cfa4d5cddc9c](unnamed_be20aa9a775e43389586cfa4d5cddc9c.png)
- effect of gamma on accuracy
![unnamed_85dd62cc723747808034c18eaafc8c92](unnamed_85dd62cc723747808034c18eaafc8c92.png)

10. choices to make using SVM
- kernel
   - gaussian, polynomial is default
   - elaborate kernel used if necessary
- kernel parameters
   - gamma in Gaussian kernel
- optimization criterion (hard/soft margin, C)

reference:
- Gachon University - Machine learning lecture