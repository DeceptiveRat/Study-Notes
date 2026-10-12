# 1. installation
sudo pip install sshuttle

# 2. usage
- use sshuttle to connect to the new domain
sshuttle -r root@10.10.155.5 10.10.10.0/24 --ssh-cmd “ssh -i pivot”

run root user at 10.10.155.5
through that root user connect to the new network of 10.10.10.0/24
run ssh command with identity file pivot

-  as long as sshuttle is open and running we can communicate with that network