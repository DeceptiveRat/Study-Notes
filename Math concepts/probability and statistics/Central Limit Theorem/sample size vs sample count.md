Good question — you’re asking about the **number of samples** (what we called `num_samples` in the code).

Let’s separate **sample size** vs **sample count**, since they do different things:

---

### 🔹 Sample Size ((n))

* How many observations are inside *one* sample.
* Controls how “normal-looking” the **distribution of sample means** will be.
* Larger (n) → sample means are more tightly clustered (smaller variance) and closer to a normal curve.

---

### 🔹 Sample Count (e.g., 1,000, 10,000 samples)

* How many times you repeat the sampling process.
* Controls how well you can **visualize** the Central Limit Theorem.
* More samples = smoother histogram (less noisy).
* But it doesn’t change the underlying distribution itself—it just gives you a better picture of it.

---

### Example

* **Sample size = 30, sample count = 10**
  - you only get 10 averages, histogram will be blocky.

* **Sample size = 30, sample count = 1,000**
  - you get a much smoother bell curve.

* **Sample size = 100, sample count = 1,000**
  - now it’s both smooth *and* very close to a perfect normal distribution.

---

👉 In short:

* **Sample size** affects the *shape* of the sampling distribution.
* **Sample count** affects how *clear/smooth* the histogram looks.

---

Do you want me to give you code that **compares low vs high sample count side by side** so you can see the difference visually?
