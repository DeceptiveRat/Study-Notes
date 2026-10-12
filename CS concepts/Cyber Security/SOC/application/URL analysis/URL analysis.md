## 1. URL anatomy
1.1. normal URL
![unnamed_48608b1712b241ff832259589a6064e8](unnamed_48608b1712b241ff832259589a6064e8.png)
- domain + TLD can't be spoofed

1.2. suspicious URL
*always defang malicious URLs*
![unnamed_08881c5d21004d118684502b72f2a9c1](unnamed_08881c5d21004d118684502b72f2a9c1.png)
- use of http, not https
- actual domain is dnsdyn, not apple
- strange path name
- personal email as parameter

![unnamed_4fef4b55323c4bcbb53c7feba1348ac7](unnamed_4fef4b55323c4bcbb53c7feba1348ac7.png)
- typo squatting

2. URL analysis tools
- <https://defa.ng/>
   - defang malicious URLs
- <https://unshorten.net/>
   - unshorten URLs
- cyberchef
   - decode URLs
- email IOC extractor

reference:
- TCM-security SOC101: <https://youtu.be/56NDgBOSpUg?feature=shared>