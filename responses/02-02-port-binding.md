¡Muy bien!

Ahora vamos a hacer cambios para que nuestero servicio de Postgres lo podamos
acceder desde localhost, para conectarnos con nuestros IDE's (¿recuerdan que yo
uso Valentina Studio?).

Para éso, agrega [la llave `ports`](https://docs.docker.com/compose/compose-file/#ports)
para conectar nuestro puerto local `5432` (`HOST`) al puerto de postgres 
(`CONTAINER`), y poder verlo con nuestro IDE (Valentina Studio, etc)

Cuando lo hayas agregado, corre los siguientes comandos:

- `docker-compose down` para parar y eliminar todos los contenedores del stack,
  junto con **sus configuraciones anteriores**

- `docker-compose up` para volver a levantar los servicios del stack. Ahora,
  nuestro servicio de Postgres estará disponible en `localhost:5432`

Sí, no tenemos password aún. Para éso, necesitaremos agregar variables de
entorno a nuestro servicio, que haremos en el siguiente paso. Responde con un
comentario: "¿Qué pasó con el password?" para continuar.
