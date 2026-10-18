Short answer: **it doesn’t actually only replace the first occurrence**.
What you are seeing is caused by the **regex pattern itself**, not by `re.sub`.

Let’s break this down precisely.

---

## Your code

```python
text = re.sub(r" (\(.*\))", r"\1", text)
```

---

## Why it *appears* to replace only one occurrence

### 1. `re.sub()` replaces **all matches by default**

Unless you pass `count=1`, `re.sub()` is global.

So this is **not** the issue.

---

### 2. The real problem: `.*` is **greedy**

Your pattern:

```regex
 (\(.*\))
```

Breakdown:

* Space: `" "`
* `\(` → literal `(`
* `.*` → **greedy match of everything**
* `\)` → last possible `)`

This means:

> “Match a space, then an opening parenthesis, then **as much as possible** until the **last closing parenthesis in the entire string**.”

As a result:

* The **first** `" ("` starts the match
* `.*` swallows **everything up to the final `)`**
* Only **one giant match** exists
* Therefore, only one replacement happens

---

## Example

### Input

```
hello (c123) world (c456) test (c789)
```

### What your regex matches

```
 (c123) world (c456) test (c789)
```

One match → one replacement.

---

## Correct pattern (non-greedy)

Use `*?` instead of `*`:

```python
text = re.sub(r" (\(.*?\))", r"\1", text)
```

Now:

* Each `" (cxxxx)"` is matched independently
* All occurrences are replaced

---

## Even better: be specific

If your content is always something like `(c12345)`:

```python
text = re.sub(r" \((c\d+)\)", r"(\1)", text)
```

or if you want to keep the parentheses:

```python
text = re.sub(r" \(\w+\)", lambda m: m.group(0)[1:], text)
```

---

## Key takeaway (important)

| Pattern    | Behavior                   |
| ---------- | -------------------------- |
| `.*`       | Greedy — eats everything   |
| `.*?`      | Non-greedy — minimal match |
| `re.sub()` | Global by default          |

Your regex **creates one giant match**, so there is only one substitution.

---

## Rule of thumb

> If a regex seems to “only match once”, look for a greedy quantifier crossing multiple intended matches.

If you want, I can:

* Draw a step-by-step matching diagram
* Show how the regex engine backtracks here
* Help you design a **safe, constrained regex** for your exact input format

Just say which.
