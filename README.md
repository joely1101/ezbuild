```
usage: 
1.setup host(recommand ubuntu 20.02)
1.1 install docker on your ubuntu/linux(from https://docs.docker.com/engine/install/ubuntu/)
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin

1.2 login docker registry(any server in config)
docker login docker.registry.yours.
  if insecure-registries used, please modify docker config file
  #vi /etc/docker/daemon.json
    {
        "insecure-registries": ["192.168.1.100:9000"]
    }
     

1.3 install bash-complete
apt-get install bash-completion

2.clone this repo to user local file(do not run as root user)
git clone this_project_path/ezbuild.git ~/.local/ezbuild

3.do link ezbuild in ~/.local/bin (note, CAN NOT USE COPY, MUST symbolic link)
ln -sf ~/.local/ezbuild/ezbuild ~/.local/bin/ezbuild

4.add bash completion for ezbuild
sudo ln -sf ~/.local/ezbuild/ezbuild.bash_complete /etc/bash_completion.d/ezbuild.bash_complete

4.logout bash and login again for take step2,3 effect.
5.If new project supported on git, just do 'ezbuild update'

Usage:
   ezbuild update [ project] - updte build env list or update project's docker image
   ezbuild ls    - list all supported project name
   ezbuild login project-name -  login project's building OS
   ezbuild del project-name - delete docker instance of this project.

Note: 
1.if you want docker to emulate other cpu(arm64/mips...), please enable qemu static
sudo apt-get install -y qemu-user-static
docker run --rm --privileged multiarch/qemu-user-static --reset -p yes


```
```
Example to use openwrt
user~$ mkdir workdir
user~$ cd workdir/
user~$ ezbuild login openwrt
user@openwrt-dev-user:~/workdir$

```