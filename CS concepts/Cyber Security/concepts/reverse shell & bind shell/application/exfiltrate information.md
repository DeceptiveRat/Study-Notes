## 1. description
malicious file downloads uploader program from C&C server. Uploader program extracts sensitive information, i.e. /etc/passwd, and sends it to the C&C server

## 2. overview
(1) malicious file is opened on victim
(2) downloads uploader from C&C server
(3) uploader is run by malicious file
(4) uploader exfiltrates sensitive information to C&C server

## 3. notes
- use obfuscation to evade detection => try uploading to virus total
- make downloader look innocent