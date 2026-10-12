Great question — this is the part that confuses almost everyone at first.
Here’s the simplest way to understand **how one field becomes two different searchable fields**, and **why that gives you two search behaviors**.

---

# 🎯 Short Answer

Because Elasticsearch **stores the same field in two different ways**:

* **`foo` (type: text)** → tokenized → used for *full-text search*
* **`foo.keyword` (type: keyword)** → stored as a single whole string → used for *exact match / aggregations*

So even though you only wrote one field into the document, Elasticsearch *internally creates two versions* of it.

---

# 🧠 Deep Explanation (Simple)

## 1. How Elasticsearch stores text

When storing text, Elasticsearch can store it in two fundamentally different ways:

### **A. Analyzed (tokenized) text → for full-text search**

Example: `"The Quick Brown Fox"`

After analysis (tokenization + lowercasing, etc), ES stores:

```
"the", "quick", "brown", "fox"
```

So searching `"fox"` will match.

This is how **`text`** fields work.

---

### **B. Not analyzed (kept as whole string) → for exact match**

ES stores the entire string as one unit:

```
"The Quick Brown Fox"
```

Searching `"fox"` will NOT match,
but an exact match for `"The Quick Brown Fox"` will.

This is how **`keyword`** fields work.

---

## 2. New default mapping = BOTH stored automatically

Given your example:

```json
"foo": {
  "type": "text",
  "fields": {
    "keyword": {
      "type": "keyword"
    }
  }
}
```

Elasticsearch **generates two fields** from the same data:

### Field #1: `foo`

* type: **text**
* tokenized into words
* searchable by parts of the text

### Field #2: `foo.keyword`

* type: **keyword**
* single whole string
* used for exact-match, sorting, aggregations

---

# 🔍 Example — Let's say the document has:

```json
{ "foo": "New York City" }
```

## Searching with `foo` (text)

Query:

```
search for "york"
```

Matches! Because `foo` was analyzed into tokens:

```
["new", "york", "city"]
```

## Searching with `foo.keyword` (keyword)

Query:

```
search for "york"
```

Does NOT match — because `"New York City"` is stored as one single token.

But:

```
search for "New York City"
```

Matches exactly.

---

# 📊 Why this gives 2 search types

### ✔️ Full-text search → use `foo`

* “find documents that mention *anything about* dogs”
* “search for this word/phrase inside the text”

### ✔️ Exact match → use `foo.keyword`

* “group by category”
* “count how many times the value appears”
* “sort alphabetically”
* “search for an exact full string”

---

# 🗂 Example query difference

### Full-text search:

```json
{
  "query": {
    "match": {
      "foo": "york"
    }
  }
}
```

### Exact search:

```json
{
  "query": {
    "term": {
      "foo.keyword": "New York City"
    }
  }
}
```

---

# 💡 Analogy

Imagine taking a sentence and storing it in two ways:

* **Version A**: Cut it into words (for word search)
* **Version B**: Save the whole sentence (for exact lookup)

ES just does this *automatically* now.

---

# If you want, I can also show:

* How Kibana displays `.keyword` fields
* What happens if you ONLY want keyword or ONLY text
* How this affects speed / memory
* How to define custom analyzers

Just tell me!
