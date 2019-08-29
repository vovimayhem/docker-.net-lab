Ahora necesitamos ligar el servicio `web` con el servicio `postgres`.

Para éso ocuparemos hacer 2 cosas:

- Agregar la [lista de `depends_on`](https://docs.docker.com/compose/compose-file/#depends_on), con `postgres` para que cuando se levante el proceso `web`, automáticamente levante también el proceso `postgres`.

- Agregar la [lista de `environment`](https://docs.docker.com/compose/compose-file/#environment) de la app `web`, con la variable de entorno `DATABASE_URL: postgres://postgres:3x4mpl3P455@postgres:5432/demo_development`, que es la configuración que usará la app para conectarse a la base de datos.

Respondan "OK" para continuar con la configuracion de puertos para la app `web`.