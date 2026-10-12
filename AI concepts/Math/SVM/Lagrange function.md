Great question — you’re basically asking how we go from the **primal SVM optimization problem** (first picture) to its **Lagrangian form** (second picture). Let’s break it down step by step.

---

### 1. Primal Problem (first picture)

We want to solve:

$$
\min_{w,b} \quad \frac{1}{2}\|w\|^2
$$

subject to the constraints:

$$
y_i(w^T x_i + b) \geq 1, \quad \forall i
$$

* **Objective**: minimize $\tfrac{1}{2}\|w\|^2$ → maximize the margin.
* **Constraints**: all training samples are correctly classified with a margin of at least 1.

---

### 2. Method of Lagrange Multipliers

To solve a constrained optimization problem, we introduce **Lagrange multipliers** $\alpha_i \geq 0$ for each constraint.

General form for inequality constraints $g_i(x) \geq 0$ is:

$$
L(x, \alpha) = f(x) - \sum_i \alpha_i g_i(x), \quad \alpha_i \geq 0
$$

---

### 3. Apply to Our Case

Our constraint is:

$$
y_i (w^T x_i + b) - 1 \geq 0
$$

So, $g_i(w, b) = y_i(w^T x_i + b) - 1$.

Plugging into the Lagrangian:

$$
L(w, b, \alpha) = \frac{1}{2}\|w\|^2 - \sum_{i=1}^N \alpha_i \big( y_i (w^T x_i + b) - 1 \big)
$$

---

### 4. That’s Exactly the Second Picture

So the second picture is simply the **Lagrangian formulation** of the primal optimization problem in the first picture.

* $\tfrac{1}{2}\|w\|^2$ → original objective.
* $- \sum_i \alpha_i \big(y_i(w^T x_i + b) - 1\big)$ → penalty for violating constraints, weighted by Lagrange multipliers $\alpha_i \geq 0$.

---

✅ So the step from **first picture → second picture** is:
Take the original optimization problem with inequality constraints, and form the **Lagrangian function** by introducing Lagrange multipliers for each constraint.

---

Would you like me to also show you how we **derive the dual problem** from this Lagrangian? That’s the next key step in SVM optimization.
