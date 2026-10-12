## etc
- decode blob
``` sh 
sqlite3 "61211127-babe-441f-9842-9636ffd894af.db" "SELECT hex(data) FROM gen_metadata WHERE data IS NOT NULL LIMIT 1;" | xxd -r -p | protoc --decode_raw
```