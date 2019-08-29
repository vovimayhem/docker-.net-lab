Ahora nos toca agregar un servicio de bases de datos al stack. Usaremos
PostgreSQL en éste curso.

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

Cuando vean que se disparan un montón de mensajes de log, es hora de responder
"OK!" en éste Issue, para recibir la siguiente indicación :)
