Ahora, usaremos el comando `dotnet restore` para descargar las dependencias del
proyecto, y que se queden guardadas en la imagen.

Utilicen [el comando `RUN`](https://docs.docker.com/engine/reference/builder/#run)
para correr el comando `dotnet restore`. 

Cuando se corra el build de éste archivo, se descargaran las dependencias del
proyecto que estan definidas en el archivo `MvcMovie.csproj`, que copiamos en
el paso anterior.

Cuando hayan agregado ésto, respondan "¿Qué sigue?" :)
