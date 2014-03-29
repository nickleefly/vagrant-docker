# Vagrant Docker ssh

ssh into docker

# Usage

* run `vagrant up`, then `vagrant ssh` into virtual machine
* install docker
* `cd docker` build image with `sudo docker build -t eg_sshd .`
* run container with `sudo docker run -d -P --name test_sshd eg_sshd`
* check with `sudo docker port test_sshd 22` to see container's port 22 is mapped to
* let's say its `0.0.0.0:49153`
* ssh root@127.0.0.1 -9 49153

## run docker without `sudo`

[check official link](http://docs.docker.io/en/latest/installation/ubuntulinux/#giving-non-root-access)
