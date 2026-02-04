Hemos elegido `mdbook` para generar nuestras páginas de Github. Lo que hace `mdbook` es generar un proyecto estático de HTML a partir de archivos `.md` que detallan el proyecto. Para ello, nuestro flujo de trabajo sigue la siguiente idea:

- Creamos un proyecto de `mdbook` con la estructura inicializada:

```
mdbook init docs
```

y añadimos los cambios a nuestro repositorio.

- Dentro de este proyecto, podemos modificar parámetros generales en `book.toml` y el contenido se estructura en los archivos `*.md`. En particular, `SUMMARY.md` incluye la ruta de todos los archivos que se incluyen.

- Para desplegar la página de forma automática en Github Pages, seguimos varios pasos. El primero consiste en crear una acción que invoque a `mdbook` para generar la página estática y que genere los cambios en la rama `gh-pages`.

- A continuación, vamos a la zona de `Settings`, `Pages` y configuramos `Build and deployment`. La opción que elegimos es `Deploy from a branch` y elegimos la rama de `gh-pages`. Si no se ha generado, vamos previamente a `Actions` y ejecutamos la acción que hemos creado anteriormente (está configurada para que se pueda invocar de forma manual).

- Por la forma en la que hemos configurado la acción, solo se hace re-deployment de la página si hacemos cambios dentro del folder `docs`.

