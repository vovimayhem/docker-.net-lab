¡OK! Vamos a agregar ése password para acceder al servicio de Postgres.

Según [la documentación de la imagen oficial de Postgres](https://hub.docker.com/_/postgres), existen varias variables de entorno que permiten configurar el usuario inicial, el password del usuario inicial, el nombre de la base de datos inicial, las opciones de arranque del servicio y de la locación del directorio donde se almacenan los datos.

Busquen "Environment Variables" en [la documentación de la imagen oficial de Postgres](https://hub.docker.com/_/postgres), para ver qué variable de entorno necesitamos agregar para configurar el password del usuario inicial.

Cuando sepamos qué variable de entorno utilizar, agreguemos [la llave `environment`](https://docs.docker.com/compose/compose-file/#environment) al servicio de `postgres`, y después agreguemos la variable de entorno para hacer que `3x4mpl3P455` sea el password del usuario inicial.

Cuando lo hayas agregado, corre los siguientes comandos:

- `docker-compose down` para borrar de nuevo el contenedor del servicio de `postgres`, ya que éste se creó sin password en el paso anterior.

- `docker-compose up` para volver a levantar los servicios del stack. Ahora, podremos acceder al servicio en `localhost:5432` con el usuario `postgres` y el password `3x4mpl3P455`.


Si seguimos repitiendo los comandos `docker-compose down` y `docker-compose up`, van a notar que la base de datos se está eliminando constantemente... porque nos falta persistir los datos en un volúmen - tal como lo vimos el martes con `docker`. Es hora de saber configurar lo mismo, pero con `docker-compose`.

Responde "¿Cómo guardo los datos en un volúmen?" en éste Issue para continuar.