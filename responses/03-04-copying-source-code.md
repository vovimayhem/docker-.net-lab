Ahora necesitamos copiar el archivo con la lista de dependencias de la app.

Utilicen [el comando `COPY`](https://docs.docker.com/engine/reference/builder/#copy)
para copiar el archivo `MvcMovie.csproj` (que entre otras cosas, contiene la
lista de dependencias) al directorio `/usr/src/`.

**Noten** que hay qué agregar el slash final en éste comando, para que no
intente guardar el archivo con el nombre `src` dentro del folder `/usr/`.

Cuando hayan agregado éste comando, respondan "OK!"