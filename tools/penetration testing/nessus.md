---
<https://www.tenable.com/products/nessus>
---

# 1. Installation
- download the tenable nessus package file
- dpkg -i Nessus<version>-debian6_amd64.deb

# 2. Start
- start the nessus scanner with /bin/systemctl start nessusd.service
- go to <https://127.0.0.1:8834/#/>

# 3. Stop
- /bin/systemctl stop nessusd.service