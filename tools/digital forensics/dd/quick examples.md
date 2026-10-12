- skipping bytes efficiently

```sh
dd iflag=skip_bytes,fullblock skip=108584 count=2 bs=512 of=seg_seqnum1_1.dat
```

- start writing at byte X

```sh
dd if=IF of=OF oflag=seek_bytes iflag=count_bytes bs=512 seek=X count=Y conv=notrunc
```
