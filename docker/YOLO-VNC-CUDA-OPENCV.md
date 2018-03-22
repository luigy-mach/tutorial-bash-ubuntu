
YOLO
====

[Retornar](./README.md)
------------------------




Contenido
----------

   * [YOLO](#yolo)
      * [<a href="./README.md">Retornar</a>](#retornar)
      * [Contenido](#contenido)
      * [Descargando imagen de <a href="https://hub.docker.com/r/luigymach/yolo-ubuntu-xfce-vnc/" rel="nofollow">docker hub</a>](#descargando-imagen-de-docker-hub)
      * [Clonando proyecto](#clonando-proyecto)
         * [Descargando pesos](#descargando-pesos)
      * [Ejecutando maquina virtual](#ejecutando-maquina-virtual)
      * [Ingresar a la maquina virtual docker desde un navegador](#ingresar-a-la-maquina-virtual-docker-desde-un-navegador)
      * [Dentro de la carpeta darknet ubicada en Desktop](#dentro-de-la-carpeta-darknet-ubicada-en-desktop)
      * [Referencias:](#referencias)





Descargando imagen de [`docker hub`](https://hub.docker.com/r/luigymach/yolo-ubuntu-xfce-vnc/)
------------------------------


- Verificando imagenes
```console
foo@bar:~$ sudo docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
```

- Descargando imagen de [`docker hub`](https://hub.docker.com/r/luigymach/yolo-ubuntu-xfce-vnc/)
```console
foo@bar:~$ docker pull luigymach/yolo-ubuntu-xfce-vnc:2.1.0
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

```
- Verificando Descarga

```console
foo@bar:~$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
REPOSITORY                       TAG                 IMAGE ID            CREATED             SIZE
luigymach/yolo-ubuntu-xfce-vnc   2.1.0               0b8381ae1f95        7 weeks ago         8.67GB
```

> En caso se tenga una imagen guardada en disco usar `load`,ver[`load`](./README.md/#cargar-imagen)
------------------------




Clonando proyecto
--------------------
```console
foo@bar:~$ mkdir -p ~/yolo/darknet
foo@bar:~$ git clone https://github.com/luigy-mach/darknet.git ~/yolo/darknet
foo@bar:~$ cd ~/yolo/darknet
```

### Descargando pesos
- wget <file.ext> -P ~/yolo/darknet
```console
foo@bar:~$ wget https://pjreddie.com/media/files/yolo.weights -P ~/yolo/darknet
```

> NOTA: Descargar un video dentro de la carpeta `~/yolo/darknet`


Ejecutando maquina virtual
------------------------------	
- `sudo nvidia-docker run -it --user 0 -p 5901:5901 -p 6901:6901 -v "\[carpeta-a-montar\]:\[ubicacion-dentro-de-docker\]" \[nombre-de-la-imagen\]:\[tag-version\] bash`
```console
foo@bar:~$ sudo nvidia-docker run -it --user 0 -p 5901:5901 -p 6901:6901 -v "/home/$USER/yolo:/headless/Desktop" luigymach/yolo-ubuntu-xfce-vnc:2.1.0 bash
```

Ingresar a la maquina virtual docker desde un navegador
-------------------------------------------------------
- `http://\[my-ip\]:6901/`
- pass: vncpassword


	
Dentro de la carpeta darknet ubicada en Desktop
-----------------------------------------------
- Compilar proyecto
```console
foo@bar:~$ make
```

- `./darknet detector demo cfg/coco.data cfg/yolo.cfg \[ubicacion-pesos.weights\] \[video-test\]`


```console
foo@bar:~$ ./darknet detector demo cfg/coco.data cfg/yolo.cfg yolo.weights video.mp4
```
	


Referencias: 
-------------

- https://pjreddie.com/darknet/yolo/
- https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-docker-ce-1	
- https://github.com/NVIDIA/nvidia-docker
- https://hub.docker.com/r/luigymach/yolo-ubuntu-xfce-vnc/

