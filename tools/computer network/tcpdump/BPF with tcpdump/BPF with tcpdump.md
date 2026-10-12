## common usage
- tcpdump -r dirb.log 'tcp[((tcp[12:1] & 0xf0) >> 2) + 9:4] = 0x32303020'
http 200 OK replies

