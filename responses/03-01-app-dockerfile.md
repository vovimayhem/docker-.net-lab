Ahora vamos a pasarnos a algo diferente: Crear una imagen para correr la app.

Para ésto primero necesitamos construir una imagen de Docker con .NET y con las
librerías que necesitamos para correr la app en "modo desarrollo", y configurar
el comando default con el que vamos a correr la app.

Para ésto, necesitaremos crear un archivo `Dockerfile`:

### Archivo Dockerfile

Un archivo Dockerfile` es un archivo de texto con la siguiente estructura:

```Dockerfile
FROM nombre-de-la-imagen-base

ENV NOMBRE_DE_VARIABLE VALOR_DE_VARIABLE

WORKDIR /directorio/que-queremos/que-sea-el-default

COPY archivos-que-queremos-copiar destino-de archivos

RUN comando-para-agregar-cosas-a-la-imagen
```

Vamos a crear un archivo llamado así: `Dockerfile` (noten la falta de extensión)
en la raíz del proyecto.

El primer comando que agregaremos a éste archivo será [el comando `FROM`](https://docs.docker.com/engine/reference/builder/#from) para usar [la imagen de microsoft `microsoft/dotnet:sdk`](https://hub.docker.com/_/microsoft-dotnet-core) como nuestra base.

Respondan "OK!" para continuar