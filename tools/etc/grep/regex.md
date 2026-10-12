1. bracket expression
- list of characters enclosed by [ ]
- matches any single character in that list
- if first character is ^, matches character not in list

```sh
grep [0123456789]
grep [0-9]
grep [a-zA-Z]
```

- [:alnum]: character class of numbers and letters

2. anchoring
- ^: match empty string at beginning of line
- $: match empty string at end of line

3. backslash character and special expressions
- \<: empty string at beginning of word
- \>: empty string at end of word

4. repetition
- ?: matched at most once
- *: matched 0 or more 
- +: matched 1 or more
- {n}: exactly n times
- {n,}: n or more 
- {,m}: at most m times; GNU extension
- {n,m}: at least n, not more than m times