1. Dot (.)
- matches any single character besides end of line

2. Start of line (^)
- matches start of line

3. End of line ($)
- matches end of line

4. match character set
- matches one out of several characters in bracket
- awk '/[CT]all/' => "Call" or "Tall"

5. exclusive set
- matches one out of several characters not in bracket
- awk '/[^CT]all/' => "Ball", "Gall", ...

6. alteration
- regular expressions can be logically ORed
- awk '/Call|Ball/' => "Call" or "Ball"

7. zero or one occurrence
- awk '/Colou?r/' => "Color" or "Colour"

8. zero or more occurrence
- awk '/cat*/' => "ca", "cats2", ...

9. one or more occurrence
- awk '/cat+/' => "cat", "cat231", ...

10. grouping
- awk '/Apple (Juice|Cake)/' => "Apple Juice" or "Apple Cake"