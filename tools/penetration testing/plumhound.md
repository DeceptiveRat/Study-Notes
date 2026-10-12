# 1. installation
- clone the gitjhub directory into a directory
- sudo pip3 install -r requirements.txt

# 2. usage
- bloodhound must be up to use plumhound
- for a quick query of the domain
sudo python3 PlumHound.py --easy -p <password>

- to run a default task
sudo python3 PlumHound.py -x tasks/default.tasks -p <password>

---
reference:
(1) tcm-sec: [Domain Enumeration with Plumhound](<elastic stack.md>)