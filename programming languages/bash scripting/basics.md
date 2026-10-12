1. passing arguments:
- arguments appear as $1, $2, etc
- count of arguments: $#

2. printf
- syntax

```sh
printf FORMAT [ARGUMENT]
```

e.g. printf "Hello, %s!\n" "world"

3. if else
- syntax

```sh
# If...else statement
num=8
if [ $num -gt 10 ]; then
  echo "Number is greater than 10"
else
  echo "Number is 10 or less"
fi
```


4. parameter expansion
- #: delete shortest match from front

```sh
${var#pattern}
```

- ##: delete longest match from front
- %: delete shortest match from back
- %%: delete longest match from back
- /: replace first instance

```sh
${var/pattern/newvar}
```

- //: replace all instances

5. logical operators
- ||: or

reference:
- [w3schools]"Bash If...Else", <https://www.w3schools.com/bash/bash_conditions.php>, Jan 27 2026