Perfect 👍 Let’s build a simple scenario where we can use **both a chi-square test and a t-test**, but for different questions.

---

## 📊 Example Dataset

Suppose we surveyed **20 students** about their study habits and exam scores.

* **Categorical data**: Did the student attend a study group? (Yes/No)
* **Numerical data**: Their exam score (0–100).

| Student | Study Group | Exam Score |
| ------- | ----------- | ---------- |
| 1       | Yes         | 88         |
| 2       | Yes         | 92         |
| 3       | No          | 70         |
| 4       | No          | 65         |
| 5       | Yes         | 85         |
| …       | …           | …          |

---

## 🔹 **Chi-Square Test (Categorical Question)**

**Question**: Is there an association between **study group attendance** (Yes/No) and **passing the exam** (Pass = score ≥ 75, Fail = score < 75)?

1. Convert scores into categories: Pass/Fail.

   * Example table (contingency table):

   |                | Pass | Fail | Total |
   | -------------- | ---- | ---- | ----- |
   | Study Group    | 8    | 2    | 10    |
   | No Study Group | 3    | 7    | 10    |
   | **Total**      | 11   | 9    | 20    |

2. Run a **chi-square test of independence**.

   * Null hypothesis ((H_0)): Study group attendance is independent of passing.
   * Alternative ((H_a)): They are associated.
   * If (p < 0.05), we conclude there **is** an association.

---

## 🔹 **t-Test (Numerical Question)**

**Question**: Do students who attended study groups have a higher **average exam score** than those who didn’t?

1. Group means:

   * Study group: mean ≈ 88
   * No study group: mean ≈ 70

2. Do a **two-sample t-test**.

   * Null hypothesis ((H_0)): Mean score (Study group) = Mean score (No study group).
   * Alternative ((H_a)): Mean score (Study group) ≠ Mean score (No study group).
   * If (p < 0.05), we conclude study groups **significantly improved average scores**.

---

## 🎯 Takeaway

* **Chi-square test** → Categorical outcome (Pass/Fail). Are two categorical variables related?
* **t-test** → Numerical outcome (Exam score). Do two groups differ in their means?

---

Do you want me to actually **run the calculations** for these tables (show the chi-square statistic and t-test result), so you can see the numbers worked out?
