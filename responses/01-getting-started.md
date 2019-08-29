¡Hola!

Vamos a empezar por utilizar [docker-compose](https://docs.docker.com/compose/),
que es una herramienta para definir y correr applicaciones multi-contenedores
(stacks) de Docker.

### Nota para los usuarios de Linux

La instalación de Docker en Linux no incluye Docker Compose. Sigan
[los pasos para installar Docker Compose](https://docs.docker.com/compose/install/).

### Agregar Postgres al stack

Empezemos por crear un archivo llamado `docker-compose.yml` en la raíz del
proyecto - observen que éste fragmento de código ya define un volúmen para los
datos de la DB:

```yaml
version: "3.7"

services:
  postgres:
    # Aquí estaremos agregando las configuración del servicio de postgres
```

Utilizaremos [la imagen oficial de Postgres](https://hub.docker.com/_/postgres)
para iniciar los contenedores de éste servicio. Les recomiendo usar la version
`postgres:11-alpine`, ya que es una imagen muy pequeña, y se descarga muy rápido.

Para decirle a `docker-compose` que utilice ésta imagen como base, debemos
agregar [la llave `image`](https://docs.docker.com/compose/compose-file/#image),
con el nombre de la imagen que queremos usar.

Una vez que tengan hayan hecho éstos cambios, podremos levantar podremos iniciar
el servicio con el siguiente comando:

```bash
docker-compose up
```

Cuando vean que se disparan un montón de mensajes de log, es hora de hacer un
Commit + Push con Git, para avanzar al siguiente paso.
