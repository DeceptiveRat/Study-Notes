1. file existence check
- -e for file, directory, symlink, etc

```sh
if [ -e "filename" ]; then
    echo "File exists"
else
    echo "File does not exist"
fi
```

- -f for file only

```sh
if [ -f "filename" ]; then
    echo "Regular file exists"
fi
```
