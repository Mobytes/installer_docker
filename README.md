## INSTALLER DOCKER WINDOWS
Este manual es para poder instalar el software de hrsystem con docker en windows.

### Version
V0.4

### Technologies

* [DockerToolbox](https://drive.google.com/file/d/1ebWirBtiEBDf7JVL4utbmAH9ktqH0j8y/view?usp=sharing)
* [Git](https://git-scm.com)

Antes de configurar el software tenemos que localizar 

### Configuration
* Descargar la configuracion del instalador del software en docker.
```sh
$ git clone https://github.com/evervasquez/hrsystem_installer.git system
```

* Nos movemos a la carpeta con el comando ```cd```
```sh
$ cd system
```

* Descargar el codigo fuente del software preparado para la dockerizacion con el renombrar a la carpeta ``app``
```sh
$ git clone https://github.com/evervasquez/hrsystem.git app
```

* Configuracion  final
```
system/
├─ docker-compose.yml
├─ production.yml
├─ README.md
├─ .env
├─ nginx/
│  ├─ Dockerfile
│  └─ nginx.conf
├─ app/
│  ├─ hrsystem/
│  ├─ Dockerfile
│  ├─ Gulpfile.js
│  ├─ package.json
│  └─ ...
```

### Installation
Todos los comandos de docker tienen que ser lanzados dentro de la carpeta del proyecto de `docker`

### Situarnos en la carpeta system/
```sh
$ cd system/
```

### Creamos los servicios
```sh
$ docker-compose build
```

### Inciamos los servicios
```sh
$ docker-compose up -d
```


## Comandos adicionales


### Reniciar servicios de docker
```sh
$ docker-compose up -d --no-deps --build </service>
```

### Listar servicios de docker
```sh
$ docker ps
```

### Entrar en el contenedor
```sh
$ docker exec -i -t [name-container] /bin/bash
```

### Clear project docker
* Eliminar todos los contenedores detenidos, 
```sh
$ docker system prune
```

* Eliminar volumenes detenidos.
```sh
$ docker system prune --volumes
```

* Remove one or more containers
```sh
$ docker container ls -a
$ docker container rm cc3f2ff51cab cd20b396a061
```
