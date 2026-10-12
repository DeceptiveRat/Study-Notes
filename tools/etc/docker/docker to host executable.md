1. build image with dockerfile

```python
sudo docker buildx build .
```

2. start docker

```sh
sudo docker run -it -u 0 -p 12345:12345 -v $(pwd):/mnt 008aeef0d5c9 /bin/bash
```

-it: interactive
-u: as user
-p: map port
-v: mount directory
- /bin/bash: start /bin/bash

3. start executable

```sh
socat TCP-LISTEN:12345,reuseaddr,fork EXEC:./binary
```


4. executable listening at at 0.0.0.0:12345