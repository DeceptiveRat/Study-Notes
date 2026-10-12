1. regex functions
- findall
   - returns a list containing all matches
- search 
   - returns a match object if there is a match anywhere in the string
- split
   - returns a list where the string has been split at each match
- sub
   - replaces one or many matches with a string

2. metacharacters
- []
   - a set of characters
   - e.g. [a-m]
- \ 
   - signals a special sequence
   - e.g. \d
- .
   - any character (except newline)
   - e.g. he..o
- ^
   - starts with
   - e.g. ^hello
- $
   - ends with
   - e.g. planet$
- *
   - zero or more occurrences
   - e.g. hel*o
- +
   - one or more occurrences
   - e.g. hel+o
- ?
   - zero or one occurrences
   - e.g. he.?o
- {}
   - exactly the specified number of occurrences
   - e.g. he.{2}o
- |
   - either or
   - e.g. falls|stays
- ()
   - capture and group

3. flags
- re.ASCII
   - re.A
   - returns only ascii matches
- re.DEBUG
   - returns debug information
- re.DOTALL
   - re.S
   - makes the . character match all characters including newline characters
- re.IGNORECASE
   - re.I
   - case-insensitive matching
- re.MULTILINE
   - re.M
   - returns only matches at beginning of each line
- re.NOFLAG
   - no flag is set
- re.UNICODE
   - re.U
   - returns unicode match
   - default from python3
- re.VERBOSE
   - re.X
   - allows whitespaces and comments inside patterns

4. special sequences
- \A
   - returns match if specified characters are at the beginning of the string
   - e.g. \AThe
- \b
   - returns a match where the specified characters are at the beginning or at the end of a word
   - e.g. \bain
   - e.g. ain\b
   - negated: \B
- \d
   - returns a match where the string contains digits
   - negated: \D
- \s
   - returns a match where the string contains a white space character
   - negated: \S
- \w
   - returns a match where the string contains any word characters (a~Z, 0~9, _)
   - negated: \W
- \Z
   - returns a match if the specified characters are at the end of the string
   - e.g. Spain\Z

5. sets
- [arn]
   - returns a match where one of the specified(a, r, n) characters are present
- [a-n]
   - returns a match for any character between a and n
- [^arn]
   - returns a match for any characters except a, r, and n
- [0123]
   - returns a match where any of the specified digits(0, 1, 2, 3) are present
- [0-9]
   - returns a match for any digit between 0 and 9
- [0-5][0-9]
   - returns a match for any two-digit numbers from 00 to 59
- [a-zA-Z]
   - returns a match for any character between a and Z
- [+]
   - returns a match for any + character in the string

reference:
<https://www.w3schools.com/python/python_regex.asp>