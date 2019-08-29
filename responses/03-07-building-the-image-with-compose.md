Último (de la sección): Ahora vamos a hacer un build de la imagen, pero usando
`docker-compose`.

Para ésto, necesitamos agregar un nuevo servicio `web` a nuestro archivo
`docker-compose.yml`:

```yaml
version: "3.7"

# ...

services:
  web:
    # ...
  postgres:
    # ...
```

Dentro del servicio `web`, agreguen [la llave `build`](https://docs.docker.com/compose/compose-file/#build)
para definir cómo se va a construir nuestra imagen de la app.

Dentro de la llave `build`, agreguen [la llave `context`](https://docs.docker.com/compose/compose-file/#context)
con el valor `.`.

Cuando hayan agregado ésta configuracion, construyan la imagen con el siguiente
comando:

```bash
docker-compose build web
```

Ésto indicará a docker que construya el Dockerfile usado en el servicio `web`,
y hará lo mismo que `docker build .`, pero ahora tenemos ya guardado la
configuracion de cómo generar ése `docker build .` :)

Si todo funcionó, debes guardar los cambios en Github para continuar: 

```bash
git add Dockerfile docker-compose.yml
git commit -m "Agrega el archivo para construir la imagen de la app"
git push origin master
```