1. strip ANSI escape codes (from linpeas output, etc)

```plain-text
awk '{gsub(/\x1B\[[0-9;]*[mK]/, "")}1' peas.out > clean.txt
```


2. remove from front and back

```sh
# \t ![[DCO demo.png]] >> DCO demo.png
awk '{sub(/^\s*!\[\[/, ""); sub(/\]\]$/, ""); print}'
```


3. remove between angle brackets

```sh
# <Value Protected="True">Z7iQcL9ebSk=</Value> >> Z7iQcL9ebSk=
awk '{gsub(/\s*<[^>]+>/, ""); print}'
```


4. separate by comma and postfix number

```sh
# 1,2,3 =>
# 1: 1
# 2: 2
# 3: 3
awk -F, '{for(i=1;i<=NF;i++) print i ": " $i}'
```


5. get only files



```sh
# GET https://fras.sdfasdf/409ba913-0a20ddf33b0bbc7b.js 2 => 409ba913-0a20ddf33b0bbc7b.js
awk -F'/' '{print $NF}' coupang_gets_files.txt | awk '{print $1}'
```
