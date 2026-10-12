# Deriving the dual SVM problem

Start from the primal Lagrangian (what you already have):

$$
L(w,b,\alpha)=\frac{1}{2}\|w\|^2-\sum_{i=1}^N \alpha_i\big(y_i(w^\top x_i + b)-1\big),
\qquad \alpha_i \ge 0.
$$

**Step 1 — stationarity conditions (set partial derivatives to zero).**

1. Derivative w.r.t. $w$:

$$
\frac{\partial L}{\partial w}=w - \sum_{i=1}^N \alpha_i y_i x_i = 0
\quad\Longrightarrow\quad
w = \sum_{i=1}^N \alpha_i y_i x_i.
$$

2. Derivative w.r.t. $b$:

$$
\frac{\partial L}{\partial b} = -\sum_{i=1}^N \alpha_i y_i = 0
\quad\Longrightarrow\quad
\sum_{i=1}^N \alpha_i y_i = 0.
$$

(These are necessary optimality conditions for the saddle point.)

**Step 2 — substitute $w$ back into $L$ to eliminate primal variables.**

Compute the pieces:

* $\tfrac{1}{2}\|w\|^2 = \tfrac{1}{2}\big(\sum_i \alpha_i y_i x_i\big)^\top \big(\sum_j \alpha_j y_j x_j\big) = \tfrac{1}{2}\sum_{i=1}^N\sum_{j=1}^N \alpha_i \alpha_j y_i y_j \, x_i^\top x_j.$

* The term $\sum_i \alpha_i y_i w^\top x_i$:

$$
\sum_{i}\alpha_i y_i (w^\top x_i)
= \sum_i \alpha_i y_i \Big(\sum_j \alpha_j y_j x_j\Big)^\top x_i
= \sum_{i}\sum_{j}\alpha_i\alpha_j y_i y_j \, x_j^\top x_i
$$

(which is the same double sum as above).

Now substitute into $L$:

$$
\begin{aligned}
L &= \frac{1}{2}\sum_{i,j}\alpha_i\alpha_j y_i y_j x_i^\top x_j
\;-\;\sum_i \alpha_i\big(y_i(w^\top x_i + b)-1\big)\\[4pt]
  &= \frac{1}{2}\sum_{i,j}\alpha_i\alpha_j y_i y_j x_i^\top x_j
  \;-\;\sum_i \alpha_i y_i w^\top x_i \;-\; b\sum_i \alpha_i y_i \;+\; \sum_i \alpha_i\\[4pt]
  &= \frac{1}{2}\sum_{i,j}\alpha_i\alpha_j y_i y_j x_i^\top x_j
  \;-\;\sum_{i,j}\alpha_i\alpha_j y_i y_j x_i^\top x_j
  \;-\; b\sum_i \alpha_i y_i \;+\; \sum_i \alpha_i\\[4pt]
  &= -\tfrac{1}{2}\sum_{i,j}\alpha_i\alpha_j y_i y_j x_i^\top x_j
  \;-\; b\sum_i \alpha_i y_i \;+\; \sum_i \alpha_i.
\end{aligned}
$$

Use the stationarity condition $\sum_i \alpha_i y_i = 0$ to drop the $b$ term. So the Lagrangian (after eliminating $w,b$) becomes the dual objective function:

$$
L(\alpha) = \sum_{i=1}^N \alpha_i 
\;-\; \tfrac{1}{2}\sum_{i=1}^N\sum_{j=1}^N \alpha_i\alpha_j y_i y_j \, x_i^\top x_j.
$$

**Step 3 — form the dual optimization problem.**

We maximize $L(\alpha)$ w.r.t. $\alpha$ (because the primal is minimize over primal vars and Lagrange multipliers form a max-min saddle), subject to the constraints coming from KKT/stationarity:

$$
\begin{aligned}
&\maximize_{\alpha}\quad && \sum_{i=1}^N \alpha_i - \tfrac{1}{2}\sum_{i=1}^N\sum_{j=1}^N \alpha_i\alpha_j y_i y_j \, x_i^\top x_j,\\[4pt]
&\text{subject to}\quad && \sum_{i=1}^N \alpha_i y_i = 0,\\
&&& \alpha_i \ge 0,\quad i=1,\dots,N.
\end{aligned}
$$

That is the standard SVM dual (hard-margin). This is a concave quadratic program in $\alpha$.

**Extra useful facts**

* Recover $w$ from $\alpha$:

$$
w = \sum_{i=1}^N \alpha_i y_i x_i.
$$

* The bias $b$ can be found using any support vector $x_k$ with $0 < \alpha_k$ (KKT complementary slackness):

$$
y_k (w^\top x_k + b) = 1 \quad\Longrightarrow\quad
b = y_k - \sum_{j=1}^N \alpha_j y_j x_j^\top x_k.
$$

* If you add slack variables (soft-margin) with penalty $C$, the only change in the dual is the box constraint $0 \le \alpha_i \le C$ instead of $\alpha_i \ge 0$.

---

If you want, I can now show a short worked example with 2–3 points and compute the dual objective matrix and solution numerically. Want that?
