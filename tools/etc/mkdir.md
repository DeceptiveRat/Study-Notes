### • create directory
### • with {} to create multiple nested directories

```sh
mkdir -p {a,b}/{x,,y,z}
```

>	a
	> x
	> y
	> z
> b
	> x
	> y
	> z

