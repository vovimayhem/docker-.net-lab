¡Ya es el último!

En éste paso daremos de alta un volúmen en donde puedan guardarse los datos
del servicio de postgres, y cómo montarlo en los contenedores de ése servicion.

Para dar de alta volúmenes con su configuración, es necesario agregar
[la llave `volumes`](https://docs.docker.com/compose/compose-file/#volume-configuration-reference) en la raíz
del documento - éso es, al mismo nivel que `services`:

```yaml
version: "3.7"

volumes:
  my_volume_name:

services:
  postgres:
    # ...
```

El nombre de volume deberá ser `postgres_data`. No nos meteremos con
configuraciones adicionales - como drivers, etc. Lo podemos dejar así tal y como
lo mostramos en el ejemplo anterior... ¡Pero sí cambien el nombre!

Ahora, vamos a configurar el servicio de `postgres` para que utilice ése volúmen
para guardar los datos: Agreguemos [la llave `volumes`](https://docs.docker.com/compose/compose-file/#volumes)
al servicio de `postgres` - ojo: ésta configuración es una lista de valores.

De [la documentación de la imagen oficial de Postgres](https://hub.docker.com/_/postgres),
necesitamos saber en dónde se guardan los datos por default. Busquen "Where to
Store Data" y tomen nota del directorio.

Agreguemos a la lista de volúmenes el siguiente mapeo: 
`postgres_data:/path/to/where/postgres/stores/data` (¡cambien el path!). Con
ésto, estaremos haciendo que el directorio donde se guarda la data en realidad
es un volúmen de Docker para guardar la info.


Cuando hayas terminado de agregar los cambios, repetiremos el ciclo de los pasos
anteriores:

- `docker-compose down` para borrar una vez más el contenedor del servicio de
  `postgres`, ya que éste se creó sin usar el volúmen en el paso anterior.

- `docker-compose up` para volver a levantar los servicios del stack. Ahora,
  podremos agregar y guardar datos, volver a repetir `docker-compose down` para
  eliminar el contenedor de `postgres`, pero ésta vez sin perder los datos.

Si todo funcionó, debes guardar los cambios en Github para continuar: 

```bash
git add docker-compose.yml
git commit -m "Agrega la base de datos de postgresql"
git push origin master
```