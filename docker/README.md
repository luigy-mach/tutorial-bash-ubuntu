
`docker`
========

[Retornar](/README.md)
------------------------


Contenido 
---------

   * [docker](#docker)
      * [<a href="/README.md">Retornar</a>](#retornar)
      * [Contenido](#contenido)
      * [Qué es docker?](#qué-es-docker)
         * [Imagenes y containers](#imagenes-y-containers)
      * [Container y maquinas virtuales](#container-y-maquinas-virtuales)
      * [<a href="./INSTALL.md">Instalacion</a>](#instalacion)
      * [Qué es docker hub?](#qué-es-docker-hub)
         * [Como descargar una imagen](#como-descargar-una-imagen)
      * [Comandos básicos](#comandos-básicos)
         * [Descargar una imagen pull](#descargar-una-imagen-pull)
         * [images disponibles](#images-disponibles)
         * [Instancias activas ps](#instancias-activas-ps)
         * [Instancias inactivas ps -a](#instancias-inactivas-ps--a)
         * [Cambiar de nombre a imagen tag](#cambiar-de-nombre-a-imagen-tag)
         * [Guardar imagen save](#guardar-imagen-save)
         * [Cargar imagen load](#cargar-imagen-load)
         * [Borrar una imagen rmi](#borrar-una-imagen-rmi)
      * [Correr instancias](#correr-instancias)
         * [Primer plano run -it](#primer-plano-run--it)
         * [Segundo plano run -d](#segundo-plano-run--d)
         * [Entrar a una instancian en segundo plano exec](#entrar-a-una-instancian-en-segundo-plano-exec)
      * [Cliclo de vida de una instancia de docker](#cliclo-de-vida-de-una-instancia-de-docker)
         * [Matar una instancia kill](#matar-una-instancia-kill)
         * [Matar toda las instancias activas](#matar-toda-las-instancias-activas)
         * [Borrar una instancia desecha](#borrar-una-instancia-desecha)
         * [Borrar toda las instancias inactivas](#borrar-toda-las-instancias-inactivas)
      * [Subir un image a <code>docker hub</code>](#subir-un-image-a-docker-hub)
         * [commit](#commit)
      * [Subir un image a <code>docker hub</code>](#subir-un-image-a-docker-hub-1)
         * [push](#push)
      * [Ejemplos del autor.](#ejemplos-del-autor)
         * [<a href="./SPARK-HADOOP.md">Spark y hadoop</a>](#spark-y-hadoop)
         * [<a href="./YOLO-VNC-CUDA-OPENCV.md">YOLO-VNC-cuda-opencv</a>](#yolo-vnc-cuda-opencv)
   * [Referencias](#referencias)









Qué es `docker`?
---------------
`Docker` es una plataforma para desarrolladores y [sysadmins](https://en.wikipedia.org/wiki/System_administrator) para **desarrollar, deployar y correr** aplicaciones con **containers**. 

### Imagenes y containers
- [ **`runtime`** ](https://stackoverflow.com/questions/3900549/what-is-runtime) en general este termino se refieres a cualquier libreria, framewokr o plataforma donde tu codigo corre. 

- Un `container` se inicia cuando ejecutamos una imagen.
- Una **`image`** es una paquete ejecutable que incluye todo lo necesario para ejecutar una aplicacion, o sea, codigo, entornos de ejecución(*runtimes*) ,librerias, variables global es y configuracion de archivos.

- Un **`container`** es una instancia **runtime** de una **imagen**; es decir una imagen se convierte en memoria cuando se ejecuta (`una imagen con estado o proceso de usuario`)



`Container` y maquinas virtuales
----------------------------
- Un **`container`** se ejecuta nativamente sobre linux y comparte el kernel de la maquina huesped (host) con otros `containers`. Se ejecuta como un proceso discreto, no ocupa más memoria que otro ejecutable, convirtiendolo en super ligero.


- En contraste con una **`maquina virtual`**(VM, *vitual machine*) que ejecuta un sistema operativo completo con `acceso virtual`, es decir que tiene acceso a los recursos de la maquina hospedera (host) esto se da atravez del `hypervisor`

![docker vs VM|512x397](./images/dockerAndVM.png)


[Instalacion](./INSTALL.md)
---------------------------


Qué es `docker hub`?
--------------------
[`docker hub`](https://hub.docker.com/) es un servivio de registro basado en la nube que permite vinvular repositorios (codigo), crear tus propias `images` y probarlas. Además de subir las `images` a docker cloud. 

- Esto proporciona un recurso centralizados para guardar,distribuir y colaborar con equipos de trabajo.

![docker hub](./images/dockerHub.png)

> NOTA: Puedes buscar y descargar `docker images` sin tener una cuenta, siembargo para subir alguna `imagen` debes tener una cuenta.

- Crea tu cuenta [AQUI](https://hub.docker.com/)



### Como descargar una imagen 
- Para descargar una imagen de [`docker hub`](https://hub.docker.com/)
se debe usar el comando [`pull`](#descargar-una-imagen-pull)






Comandos básicos
----------------

### Descargar una imagen `pull`

- Dirigirse a un repositorio de su elección
  - Por ejemplo [Hello-work](https://hub.docker.com/_/hello-world/) 

- Copiar el contenido de **Docker Pull Command**
  - por ejemplo **`docker pull hello-world`**

```console
foo@bar:~$ sudo docker pull hello-world

```
- Nos mostrara el siguiente mensaje.

```console
foo@bar:~$ sudo docker pull hello-world
Using default tag: latest
latest: Pulling from library/hello-world
Digest: sha256:97ce6fa4b6cdc0790cda65fe7290b74cfebd9fa0c9b8c38e979330d547d22ce1
Status: Image is up to date for hello-world:latest

```
- Podemos verificar con el comando [`images`](#images-disponibles) visto anteriormente.



### `images` disponibles 
- Nos muestra que `images` locales tengo.

```console
foo@bar:~$ sudo docker images
REPOSITORY                       TAG                 IMAGE ID            CREATED             SIZE
luigymach/yolo-ubuntu-xfce-vnc   2.1.0               0b8381ae1f95        7 weeks ago         8.67GB
```

### Instancias activas `ps`
- Nos muestra que `instancias` activas de `imagenes de docker` tengo.

```console
foo@bar:~$ sudo docker ps
CONTAINER ID        IMAGE                                  COMMAND                  CREATED             STATUS              PORTS                                            NAMES
ea4f374da77b        luigymach/yolo-ubuntu-xfce-vnc:2.1.0   "/dockerstartup/vnc_…"   4 hours ago         Up 4 hours          0.0.0.0:5903->5901/tcp, 0.0.0.0:6903->6901/tcp   trusting_mayer
7382d5afbb0a        luigymach/yolo-ubuntu-xfce-vnc:2.1.0   "/dockerstartup/vnc_…"   4 hours ago         Up 4 hours          0.0.0.0:5902->5901/tcp, 0.0.0.0:6902->6901/tcp   fervent_carson
cfde2bf32000        luigymach/yolo-ubuntu-xfce-vnc:2.1.0   "/dockerstartup/vnc_…"   4 hours ago         Up 4 hours          0.0.0.0:5901->5901/tcp, 0.0.0.0:6901->6901/tcp   goofy_sammet

```




### Instancias inactivas `ps -a`
- Nos muestra que `instancias` **activas y inactivas** de `imagenes de docker` tenemos.
> Note que tambien se muestran las instancias que fueron **`desechadas`**(inactivas)

```console
foo@bar:~$ sudo docker ps -a
CONTAINER ID        IMAGE                                      COMMAND                  CREATED             STATUS                     PORTS                                            NAMES
305dd8df3fa6        luigymach/cluster-hadoop-spark-gpu:1.0.1   "sh -c 'service ssh …"   7 seconds ago       Exited (0) 3 seconds ago                                                    kind_noether
3f5bf7c3afdc        luigymach/cluster-hadoop-spark-gpu:1.0.1   "sh -c 'service ssh …"   14 seconds ago      Exited (0) 8 seconds ago                                                    jovial_einstein
ea4f374da77b        luigymach/yolo-ubuntu-xfce-vnc:2.1.0       "/dockerstartup/vnc_…"   4 hours ago         Up 4 hours                 0.0.0.0:5903->5901/tcp, 0.0.0.0:6903->6901/tcp   trusting_mayer
7382d5afbb0a        luigymach/yolo-ubuntu-xfce-vnc:2.1.0       "/dockerstartup/vnc_…"   4 hours ago         Up 4 hours                 0.0.0.0:5902->5901/tcp, 0.0.0.0:6902->6901/tcp   fervent_carson
cfde2bf32000        luigymach/yolo-ubuntu-xfce-vnc:2.1.0       "/dockerstartup/vnc_…"   4 hours ago         Up 4 hours                 0.0.0.0:5901->5901/tcp, 0.0.0.0:6901->6901/tcp   goofy_sammet
```




### Cambiar de nombre a imagen `tag`
- Para esto se necesita el `IMAGE ID`, lo podemos obtener con [`images`](#images-disponibles) 

> sudo docker tag [ID] [nombre-nuevo:version-nueva]


```console
foo@bar:~$ sudo docker tag f2a91732366c mynew-hello-work:2.0.0

```

- Se observa como con una misma `IMAGE ID` tenemos dos `REPOSITORY` (nombre de repositorio)
```console
foo@bar:~$ sudo docker images
REPOSITORY                           TAG                 IMAGE ID            CREATED             SIZE
hello-world                          latest              f2a91732366c        4 months ago        1.85kB
mynew-hello-work                     2.0.0               f2a91732366c        4 months ago        1.85kB
```



### Guardar imagen `save`
- sudo docker save > [nombre-del-archivo-a-guardar.tar] 
```console
foo@bar:~$ sudo docker save busybox > busybox.tar
foo@bar:~$  ls -sh busybox.tar
2.7M busybox.tar
```

### Cargar imagen `load`
- sudo docker load < [nombre-del-archivo-a-cargar]
```console
foo@bar:~$ ls
busybox.tar.gz 

foo@bar:~$ sudo docker docker images 
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE

foo@bar:~$ sudo docker load < busybox.tar.gz
Loaded image: busybox:latest

foo@bar:~$ sudo docker docker images 
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
busybox             latest              769b9341d937        7 weeks ago         2.489 MB

```



### Borrar una imagen `rmi`

- Para esto se necesita el `IMAGE ID`, lo podemos obtener con [`images`](#images-disponibles) 

```console
foo@bar:~$ sudo docker images

REPOSITORY                TAG                 IMAGE ID            CREATED             SIZE
test1                     latest              fd484f19954f        23 seconds ago      7 B (virtual 4.964 MB)
test                      latest              fd484f19954f        23 seconds ago      7 B (virtual 4.964 MB)
test2                     latest              fd484f19954f        23 seconds ago      7 B (virtual 4.964 MB)

foo@bar:~$ sudo docker rmi fd484f19954f

Error: Conflict, cannot delete image fd484f19954f because it is tagged in multiple repositories, use -f to force
2013/12/11 05:47:16 Error: failed to remove one or more images

foo@bar:~$ sudo docker rmi test1

Untagged: test1:latest

foo@bar:~$ sudo docker rmi test2

Untagged: test2:latest


foo@bar:~$ sudo docker images

REPOSITORY                TAG                 IMAGE ID            CREATED             SIZE
test                      latest              fd484f19954f        23 seconds ago      7 B (virtual 4.964 MB)

$ docker rmi test

Untagged: test:latest
Deleted: fd484f19954f4920da7ff372b5067f5b7ddb2fd3830cecd17b96ea9e286ba5b8
```





Correr instancias
-----------------

Existe dos formas de `crear una instancia` de docker:

### Primer plano `run -it`

- Podemos ejecutar y usar una terminal en el contenedor:

```console
foo@bar:~$ sudo docker run -ti ubuntu:14.04 /bin/bash
```
  - t: Asigna una tty (hace referencia a una **consola/terminal** en linux)
  - i: Nos comunicamos con el contenedor de **`modo interactivo`**.

> **NOTA**: Al salir del **modo interactivo** el contenedor se detendrá.


### Segundo plano `run -d`
- **Problema**: Ya sabemos cómo correr un contenedor en modo interativo `run -it`. El problema es que el mismo al terminar de ejecutar la tarea, finaliza. 
- Que pasaria si quieren hacer contenedores que corran servicios 
   - Por ejemplo, un servidor web, el comando es el siguiente:
```console
foo@bar:~$ sudo docker run -d -p 8080:8080 python:2.7 python -m SimpleHTTPServer 8080
```
   - Esto ejecuta un servidor Python (SimpleHTTPServer module), en el puerto 8080. 
   - `-p 8080:8080` le indica a Docker que tiene que hacer un **port forwarding** del contenedor hacia el puerto 8080 de la máquina hospedera (host).
   - Ahora podemos abrir un Navegador con `http://localhost:8080` y accederemos al servicio.

> **NOTA**: Luego de ejecutar el **Detached Mode** el contenedor no se detendrá, Estará corriendo en segundo plano, para accesar a esta maquina virtual usaremos el comando [**exec**](#entrar-a-una-instancian-en-segundo-plano-exec)

### Entrar a una instancian en segundo plano `exec`

- La opción **-d** hace que el contenedor se ejecute en segundo plano. Esto nos permite ejecutar comandos sobre el mismo en cualquier momento mientras esté en ejecución. Por ejemplo:

```console
foo@bar:~$ sudo docker exec -ti <container-id> /bin/bash
```
  - t: Asigna una tty (hace referencia a una **consola/terminal** en linux)
  - i: Nos comunicamos con el contenedor de **`modo interactivo`**.

> **NOTA**: Al salir del **modo interactivo** en **Detached Mode**  el contenedor no se detendrá.







Cliclo de vida de una `instancia` de docker
---------------------------------------------

- Hasta que hemos visto como ejecutar una `instancia` de docker en **modo interactivo** y **Detached Mode**. Ahora veremos cómo manejar el ciclo de vida de un contenedor. 
- Docker provee de comandos como:


### Matar una instancia `kill`
- Es necesario saber el `CONTAINER ID` de la **instancia viva**, 
   - ver comando: [docker ps](#instancias-activas-ps)
   - `sudo docker kill [CONTAINER ID]`

```console
foo@bar:~$ sudo docker kill ea4f374da77b
```

### Matar toda las instancias activas
```console
foo@bar:~$ sudo docker kill $(sudo docker ps -aq)
```



### Borrar una instancia desecha
- Es necesario saber el `CONTAINER ID` de la **instancia inactiva**, 
   - ver comando: [docker ps -a](#instancias-activas-ps)
   - `sudo docker rm [CONTAINER ID]` 
```console
foo@bar:~$ sudo docker rm ea456g6da77
```

### Borrar toda las `instancias inactivas`
```console
foo@bar:~$ sudo docker rm $(sudo docker ps -aq)
```


- Con todos ellos podremos usar el argumento **--help** para ver las opciones disponibles. 
   - Ejemplo: 

```console
foo@bar:~$ sudo docker rm --help

Usage:   docker rm [OPTIONS] CONTAINER [CONTAINER...]

Remove one or more containers

Options:
  -f, --force     Force the removal of a running container (uses SIGKILL)
      --help      Print usage
  -l, --link      Remove the specified link
  -v, --volumes   Remove the volumes associated with the container
```







Subir un `image` a `docker hub`
---------------------------------------

 ### commit

- Si deseamos `guardar` los cambios que hicimos dentro de una `instancia` de docker. Haremos lo siguiente:

   - Necesitamos saber que `instancias` tenemos activas.
```console
foo@bar:~$ sudo docker ps

CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS              NAMES
c3f279d17e0a        ubuntu:12.04        /bin/bash           7 days ago          Up 25 hours                            desperate_dubinsky
197387f1b436        ubuntu:12.04        /bin/bash           7 days ago          Up 25 hours                            focused_hamilton
```

   - Luego ejecutaremos el comando `commit` guiamos de la siguiente estructura
   - `sudo docker commit [CONTAINER ID]  [nombre-que-deseamos-poner]:[version]`

```console
foo@bar:~$ sudo docker commit c3f279d17e0a  testimage:version3

f5283438590d

foo@bar:~$ sudo docker images

REPOSITORY                        TAG                 ID                  CREATED             SIZE
svendowideit/testimage            version3            f5283438590d        16 seconds ago      335.7 MB
```

> NOTA: Si la instancia se encuentra `inactiva` tambien es posible aplicar el comando `commit`




Subir un `image` a `docker hub`
---------------------------------------

### `push`
- Es necesario crear una cuentan en `docker hub` 
- Primero loguearse
```console
foo@bar:~$ sudo docker login
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username : 

```

- Para poder ejecutar un `push` se debe tener en cuenta lo siguiente:
   - El nombre del repositorio obtenido con de `sudo docker images`, es decir `REPOSITORY` debe contener el usuario de `docker hub`. 
   - En caso no lo tenga ver el comando [tag](#cambiar-de-nombre-a-imagen-tag)
      - Por ejemplo:
         - `REPOSITORY` para este ejemplo usaremos `hello-world` y usaremos el usuario docker `lugymach`
            - `luigymach/<nombre-de-repository>:<version>`
            - `luigymach/hello-world:1.0.0`

```console
foo@bar:~$ sudo docker images
REPOSITORY                               TAG                          IMAGE ID            CREATED             SIZE
hello-world                              latest                       f2a91732366c        4 months ago        1.85 kB

foo@bar:~$ sudo tag f2a91732366c luigymach/hello-world:1.0.0

```
   - Tenemos todo listo para ejecutar el comando `push`
      

```console
foo@bar:~$ sudo docker images
REPOSITORY                               TAG                          IMAGE ID            CREATED             SIZE
hello-world                              latest                       f2a91732366c        4 months ago        1.85 kB
luigymach/hellowork-test                 1.0.0                        f2a91732366c        4 months ago        1.85 kB


foo@bar:~$ sudo docker push luigymach/hellowork-test:1.0.0

The push refers to a repository [docker.io/luigymach/hellowork-test]
f999ae22f308: Mounted from library/hello-world 
1.0.0: digest: sha256:8072a54ebb3bc136150e2f2860f00a7bf45f13eeb917cca2430fcd0054c8e51b size: 524
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

- https://docs.docker.com/get-started/#docker-concepts
- https://github.com/brunocascio/docker-espanol
- https://docker-curriculum.com/
- https://docs.docker.com/engine/reference/commandline/docker/