- pass commands through stdin

```sh
echo "cc(pid=668);dis(0x13fe695)" | python vol.py -f stuxnet.vmem volshell
```


- view currently available layers

```sh
(layer_name) >>> list(self.context.layers)
['memory_layer', 'layer_name']
```


- display bytes in different layer

```sh
(layer_name) >>> db(0x2866247, count=128, layer_name="memory_layer")
0x2866247    68 49 4e 49 54 4b 44 42 47 e0 39 00 00 00 30 1d    hINITKDBG.9...0.
0x2866257    00 00 3a 00 00 00 1c 1d 00 00 00 00 00 00 00 00    ..:.............
0x2866267    00 00 00 00 00 20 00 00 68 50 4f 4f 4c 4d 49 00    ........hPOOLMI.
0x2866277    00 07 13 00 00 00 70 1d 00 00 14 00 00 00 56 1d    ......p.......V.
0x2866287    00 00 00 00 00 00 00 00 00 00 00 00 00 20 00 00    ................
0x2866297    68 50 4f 4f 4c 43 4f 44 45 61 2f 00 00 00 90 1d    hPOOLCODEa/.....
0x28662a7    00 00 30 00 00 00 6a 1d 00 00 00 00 00 00 00 00    ..0...j.........
0x28662b7    00 00 00 00 00 20 00 00 68 41 4c 4d 4f 53 54 52    ........hALMOSTR
```


- get PEB object using address

```python3
peb = self.context.object(self.current_symbol_table + "!_PEB", layer_name = self.current_layer, offset = peb_address)
```
