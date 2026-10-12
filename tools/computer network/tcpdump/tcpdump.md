## 1. options
- -X
display packets in hexadecimal and ascii

- -A
display ascii

- -D
view interfaces

- -i
chose interface

- -n
do not resolve host name

- -w/-r
write/read to/from file

- -t
remove time stamp

- -tt
change timestamp to Unix epoch time

- -ttt
change timestamp to time in ms since last packet

- -tttt
change timestamp to standard format

- -c
get number of packets to capture/return

- --count
get number of packets matched

## 2. filters
- host/src/dst [host name or address]
- /src/dst net [CIDR notation]
packets to and from subnet

- /src/dst port [port number]

## 3. common usage
- sudo tcpdump -tt -r example.pcap -n tcp | cut -d " " -f 3 | cut -d "." -f 1-4 | sort | uniq -c | sort -nr
view source ips sorted by frequency

