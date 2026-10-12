# 1. installation

```sh
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-compose-plugin
```


# 2. usage
- docker ps -a
can view the containers running

- docker compose stop
stop containers

- docker compose up
start containers using the yml file in the directory

- docker rm <container id> or docker rm $(sudo docker ps -aq)
remove selected container or all the containers


---
<https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository>