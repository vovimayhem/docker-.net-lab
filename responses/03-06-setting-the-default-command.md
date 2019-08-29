Ahora definiremos el comando default que correrá la imagen.

El comando `dotnet watch run` servirá para iniciar el servicio web dentro del
contenedor. Cuando se detecte que hubo un cambio en el contenido del directorio
de la app (Aquí dentro será `/usr/src`), éste recompilará la aplicación y
reiniciará el servicio dentro del contenedor.

Usemos [el comando `CMD`](https://docs.docker.com/engine/reference/builder/#cmd)
en nuestro Dockerfile para asegurarnos que el comando por default que se
ejecutará con la imagen sea `dotnet watch run`.

Una vez que hayan terminado, respondan "OK!" para continuar.
