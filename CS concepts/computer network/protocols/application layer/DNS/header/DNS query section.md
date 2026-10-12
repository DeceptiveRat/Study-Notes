
| Name |
| --- |
| Type |
| Class |


## 1. Query name
- domain name
- variable length^(3)^

## 2. type
- DNS record type
- 2 bytes

| type | value | description |
| --- | --- | --- |
| A | 1 | request IP address, stored in the value tuple of the RR for name in the name string |
| NS | 2 | name is a domain and value is the authoritative server for that domain |
| CNAME | 5 | value is canonical hostname for alias hostname in name |
| MX | 15 | value is canonical name of a mail server with alias in name |
| PTR | 12 | request hostname for IP address |
| HINFO | 13 | information about host hardware |
(4)(5)

## 3. class
- protocol family (class)
- 2 bytes
- 1, IN: Internet


---
reference:
(1): <https://cabulous.medium.com/dns-message-how-to-read-query-and-response-message-cfebcb4fe817>
(2): <http://www.ktword.co.kr/test/view/view.php?no=2251>
(3): <https://www.uptimia.com/questions/what-is-the-maximum-length-of-a-dns-name-in-characters#:~:text=DNS%20names%20can%20be%20up,have%20up%20to%2061%20characters>[.](https://www.uptimia.com/questions/what-is-the-maximum-length-of-a-dns-name-in-characters#:~:text=DNS%20names%20can%20be%20up,have%20up%20to%2061%20characters.)
(4): Computer Networking: A Top-Down Approach
(5): <https://www.iana.org/assignments/dns-parameters/dns-parameters.xhtml#dns-parameters-8>