The authoritative source for this behavior is the **Official YARA Documentation**, specifically within the **Writing YARA rules** module. 

There are two specific rules in the documentation that combine to create the exact trap you fell into:

### 1. How the `wide` modifier actually works
Under the subsection *Wide-character strings*, the developers explicitly warn users about the limitations of the modifier. It does not parse memory as true Unicode; it performs a mechanical byte insertion:
> *"However, keep in mind that this modifier **just interleaves the ASCII codes of the characters in the string with zeroes**, it does not support truly UTF-16 strings containing non-English characters."*
> — [YARA Documentation: Wide-character strings](https://yara.readthedocs.io/en/stable/writingrules.html#wide-character-strings)

### 2. Applying `wide` to Regular Expressions
Under the subsection *Regular expressions*, the documentation confirms that this exact same "dumb" interleaving mechanic is blindly applied to regex syntax:
> *"As with text strings, regular expressions can be followed by the `nocase`, `ascii`, `wide`, and `fullword` modifiers. **The semantics of these modifiers are exactly the same as for text strings**."*
> — [YARA Documentation: Regular expressions](https://yara.readthedocs.io/en/stable/writingrules.html#regular-expressions)

---

### What this means for your compiled rule
Because the semantics are "exactly the same," YARA does not evaluate your regex against a dynamically decoded UTF-16 memory space. Instead, it takes your regex syntax and physically injects literal `\x00` requirements into the evaluation tree.

When you write the character class `[^b]` and append the `wide` modifier, YARA takes your logic (`not 0x62`) and **interleaves a zero**. 

The compiled machine instruction literally becomes a two-byte check:
1. **Evaluate the class:** Is the current byte not `0x62`?
2. **Evaluate the interleaved zero:** Is the very next byte `0x00`?

When YARA bumped into the `00 88` bytes right before your block of 'b's in the hex dump, Step 1 passed (`00` is not `62`), but Step 2 immediately failed (`88` is not `00`), crashing the match before it even started.