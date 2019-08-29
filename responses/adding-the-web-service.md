Nice!

Ahora vamos a agregar el servicio de nuesta aplicación web.

Para ésto primero necesitamos construir una imagen de Docker con .NET y con las librerías que necesitamos para correr la app en "modo desarrollo"

### Archivo Dockerfile

Vamos a crear un archivo llamado `Dockerfile` (noten la falta de extensión) en la raíz del proyecto. Los archivos `Dockerfile` tienen ésta estructura (no son todos los comandos que existen):

```Dockerfile
FROM nombre-de-la-imagen-base

ENV NOMBRE_DE_VARIABLE VALOR_DE_VARIABLE

WORKDIR /directorio/que-queremos/que-sea-el-default

COPY archivos-que-queremos-copiar destino-de archivos

RUN comando-para-agregar-cosas-a-la-imagen
```

Entonces, nuestro archivo va a tener 5 pasos - las apps de .NET son relativamente sencillas para el Dockerfile:

1. Usaremos [el comando `FROM`](https://docs.docker.com/engine/reference/builder/#from) para usar [la imagen de microsoft `microsoft/dotnet:sdk`](https://hub.docker.com/_/microsoft-dotnet-core) como nuestra base.

2. Usaremos [el comando `ENV`](https://docs.docker.com/engine/reference/builder/#env) para guardar 2 variables de entorno en la imagen:
    - La variable `HOME` con el valor `/usr/src`, para indicarle al entorno del contenedor que el directorio `/usr/src` es el home del sistema, y se guarde ahí cosas como el historial de comandos (muy útil en desarrollo)
    - La variable `NUGET_PACKAGES` con el valor `/usr/nuget/packages`, para
    indicarle a NuGet (El administrador de paquetes de .NET) en dónde es que debe guardar las dependencias descargadas.

3. Usaremos [el comando `WORKDIR`](https://docs.docker.com/engine/reference/builder/#workdir) para configurar que el directorio `/usr/src` sea el directorio default en donde se ejecutarán los comandos que le enviemos al contenedor, y que se el directorio al que entraremos cuando entremos al container.

4. Usaremos [el comando `COPY`](https://docs.docker.com/engine/reference/builder/#copy) para copiar el archivo `MvcMovie.csproj` (que contiene la lista de dependencias) al directorio `/usr/src/` - Noten que hay qué agregar el slash final en éste comando, para que no intente guardar el archivo con el nombre `src` dentro del folder `/usr/`.

5. Usaremos [el comando `RUN`](https://docs.docker.com/engine/reference/builder/#run) para correr el comando `dotnet restore`, que entre otras cosas, descargará las dependencias del proyecto definidas en el archivo `MvcMovie.csproj`

6. Usaremos [el comando `CMD`](https://docs.docker.com/engine/reference/builder/#cmd) para configurar que el comando por default que se ejecutará con la imagen sea `dotnet watch run`

### Compose

```yaml

services:
  postgres:
    #...
  web:
    build:
      context: . #
    ports:
      - 5000:5000
    volumes:
      - .:/usr/src
```

Ahora vamos a ver un poco más de acción:

1. Agregaremos un nuevo servicio llamado `web` al archivo de `docker-compose.yml`. Éste servicio tendrá una configuración llamada `build`, y ésta a su vez una configuración llamada `context`. Con ésto estamos diciendole a `docker-compose` algo parecido a cuando ejecutamos `docker build .`