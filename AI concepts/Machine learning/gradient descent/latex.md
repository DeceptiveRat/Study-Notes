\documentclass{article}
\usepackage[utf8]{inputenc}
\usepackage{amsmath}
\begin{document}
\begin{huge}
\[
h_\theta(x) = \theta X = \theta_0 + \theta_1x_1 + \theta_2x_2 + \dots + \theta_mx_m = \hat{y}
\]
\[
J(\theta) = \frac{1}{2n}\sum\limits^{n}_{i=1}(\hat{y}^{(i)}-y^{(i)})^2
\]
for all $0<= j <= m$:
\[
\theta_j := \theta_j - \alpha\frac{\partial}{\partial\theta_j}J(\theta)
\]
\end{huge}
\end{document}