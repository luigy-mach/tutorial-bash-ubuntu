# tutorial-docker

#### Dependencias
```console
foo@bar:~$ sudo apt-get install curl
```
## Instalacion

#### Eliminar versiones anteriores 
```console
foo@bar:~$ sudo apt-get remove docker docker-engine docker.io
```
#### `docker-ce` install  on `ubuntu16.04`
```console
foo@bar:~$ sudo apt-get update
foo@bar:~$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
foo@bar:~$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
foo@bar:~$ sudo apt-key fingerprint 0EBFCD88
foo@bar:~$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
foo@bar:~$ sudo apt-get update
foo@bar:~$ sudo apt-get install docker-ce
```
#### Test - docker
```console
foo@bar:~$ sudo docker run hello-world
```
#### Instalar nvidia-docker


###### Dependencias
- tener instalado los driver y `cuda-8`  

```console
foo@bar:~$ sudo docker volume ls -q -f driver=nvidia-docker | xargs -r -I{} -n1 docker ps -q -a -f volume={} | xargs -r docker rm -f
foo@bar:~$ sudo apt-get purge -y nvidia-docker

foo@bar:~$ curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
foo@bar:~$ curl -s -L https://nvidia.github.io/nvidia-docker/ubuntu16.04/amd64/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
foo@bar:~$ sudo apt-get update

foo@bar:~$ sudo apt-get install -y nvidia-docker
foo@bar:~$ sudo pkill -SIGHUP dockerd
```


# Ref: 
> https://pjreddie.com/darknet/yolo/
> https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-docker-ce-1
> https://github.com/NVIDIA/nvidia-docker
> https://hub.docker.com/r/luigymach/yolo-ubuntu-xfce-vnc/


