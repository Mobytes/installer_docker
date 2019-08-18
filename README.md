## INSTALLER DOCKER WINDOWS
Instalador de docker.

### Version
V0.4

### Technologies

* [DockerToolbox](https://drive.google.com/file/d/1ebWirBtiEBDf7JVL4utbmAH9ktqH0j8y/view?usp=sharing)
* [Git](https://git-scm.com)

### Installation
Descargar la configuracion del instalador del software en docker
```sh
$ git clone https://github.com/evervasquez/hrsystem_installer.git system
```
Nos movemos a la carpeta con el comando ```cd```

```sh
$ cd system
```

Descargar el codigo fuente del software preparado para la dockerizacion con el renombrar a la carpeta ``app``

```sh
$ git clone https://github.com/evervasquez/hrsystem.git app
```

### Docker
Para comenzar a correr docker para que haga su trabajo

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
