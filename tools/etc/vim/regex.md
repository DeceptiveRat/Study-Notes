Here's a **Vim regex cheatsheet for `:s` (substitute) command**, tailored to help you understand the syntax and key patterns:

---

### 📝 **Basic Syntax**

```vim
:s/pattern/replacement/flags
```

* Replace `pattern` with `replacement` on the current line.
* Add `g` to replace all matches in the line.
* Add `%` (`:%s/.../.../`) to apply to the whole file.

---

### 🔤 **Special Characters**

| Pattern   | Meaning                             |
| --------- | ----------------------------------- |
| `.`       | Any single character except newline |
| `\.`      | A literal dot                       |
| `*`       | Zero or more of the previous atom   |
| `\+`      | One or more (Vim-specific)          |
| `\=`      | Zero or one                         |
| `\{n,m}`  | Between n and m times               |
| `^`       | Start of line                       |
| `$`       | End of line                         |
| `\|`      | Alternation (OR)                    |
| `\(` `\)` | Grouping                            |

---

### 🔠 **Character Classes**

| Pattern  | Matches                       |
| -------- | ----------------------------- |
| `[abc]`  | a, b, or c                    |
| `[^abc]` | Not a, b, or c                |
| `\d`     | Digit (0-9)                   |
| `\D`     | Non-digit                     |
| `\w`     | Word character \[0-9A-Za-z\_] |
| `\W`     | Non-word character            |
| `\s`     | Whitespace                    |
| `\S`     | Non-whitespace                |

> In **Vim**, `\s` matches spaces, tabs, line breaks, etc.

---

### 🔁 **Examples**

```vim
:%s/\s\+/-/g          " Replace all whitespace sequences with a dash
:%s/\(\w\+\)\s\+/\1_/g " Replace whitespace after a word with underscore
:%s/^\s\+//g           " Remove leading whitespace
:%s/\s\+$//g           " Remove trailing whitespace
```

---

### ⚙️ **Flags**

| Flag | Description                   |
| ---- | ----------------------------- |
| `g`  | Global (all matches on line)  |
| `c`  | Confirm each substitution     |
| `i`  | Ignore case                   |
| `I`  | No ignore case                |
| `n`  | Report number of matches only |

---

Would you like a downloadable version or one you can paste in your `.vimrc` or notes?
