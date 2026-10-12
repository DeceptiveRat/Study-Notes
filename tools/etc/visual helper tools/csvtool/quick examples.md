- view column names

```sh
csvtool head 1 *.csv | awk -F, '{for(i=1;i<=NF;i++) print i ": " $i}'
```


- print certain columns in readable format

```sh
csvtool col 1,2,3,7 FILENAME | csvtool readable -
```


- print row containing pattern with column names

```sh
csvtool readable FILENAME | grep -e "PATTERN" -e "ANY_COLUMN_NAME"
```
