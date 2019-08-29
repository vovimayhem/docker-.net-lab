Ahora usaremos [el comando `ENV`](https://docs.docker.com/engine/reference/builder/#env)
para guardar 2 variables de entorno en la imagen:
  
  - La variable `HOME` con el valor `/usr/src`, para indicarle al entorno del
    contenedor que el directorio `/usr/src` es el home del sistema, y se guarde
    ahí cosas como el historial de comandos (muy útil en desarrollo)
  
  - La variable `NUGET_PACKAGES` con el valor `/usr/nuget/packages`, para
    indicarle a NuGet (El administrador de paquetes de .NET) en dónde es que
    debe guardar las dependencias descargadas.

  - La variable `PORT` con el valor `5000`, para indicarle a la app que el
    levante el servidor web en el puerto 5000 por default.

Noten que cuando agregamos variables de entorno con el comando `ENV` a la imagen,
éstos valores se quedarán guardados en la imagen.

Respondan con "OK!" para continuar