### • create hexdumps of files
### • use -p to create hex stream

```sh
$ xxd -p test.bin
48b86f6f6f6f6e6700005048b8655f69735f6c6f6f5048b8666c61675f6e
616d504889e7be00000000ba00000000b8020000000f054889c74883c418
b8000000004889e6ba400000000f05b801000000bf010000000f05b83c00
00004831ff0f05
```

- write hex strings to binary

```sh
echo "DEADBEEF" | xxd -r -p > output.bin
```
