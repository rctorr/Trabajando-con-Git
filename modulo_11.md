![github](media/modulo_08/distribuido-vcs.png)

## Módulo 12: Pull Requests (Merge Requests) - ¡Colaboración Fluida en la Nube!

* Introducción a pull requests y su uso en servicios de hosting.
* Creación, revisión y fusión de pull requests.
* Limpieza y sincronización de repositorios.

Este módulo te introduce a las *pull requests* (o *merge requests*), una herramienta fundamental para la colaboración en proyectos de Git alojados en servicios como GitHub, GitLab o Bitbucket. Aprenderás a crearlas, revisarlas, fusionarlas y, finalmente, a mantener tus repositorios sincronizados y limpios.

### 12.1 Introducción a Pull Requests y su Uso en Servicios de Hosting: ¡El Puente de la Colaboración!

Las *pull requests* son una característica de los servicios de hosting de Git (como GitHub, GitLab y Bitbucket), no de Git en sí.  Permiten compartir tu trabajo con otros desarrolladores de forma organizada y eficiente.  En esencia, una *pull request* es una propuesta para integrar los cambios de una rama (rama de origen) en otra (rama de destino), normalmente `master`.

**¿Por qué usar *pull requests*?**

* **Revisión de código:** Facilita la revisión del código por parte de otros desarrolladores antes de integrarlo en la rama principal.
* **Colaboración:**  Promueve la comunicación y la retroalimentación entre los miembros del equipo.
* **Historial limpio:** Ayuda a mantener un historial de commits organizado y rastreable.
* **Integración remota:** Permite integrar cambios de forma remota, sin necesidad de clonar el repositorio.

En la práctica, una *pull request* fluye de la siguiente manera:


1. Se crea una rama local con los cambios.
2. Se envían los cambios al repositorio remoto (creando una rama remota).
3. Se crea una *pull request* en el servicio de hosting.
4. Se revisa la *pull request*, se proporciona retroalimentación y se realizan los ajustes necesarios.
5. Se aprueba la *pull request*.
6. Se fusiona la rama en el repositorio remoto (normalmente `master`).
7. Se limpia el repositorio eliminando la rama de origen y la rama de seguimiento remoto.


**Desarrollo**

**Paso 0: Preparación:** Asegúrate de tener tu repositorio local `web-prj` sincronizado con el repositorio remoto `web-prj-remoto`. Debes tener al menos una rama adicional además de `master` (ej. `temario`).


**Paso 1: Creando un nuevo repositorio en GitHub (si no lo tienes):**  En la página principal de GitHub, haz clic en el botón "+", luego en "New repository".  Dale un nombre (ej., "mi-repositorio-remoto"), asegúrate de que sea privado y haz clic en "Create repository". Copia la URL HTTPS del repositorio.


**Paso 2: Conectando el repositorio local al remoto:**  En tu terminal (en el directorio `web-prj`):

```bash
git remote add origin <URL_del_repositorio_remoto>
```

Reemplaza `<URL_del_repositorio_remoto>` con la URL que copiaste en el paso anterior.


**Paso 3: Creando una nueva rama para la *pull request*:** En tu repositorio `web-prj`:

```bash
git checkout -b nueva-caracteristica
```

Esta línea crea la rama `nueva-caracteristica` y te sitúa en ella.


**Paso 4: Realizar cambios y commit en la nueva rama:** Añade algunas modificaciones a un archivo de tu repositorio (ej., añade un nuevo color a `coloresarcoiris.txt`).  Haz `git add`, `git commit -m "Mensaje descriptivo"`.


**Paso 5: Enviar la nueva rama al repositorio remoto:**

```bash
git push -u origin nueva-caracteristica
```

(`-u` establece el seguimiento *upstream*).


### 12.2 Creación, Revisión y Fusión de Pull Requests: ¡El Flujo de Colaboración!

 Una vez que has enviado tu rama al repositorio remoto, crearás una *pull request* a través de la interfaz web de tu servicio de hosting (GitHub, GitLab o Bitbucket).  En esencia, estás solicitando que tus cambios se fusionen en la rama `master`. El servicio de hosting suele proporcionar una interfaz para la revisión del código, la adición de comentarios y la aprobación de la *pull request*.  Después de la aprobación, un administrador o colaborador fusionará la *pull request* en la rama `master`.


**Desarrollo**

**Paso 1: Crear la *pull request* en GitHub:**
1. Ve a tu repositorio `mi-repositorio-remoto` en GitHub.
2. Haz clic en el botón "New pull request".
3. Selecciona la rama `master` como rama base y la rama `nueva-caracteristica` como rama de comparación.
4. Escribe un título descriptivo para tu *pull request* (ej., "Añadiendo nuevos colores").  Puedes añadir una descripción opcional.
5. Haz clic en "Create pull request".


**Paso 2: Revisar la *pull request*:**  Simula la revisión.  Puedes añadir comentarios si fuera necesario, indicando posibles mejoras o correcciones.


**Paso 3: Aprobar la *pull request*:**  En la interfaz web de GitHub, haz clic en el botón para aprobar la *pull request*.  (Si utilizas otro servicio de hosting, los pasos serán ligeramente diferentes; consulta su documentación).


**Paso 4: Fusionar la *pull request*:**  En la interfaz web de GitHub, haz clic en el botón para fusionar la *pull request*.  GitHub normalmente realiza una fusión no *fast-forward*, incluso si el historial es lineal, creando un nuevo commit de fusión.


### 12.3 Limpieza y Sincronización de Repositorios: ¡Un Final Impecable!

Después de fusionar una *pull request*, es buena práctica eliminar la rama de origen local y la rama remota para mantener tu repositorio limpio y organizado.  Usualmente, esto solo se hace con ramas de características o ramas de tema.


**Desarrollo**

**Paso 1: Eliminar la rama local (`git branch -d`):**  En tu terminal:

```bash
git branch -d nueva-caracteristica
```


**Paso 2: Eliminar la rama remota (`git push origin --delete nueva-caracteristica`):** Para eliminar la rama remota, ejecuta:

```bash
git push origin --delete nueva-caracteristica
```


**Paso 3:  Verificar el estado del repositorio remoto:**  Actualiza la página de tu repositorio en GitHub para verificar que la rama `nueva-caracteristica` ya no existe.


**Paso 4:  Sincronización final (`git pull origin master`):**  Para asegurarte de que tu repositorio local está completamente sincronizado con el repositorio remoto, realiza un `pull` de la rama `master`:

```bash
git pull origin master
```

Si no hay divergencias, debería ser una fusión *fast-forward*.


**Paso 5: Verificar el estado final del repositorio local (`git log --graph --oneline --decorate`):** Utiliza este comando para confirmar que tu rama `master` está actualizada y que el historial es limpio y lineal.



Este módulo te ha dado una visión completa del proceso de *pull requests*, desde la creación hasta la limpieza final. ¡Recuerda que las *pull requests* son tu aliada para la colaboración fluida y eficiente en Git!  Practica regularmente para dominar esta herramienta esencial para el desarrollo colaborativo de software.

