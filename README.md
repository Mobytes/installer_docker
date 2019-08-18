## INSTALLER DOCKER
Instalador de docker.

### Version
V0.4

### Technologies

* [DockerToolbox](https://drive.google.com/file/d/1ebWirBtiEBDf7JVL4utbmAH9ktqH0j8y/view?usp=sharing)

### Installation

You need Gulp installed globally:

```sh
$ mkdir sistravent && cd sistravent
$ git clone git@gitlab.com:pever/sistravent.com.git sistravent
$ virtualenv -p python3.4 virtual
$ source virtual/bin/activate
$ (virtual) cd sistravent
$ pip install -r requirements/local.txt
```

### Configurar Base de Datos `sistravent/settings/local.py`

copiar local.example.py a local.py
```sh
$ (virtual) cp sistravent/settings/local.example.py sistravent/settings/local.py
```

```py

DATABASES = {

    'default': {
            'ENGINE': 'tenant_schemas.postgresql_backend',
            'NAME': 'my_database',
            'USER': 'my_user',
            'PASSWORD': 'my_password',
            'HOST': 'localhost',
            'PORT': '5432',
        }
}
```

### Migraciones [warning]

```sh
$ (virtual) python manage.py makemigrations --settings=sistravent.settings.local
$ (virtual) python manage.py migrate_schemas --settings=sistravent.settings.local --shared
```

### Crear Super Usuario
```sh
$ (virtual) python manage.py createsuperuser --username=admin --schema=public --settings=sistravent.settings.local
```

### agregar data inicial
```sh
$ (virtual) python manage.py loaddata init.json --settings=sistravent.settings.local
$ (virtual) python manage.py loaddata init2.json --settings=sistravent.settings.local
$ (virtual) python manage.py loaddata init3.json --settings=sistravent.settings.local
```
### agregar data inicial por schema
```sh
$ (virtual) python manage.py tenant_command loaddata {file.json} --schema={schema} --settings=sistravent.settings.local
$ (virtual) python manage.py tenant_command loaddata concepts.json --schema=mobytes --settings=sistravent.settings.local
```

```sh
$ (virtual) python manage.py migrate_schemas --schema=tarapoto --settings=sistravent.settings.local
```

### Sincronizar Base de Datos
Este Comando les generará un sql, copiar ese sql y pegarlo en query y correrlo. Esto hará sincronizar nuestra aplicación django con la base de datos.

```sh
$ (virtual) python3 manage.py sqlsequencereset system config maintenance accounts finances inventory sales contacts auth permission --settings=sistravent.settings.local
```

### Iniciar
```sh
$ (virtual) python manage.py runserver --settings=sistravent.settings.local
```

## Starting the worker process
```sh
$ (virtual) celery -A sistravent worker -l info
$ (virtual) celery -A sistravent beat -l info
```

## Starting the beat process (cron)
```sh
$ (virtual) celery -A sistravent beat -l info
```

### Update Schemas (Danger)
```sh
$ (virtual) python
```

### Testing ```apply in src/```
```sh
$ (virtual) coverage run --source='.' manage.py test --settings=sistravent.settings.local
$ (virtual) coverage report
$ (virtual) coverage html
