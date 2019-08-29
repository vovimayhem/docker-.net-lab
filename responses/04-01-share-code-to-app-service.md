En ésta sección continuaremos configurando el servicio `web` que agregamos en
la sección anterior.

Lo que nos faltó (a propósito) en nuestra imagen es el código fuente de la app.
Ésto es porque en éste punto, queremos ser capaces de modificar el código de la
app:

Si hubiéramos incluido el código dentro de la imagen - las imágenes de docker
son "inmutables", o sea ya no se pueden cambiar - tendríamos qué volver a
construir la imagen con `docker-compose build web` cada vez que hiciéramos algún
cambio. ¡Nada ideal para un ambiente de desarrollo!

Lo que haremos nosotros será "montar" el directorio con el código fuente de la
app dentro de nuestro servicio - usando de nuevo [la llave `volumes`](https://docs.docker.com/compose/compose-file/#volumes)
ahora en el servicio de `web`. Pero a diferencia de la vez anterior, no será un
volúmen de docker, sino nuestro directorio.

Agreguen lo siguiente a la lista de volúmenes del servicio `web`: `.:/usr/src`.

Contesten "OK!" para continuar cuando hayan agregado el cambio.