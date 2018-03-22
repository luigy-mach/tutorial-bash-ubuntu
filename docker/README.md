# tutorial-docker

#### Dependencias
```
sudo apt-get install curl
```
## Instalacion

###### (link de referencia) 
> https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-docker-ce-1

#### Eliminar versiones anteriores 
```
$ sudo apt-get remove docker docker-engine docker.io
```

#ubuntu16.04
$ sudo apt-get update
$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common

$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$ sudo apt-key fingerprint 0EBFCD88
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

#docker-ce install
$ sudo apt-get update
$ sudo apt-get install docker-ce
$ sudo docker run hello-world



#instalar nvidia-docker
	#para poder usar nvidia-docker se debe tener instalado los driver y cuda (lo he probado con cuda8)
	##(link de referencia) https://github.com/NVIDIA/nvidia-docker
	
	$ sudo docker volume ls -q -f driver=nvidia-docker | xargs -r -I{} -n1 docker ps -q -a -f volume={} | xargs -r docker rm -f
	$ sudo apt-get purge -y nvidia-docker

	$ curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
	$ curl -s -L https://nvidia.github.io/nvidia-docker/ubuntu16.04/amd64/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
	$ sudo apt-get update

	$ sudo apt-get install -y nvidia-docker
	$ sudo pkill -SIGHUP dockerd



#abrir imagen (teniendo el .rar descargado)
	##dockerhub (https://hub.docker.com/r/luigymach/yolo-ubuntu-xfce-vnc/)
	##en caso no tener el ".rar" ejecutar: (sudo docker pull luigymach/yolo-ubuntu-xfce-vnc:2.1.0)
	

$ sudo docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE

$ sudo docker load < imagen-luigy-yolo.tar
788ce2310e2f: Loading layer [==================================================>]  126.8MB/126.8MB
aa4e47c45116: Loading layer [==================================================>]  15.87kB/15.87kB
b3968bc26fbd: Loading layer [==================================================>]  14.85kB/14.85kB
c9748fbf541d: Loading layer [==================================================>]  5.632kB/5.632kB
2f5b0990636a: Loading layer [==================================================>]  3.072kB/3.072kB
8e592be0285e: Loading layer [==================================================>]  31.23kB/31.23kB
7625726d5ef9: Loading layer [==================================================>]  660.6MB/660.6MB
5304fd20ce03: Loading layer [==================================================>]  3.072kB/3.072kB
cc7d35c6b08d: Loading layer [==================================================>]  3.584kB/3.584kB
e1209d0c5f01: Loading layer [==================================================>]  218.5MB/218.5MB
a3ffa98302ae: Loading layer [==================================================>]  1.536kB/1.536kB
9cf053de1c68: Loading layer [==================================================>]  7.168kB/7.168kB
b404f4b472b1: Loading layer [==================================================>]  8.192kB/8.192kB
03f7d890ae32: Loading layer [==================================================>]  13.31kB/13.31kB
330b071e4915: Loading layer [==================================================>]  165.8MB/165.8MB
526160fab39d: Loading layer [==================================================>]  21.35MB/21.35MB
3e279e1b991b: Loading layer [==================================================>]  2.115MB/2.115MB
13d32abb55a7: Loading layer [==================================================>]  102.7MB/102.7MB
0995a3586310: Loading layer [==================================================>]  555.4MB/555.4MB
bfc3fd6d73ac: Loading layer [==================================================>]  228.6MB/228.6MB
045af7a918ca: Loading layer [==================================================>]    361kB/361kB
a9540032f318: Loading layer [==================================================>]  9.335MB/9.335MB
b1999436e376: Loading layer [==================================================>]  7.168kB/7.168kB
92d84d149b8d: Loading layer [==================================================>]  2.494MB/2.494MB
d32c6686fb45: Loading layer [==================================================>]  2.553GB/2.553GB
f109b17b2b24: Loading layer [==================================================>]   4.03GB/4.03GB
d309e6165b94: Loading layer [==================================================>]  35.78MB/35.78MB
f6a6cf23328e: Loading layer [==================================================>]   10.8MB/10.8MB
be2d424e3cc4: Loading layer [==================================================>]  39.66MB/39.66MB
Loaded image: luigymach/yolo-ubuntu-xfce-vnc:2.1.0


$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
REPOSITORY                       TAG                 IMAGE ID            CREATED             SIZE
luigymach/yolo-ubuntu-xfce-vnc   2.1.0               0b8381ae1f95        7 weeks ago         8.67GB




#clonando proyecto!
	$ git clone https://github.com/luigy-mach/darknet.git ~/yolo/darknet
	$ cd ~/yolo/darknet
	##descargando pesos
	wget <file.ext> -P ~/yolo/darknet
	$ wget https://pjreddie.com/media/files/yolo.weights -P ~/yolo/darknet

	##descargar un video dentro de la carpeta ~/yolo/darknet <<<<<---OJO

#ejecutando maquina virtual
	
	
	sudo nvidia-docker run -it --user 0 -p 5901:5901 -p 6901:6901 -v "/home/$USER/yolo:/headless/Desktop" luigymach/yolo-ubuntu-xfce-vnc:2.1.0 bash


#ingresar a la maquina virtual docker desde un navegador
	##por ejemplo (ex: http://192.168.10.188:6901/) 
	http://<my-ip>:6901/
	##pass: vncpassword


	
#dentro de la carpeta darknet ubicada en Desktop
	## compilar
	$ make

	##por ejemplo (ex: $./darknet detector demo cfg/coco.data cfg/yolo.cfg yolo.weights video_robo.mp4)
	$ ./darknet detector demo cfg/coco.data cfg/yolo.cfg yolo.weights <video-dentro-de-darknet>






Ref: 

https://pjreddie.com/darknet/yolo/
https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-docker-ce-1	
https://github.com/NVIDIA/nvidia-docker
https://hub.docker.com/r/luigymach/yolo-ubuntu-xfce-vnc/
