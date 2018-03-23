
`docker`
========

[Retornar](/README.md)
------------------------


Contenido 
---------



[Instalacion](./INSTALL.md)
---------------------------


¿Que es `docker`?
---------------------------


¿Para que sirve?
---------------------------


¿Que es `docker` hub?
---------------------------


¿Como usar `docker`?
---------------------------

### ¿Qué es una contenedor?
### ¿Qué es una instancia?
### ¿Qué es una imagen?



Comando básicos
----------------
### ¿Qué `imagenes` tengo?
```console
foo@bar:~$ sudo docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
REPOSITORY                       TAG                 IMAGE ID            CREATED             SIZE
luigymach/yolo-ubuntu-xfce-vnc   2.1.0               0b8381ae1f95        7 weeks ago         8.67GB
```
### ¿Qué instancias estan activas?

```console
foo@bar:~$ sudo docker ps
CONTAINER ID        IMAGE                                  COMMAND                  CREATED             STATUS              PORTS                                            NAMES
ea4f374da77b        luigymach/yolo-ubuntu-xfce-vnc:2.1.0   "/dockerstartup/vnc_…"   4 hours ago         Up 4 hours          0.0.0.0:5903->5901/tcp, 0.0.0.0:6903->6901/tcp   trusting_mayer
7382d5afbb0a        luigymach/yolo-ubuntu-xfce-vnc:2.1.0   "/dockerstartup/vnc_…"   4 hours ago         Up 4 hours          0.0.0.0:5902->5901/tcp, 0.0.0.0:6902->6901/tcp   fervent_carson
cfde2bf32000        luigymach/yolo-ubuntu-xfce-vnc:2.1.0   "/dockerstartup/vnc_…"   4 hours ago         Up 4 hours          0.0.0.0:5901->5901/tcp, 0.0.0.0:6901->6901/tcp   goofy_sammet

```

### ¿Qué instancias estan inactivas?

```console
foo@bar:~$ sudo docker ps -a
CONTAINER ID        IMAGE                                      COMMAND                  CREATED             STATUS                     PORTS                                            NAMES
305dd8df3fa6        luigymach/cluster-hadoop-spark-gpu:1.0.1   "sh -c 'service ssh …"   7 seconds ago       Exited (0) 3 seconds ago                                                    kind_noether
3f5bf7c3afdc        luigymach/cluster-hadoop-spark-gpu:1.0.1   "sh -c 'service ssh …"   14 seconds ago      Exited (0) 8 seconds ago                                                    jovial_einstein
ea4f374da77b        luigymach/yolo-ubuntu-xfce-vnc:2.1.0       "/dockerstartup/vnc_…"   4 hours ago         Up 4 hours                 0.0.0.0:5903->5901/tcp, 0.0.0.0:6903->6901/tcp   trusting_mayer
7382d5afbb0a        luigymach/yolo-ubuntu-xfce-vnc:2.1.0       "/dockerstartup/vnc_…"   4 hours ago         Up 4 hours                 0.0.0.0:5902->5901/tcp, 0.0.0.0:6902->6901/tcp   fervent_carson
cfde2bf32000        luigymach/yolo-ubuntu-xfce-vnc:2.1.0       "/dockerstartup/vnc_…"   4 hours ago         Up 4 hours                 0.0.0.0:5901->5901/tcp, 0.0.0.0:6901->6901/tcp   goofy_sammet
```
> Note que tambien se muestran las instancias que fueron `desechadas`


### Descargar una imagen de `https://hub.docker.com/`

Dirigirse a	un repositorio cualquiera, por ejemplo [Hello-work](https://hub.docker.com/_/hello-world/) 

- copiar Docker Pull Command
  - por ejemplo "docker pull hello-world"

```console
foo@bar:~$ sudo docker pull hello-world

```
Nos mostrara el siguiente mensaje.

```console
foo@bar:~$ sudo docker pull hello-world
Using default tag: latest
latest: Pulling from library/hello-world
Digest: sha256:97ce6fa4b6cdc0790cda65fe7290b74cfebd9fa0c9b8c38e979330d547d22ce1
Status: Image is up to date for hello-world:latest

```
podemos verificar con el comando `sudo docker images` visto anteriormente.

Cambiar de nombre a `imagen descargada`
---------------------------------------

Para esto se necesita el `IMAGE ID` de la imagen con [docker images](#qué-imagenes-tengo) 
- sudo docker [ID] [nombre-nuevo:version-nueva]


```console
foo@bar:~$ sudo docker tag f2a91732366c mynew-hello-work:2.0.0

```

```console
foo@bar:~$ sudo docker images
REPOSITORY                           TAG                 IMAGE ID            CREATED             SIZE
hello-world                          latest              f2a91732366c        4 months ago        1.85kB
mynew-hello-work                     2.0.0               f2a91732366c        4 months ago        1.85kB
```




Ejecucion
----------

### Crear nueva instancia de una imagen
#### run

### acceder a instancia ya creada
#### exec



Guardar cambios de una instancia de `docker`
---------------------------------------------

### Commit
```console
foo@bar:~$ 
```


### Guardar imagen
```console
foo@bar:~$ sudo docker save
```

### Cargar imagen
- sudo docker load < [nombre-del-archivo-a-cargar]
```console
foo@bar:~$ sudo docker load < imagen-guardade-en-disco.tar
```


Borrar
------


### kill
#### matar una instancia
Es nesario saber el `CONTAINER ID` de la instancia viva, ver comando [docker ps](#qué-instancias-estan-activas)
- sudo docker kill [CONTAINER ID] 

```console
foo@bar:~$ sudo docker kill ea4f374da77b
```
#### matar toda las instancias
```console
foo@bar:~$ sudo docker kill $(sudo docker ps -aq)
```


### rm
#### Borrar una imagen
```console
foo@bar:~$ 
```
#### Borrar una instancia desecha
```console
foo@bar:~$ 
```
#### borrar toda las `instancias inactivas`
```console
foo@bar:~$ sudo docker rm $(sudo docker ps -aq)
```



***
***
***



Ejemplos del autor.
--------------------

### [Spark y hadoop](./SPARK-HADOOP.md)
### [YOLO-VNC-cuda-opencv](./YOLO-VNC-CUDA-OPENCV.md)






Referencias
===========
- https://docs.docker.com/
