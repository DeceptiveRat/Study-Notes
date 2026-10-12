A good commit message gives **just enough context** so future-you (or teammates) can understand *why* the change happened, without drowning in low-value details like “renamed variable X to Y.”

Here’s a clean, practical rule set used by most professional developers:

---

# ✅ **What goes in a good commit message**

## **1. A short, meaningful title (50–72 chars)**

Describe the *purpose* of the change, not the low-level edits.

**Good:**

* `Fix crash when BLE sensor disconnects`
* `Add timeout logic to HTTP request handler`
* `Refactor packet parser for clarity and testability`
* `Improve login error messages`

**Bad:**

* `Change some stuff`
* `Update code`
* `Fix bug`
* `Rename variable` ← too low-level

---

## **2. (Optional) A body that explains *why*, not “what”**

Only add a body if the reason isn’t obvious.

**Useful body example:**

```
The interceptor thread sometimes blocked forever because recv()
never timed out. Added a 5-second timeout so the system can cleanly
recover when no packets arrive.
```

This answers:
**Why was this needed?
What problem does it solve?**

You *don’t* need:

* Every function you touched
* Every line you changed
* A detailed change log inside the commit message
* A repeat of the diff

Git already tracks all that.

---

# ❗️ So… how detailed should I be?

Use this rule:

> **Be detailed about intention and motivation.**
> **Be brief about implementation details.**

Examples:

### Too low-level:

* “Changed function name foo() → bar(), added two ifs, removed variable tmp.”

### Too vague:

* “Fix bug.”

### Balanced:

* “Fix incorrect checksum calculation in UDP packet builder”

And if needed:

```
The old implementation used host byte order instead of network byte order.
```

---

# 🧠 **The real goal of commit messages**

They are to help someone reading history answer:

1. **What was the purpose of this change?**
2. **Why was it needed?**
3. **Is this commit the cause of the bug I’m debugging today?**

That’s it.

You don’t need to “keep track of everything.” Git does that.

---

# ⭐ Practical workflow (zero overhead)

Here is a lightweight habit professionals use:

1. After coding, ask yourself:
   **“If someone saw this commit in 6 months, would they know what problem I solved?”**

2. Write a 1-line title like:
   **“Add retry logic to ESP32 WiFi connection”**

3. If the “why” would confuse someone in the future, write 1–3 sentences explaining it.

Done.

---

If you want, I can show you:

* Good examples of commit messages for *your code style*
* A commit message template you can paste into `.gitconfig`
* How to squash messy commits into clean ones

Just tell me!
