# 1. installation
sudo apt install hydra

# 2. usage
- bruteforcing username and password

```sh
hydra -L user.txt -P pass.txt <ip address> ssh -t 4
```

-l: username during bruteforce attack
-L: username list for attack
-p: password for attack
-P: password list for attack
-t: set thread count

- bruteforcing passwords

```sh
hydra -l msfadmin -P pass.txt <ip address> ssh -t 4
```


- find valid username

```plain-text
hydra -L usernames.txt -p pass -s 8080 <ip address> http-post-form "/:username=^USER^&password^PASS^:Invalid username."
```




---
reference:
<https://www.geeksforgeeks.org/how-to-use-hydra-to-brute-force-ssh-connections/>