# 📝 Notas del Curso de Git y GitHub

## 📁 Comandos básicos de terminal

| Comando                         | Descripción                                                       |
| ------------------------------- | ----------------------------------------------------------------- |
| `cd <nombre_del_directorio>`    | Entra a un directorio.                                            |
| `cd ..`                         | Retrocede un nivel (una carpeta) en la estructura de directorios. |
| `ls`                            | Muestra los archivos y carpetas del directorio actual.            |
| `mkdir <nombre_del_directorio>` | Crea una nueva carpeta (directorio).                              |
| `rmdir <nombre_del_directorio>` | Elimina una carpeta vacía.                                        |

## 🔧 Comandos básicos de Git

| Comando                               | Descripción                                                                                                        |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| `git init`                            | Inicia un nuevo repositorio de Git en el directorio actual.                                                        |
| `git status`                          | Muestra el estado del repositorio: qué archivos han cambiado, cuáles están listos para hacer *commit*, etc.        |
| `git add <nombre_de_archivo>`         | Añade un archivo al área de *staging* (preparado para el commit). Para añadir todos los archivos, usar `git add .` |
| `git rm --cached <nombre_de_archivo>` | Quita un archivo del *staging* sin borrarlo del disco.                                                             |
| `git commit -m "mensaje del commit"`  | Guarda los cambios añadidos con un mensaje que describa qué se hizo.                                               |
| `git log`  | Muestra la bitácora de cambios realizados en el repositorio.                                               |

## 🗃️ Otros conceptos importantes

- **Repositorio (repo):** Es como una carpeta donde Git guarda el historial de cambios de tu proyecto.

- **Staging area:** Zona intermedia donde se preparan los archivos antes de hacer el commit.

- **Commit:** Acción de guardar un conjunto de cambios en el historial del repositorio.

- **Directorio raíz:** La carpeta principal del proyecto.

## 🌿 Comandos de ramas (branches)

En Git, una rama permite trabajar en una versión separada del proyecto sin afectar la rama principal (generalmente `main`).

| Comando                            | Descripción                                                                                |
| ---------------------------------- | ------------------------------------------------------------------------------------------ |
| `git branch`                       | Muestra una lista de las ramas existentes y marca con un asterisco (\*) la rama actual.    |
| `git branch <nombre_de_rama>`      | Crea una nueva rama sin cambiarte a ella.                                                  |
| `git checkout <nombre_de_rama>`    | Cambia a otra rama. **(Nota: obsoleto, se recomienda usar `git switch`)**                  |
| `git switch <nombre_de_rama>`      | Cambia a otra rama de forma más clara y moderna.                                           |
| `git checkout -b <nombre_de_rama>` | Crea una nueva rama **y** cambia a ella de inmediato.                                      |
| `git merge <nombre_de_rama>`       | Fusiona la rama indicada con la rama actual. Se usa comúnmente para unir cambios a `main`. |
| `git branch -d <nombre_de_rama>`   | Elimina una rama que ya fue fusionada. (`-d` es "delete")                                  |
| `git branch -D <nombre_de_rama>`   | Fuerza la eliminación de una rama, aunque no haya sido fusionada. Úsalo con precaución.    |

## ✅ Buenas prácticas

- Crear ramas para nuevas funciones o correcciones en lugar de trabajar directamente en main.
- Eliminar ramas que ya se fusionaron para mantener el repositorio limpio:
git branch -d <nombre_de_rama> o git branch -D <nombre_de_rama> si es necesario forzar.

## ♻️ Comandos para deshacer cambios

A veces es necesario retroceder en el historial de cambios, ya sea para corregir errores o limpiar el historial. Git ofrece herramientas para hacerlo de distintas formas, según lo que se quiera conservar o descartar.

### 🔄 git reset

Este comando mueve el puntero `HEAD` (la referencia al último commit actual) a un commit anterior. Puede afectar el área de preparación (*staging*) y/o el directorio de trabajo, según el modo que se use.

| Comando                             | Descripción                                                                                                                 |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| `git reset --soft <id_del_commit>`  | Mueve `HEAD` al commit indicado. Conserva los archivos en staging, listos para un nuevo commit.                             |
| `git reset --mixed <id_del_commit>` | Mueve `HEAD` y **quita los archivos del staging**, pero **mantiene los cambios en el directorio**. Es el modo por defecto.  |
| `git reset --hard <id_del_commit>`  | Mueve `HEAD` y **elimina todos los cambios**, tanto del staging como del directorio. ⚠️ ¡Irreversible si no se ha guardado! |

### 🔁 git revert

| Comando                      | Descripción                                                                                                       |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| `git revert <id_del_commit>` | Crea un nuevo commit que **revierte** (deshace) los cambios de un commit anterior, **sin eliminar el historial**. |


✅ Ideal para trabajar en equipo, ya que no borra historial ni altera commits anteriores.

## 🧩 Cuándo usar cada uno
- Usa `git reset` si estás trabajando solo y necesitas limpiar o rehacer cambios localmente.
- Usa `git revert` si ya hiciste push o estás trabajando con otras personas, para mantener el historial limpio y seguro.

## 🏷️ Tags vs. Checkout en Git

Tanto git tag como git checkout permiten interactuar con puntos específicos del historial de un proyecto, pero tienen propósitos diferentes.

### 🔖 git tag
Se usa para crear etiquetas en commits importantes, como versiones oficiales (v1.0, v2.0, etc.).

| Comando                                    | Descripción                                                                                                             |
| ------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
| `git tag -a <nombre_del_tag> -m "mensaje"` | Crea una etiqueta con un mensaje descriptivo en el commit actual (por ejemplo, `git tag -a v1.0 -m "Primera versión"`). |
| `git show <nombre_del_tag>`                | Muestra información detallada del tag, incluyendo el commit al que apunta.                                              |
| `git tag -d <nombre_del_tag>`              | Elimina un tag localmente.                                                                                              |

> 🧠 Las etiquetas son útiles para marcar versiones estables o hitos importantes del proyecto.

### 🔁 git checkout

Permite cambiar de rama o explorar un commit anterior sin alterar el historial. Esto te permite revisar el estado del proyecto en distintos momentos.

| Comando                          | Descripción                                                                   |
| -------------------------------- | ----------------------------------------------------------------------------- |
| `git checkout <nombre_de_rama>`  | Cambia a otra rama.                                                           |
| `git checkout <hash_del_commit>` | Permite ver el proyecto tal como estaba en ese commit (modo "detached HEAD"). |


> ⚠️ Cuando haces checkout de un commit directamente, estás en modo “detached HEAD”, lo que significa que no estás en ninguna rama activa. Si haces cambios aquí, asegúrate de crear una nueva rama con git switch -c <nueva_rama> si quieres conservarlos.

## ✅ Diferencias clave

| `git tag`                                 | `git checkout`                                                 |
| ----------------------------------------- | -------------------------------------------------------------- |
| Marca un commit específico con un nombre. | Cambia entre ramas o revisa commits anteriores.                |
| No cambia el estado del proyecto.         | Cambia el contenido del directorio de trabajo.                 |
| Se usa para marcar versiones.             | Se usa para explorar o trabajar en otros puntos del historial. |

## ⚔️ Conflictos y Resolución de Conflictos en Git

Los **conflictos** ocurren cuando Git no puede fusionar (*merge*) automáticamente los cambios entre dos ramas porque se han modificado las mismas líneas de un archivo, o archivos que entran en conflicto directo.

### 🧠 ¿Cuándo ocurren los conflictos?

- Al hacer `git merge <rama>` si hay cambios incompatibles entre ramas.
- Al hacer `git pull` si los cambios remotos entran en conflicto con los cambios locales.
- Al hacer `git rebase` si hay commits que se sobreponen a los locales.

### 🔧 Comandos útiles durante un conflicto

| Comando                                        | Descripción                                                                                                 |
| ---------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `git status`                                   | Muestra qué archivos están en conflicto.                                                                    |
| `git diff`                                     | Muestra las diferencias entre versiones durante el conflicto.                                               |
| `git restore --source=HEAD --staged <archivo>` | Quita el archivo del *staging* y lo restaura a su estado antes del merge.                                   |
| `git merge --abort`                            | Cancela el merge y vuelve al estado anterior. Solo funciona si aún no se han resuelto todos los conflictos. |

## ✅ Buenas prácticas

- **Haz commits frecuentes**, así es más fácil encontrar el origen de un conflicto.
- **Antes de fusionar una rama, actualízala con** `git pull` para minimizar posibles conflictos.
- **Comunica con tu equipo** si hay muchos cambios sobre los mismos archivos.

## 🛠 ¿Qué es cada cosa?

| Término     | Descripción                                                                 |
|-------------|------------------------------------------------------------------------------|
| **Git**     | Sistema de control de versiones para llevar un historial de cambios en archivos. |
| **GitHub**  | Plataforma online para almacenar repositorios Git y colaborar con otros.       |
| **Git Bash**| Terminal que permite ejecutar comandos de Git en Windows.                      |

---

## 🔀 Conceptos Básicos

### 🧾 ¿Por qué usar ramas?

- Trabajar en **ramas separadas** (como `feature`, `fix`, etc.) evita romper el código que ya funciona.
- Se usa el comando para crear y cambiar a una nueva rama:
  ```bash
  git checkout -b nombre-de-rama
  ```

### 📤 ¿Cómo subir los cambios?

1. Guarda los cambios localmente:
   ```bash
   git add .
   git commit -m "Descripción de los cambios"
   ```
2. Súbelos a GitHub:
   ```bash
   git push origin nombre-de-rama
   ```

---

## 🔍 Revisión de Código (Code Review)

- Cuando terminas una funcionalidad, haces un **Pull Request** desde tu rama (`feature/xyz`) hacia la rama principal (`main` o `master`).
- Antes de hacer el merge (unir ramas), otro miembro del equipo debe revisar tu código.
- ✅ **Regla de oro:**  
  **“No hagas Pull Request si no te han hecho Code Review”** 😉

---

## 🧩 Flujo de trabajo recomendado

1. Crea una nueva rama:  
   ```bash
   git checkout -b feature/nombre
   ```
2. Trabaja en tus cambios.
3. Haz commits regularmente.
4. Sube tu rama a GitHub:  
   ```bash
   git push origin feature/nombre
   ```
5. Abre un Pull Request.
6. Espera el Code Review.
7. Si es aprobado, haz **merge** a `main`.

Este flujo ayuda a:

- Mantener el código limpio y estable.
- Trabajar en equipo sin pisarse los cambios.
- Detectar errores antes de que lleguen a producción.


## 🚀 Subir proyecto local a repositorio vacío con rama de desarrollo

1. Inicializa Git en tu carpeta local (si aún no lo hiciste):

    ```bash
    git init
    ```

2. Conecta tu repositorio local con el remoto (cambia la URL por la de tu repo):

    ```bash
    git remote add origin https://github.com/tu-usuario/tu-repo.git
    ```

3. Crea y cambia a una rama de desarrollo, por ejemplo `develop`:

    ```bash
    git checkout -b develop
    ```

4. Agrega todos los archivos y haz tu primer commit:

    ```bash
    git add .
    git commit -m "Primer commit en rama develop"
    ```

5. Sube la rama `develop` al repositorio remoto:

    ```bash
    git push -u origin develop
    ```

6. Ve a GitHub y crea un Pull Request para fusionar `develop` en `main`.

    > Nota: Si tu repo remoto está vacío y no tiene `main` creado aún, crea la rama `main` localmente y súbela:

    ```bash
    git checkout -b main
    git push -u origin main
    ```

7. Después de revisar el PR, haz el merge desde GitHub.

8. Una vez hecho el merge, borra la rama `develop` del remoto:

    ```bash
    git push origin --delete develop
    ```

9. Y borra la rama `develop` local:

    ```bash
    git branch -d develop
    ```

---

## ⚠️ Cambiar rama principal en GitHub para borrar `develop`

Si tu rama principal quedó como `develop` y quieres que sea `main`, sigue estos pasos:

1. Crea la rama `main` localmente (si no existe):

    ```bash
    git checkout -b main
    ```

2. Súbela al remoto:

    ```bash
    git push -u origin main
    ```

3. En GitHub:

    - Ve a **Settings** (Configuración) del repositorio.
    - Selecciona **Branches** en el menú lateral.
    - Cambia la **Default branch** de `develop` a `main`.
    - Guarda los cambios.

4. Ahora puedes borrar la rama `develop` remota:

    ```bash
    git push origin --delete develop
    ```

5. Y la rama `develop` local:

    ```bash
    git branch -d develop
    ```

---

Este flujo garantiza que tu rama principal sea `main` y que uses una rama de desarrollo para organizar tus cambios antes de hacer merge.

## 🔐 Configurar SSH para GitHub

Sigue estos pasos para configurar una conexión SSH segura con GitHub:

1. **Genera una clave SSH:**

    - Abre tu terminal.
    - Ejecuta el siguiente comando y sigue las instrucciones para crear la clave:
      ```bash
      ssh-keygen -t ed25519 -C "tu_correo@example.com"
      ```

2. **Inicia el agente SSH:**

    ```bash
    eval "$(ssh-agent -s)"
    ```

    Luego agrega tu clave privada:

    ```bash
    ssh-add ~/.ssh/id_ed25519
    ```

3. **Copia la clave pública:**

    ```bash
    cat ~/.ssh/id_ed25519.pub
    ```

    Copia el resultado que se muestra en pantalla.

4. **Añade la clave a GitHub:**

    - Ve a GitHub.
    - Entra a **Settings** > **SSH and GPG keys**.
    - Haz clic en **New SSH key**.
    - Pega tu clave pública copiada y guarda.

5. **Prueba la conexión:**

    ```bash
    ssh -T git@github.com
    ```

    Deberías ver un mensaje de éxito confirmando la conexión.

---

Con esto, habrás configurado SSH para GitHub de forma segura y eficiente.

## 🍴 Forks y ⭐ Stars en GitHub

### ¿Qué es un **fork**?

Un **fork** 🥢 es una copia de un repositorio que se guarda en tu cuenta de GitHub. Es útil cuando:

- Quieres contribuir a un proyecto pero **no tienes permisos** de escritura en el repositorio original.
- Quieres probar cambios sin afectar el código original.

Con un fork puedes:

- Hacer tus propias modificaciones.
- Crear ramas.
- Subir cambios.
- Luego, enviar un **Pull Request** al repositorio original para proponer tus cambios.

---

### ¿Qué es una **star**?

Una **star** ⭐ es como marcar un repositorio como favorito. Sirve para:

- Guardar proyectos que te gustan o quieres revisar después.
- Seguir repositorios que consideras interesantes.
- Mostrar apoyo a los proyectos de otros desarrolladores.

No tiene impacto en el código, pero sí ayuda a descubrir y destacar proyectos populares.

---

📌 En resumen:

| Acción   | ¿Qué hace?                                                                 |
|----------|------------------------------------------------------------------------------|
| **Fork** | Crea una copia del repositorio en tu cuenta para modificarlo libremente.   |
| **Star** | Marca un repositorio como favorito para seguirlo o guardarlo.              |


# 🚀 Comandos Git esenciales

| Comando    | Descripción breve                                | Uso típico                                 |
|------------|-------------------------------------------------|-------------------------------------------|
| `git pull` | Trae cambios del repositorio remoto y los fusiona automáticamente en tu rama actual. | Actualizar tu rama local con los últimos cambios remotos en un solo paso. |
| `git push` | Envía tus commits locales a un repositorio remoto. | Subir tus cambios para compartirlos o respaldarlos en el servidor remoto. |
| `git fetch`| Descarga los últimos cambios del remoto sin fusionarlos. | Obtener los cambios remotos para revisarlos antes de integrarlos manualmente. |
| `git merge`| Fusiona otra rama en la rama actual. | Combinar los cambios descargados o de otra rama en tu rama activa. |

---

## ⚡ Explicación rápida

- **git pull** = `git fetch` + `git merge` automático.  
- **git fetch** solo descarga actualizaciones, no las aplica.  
- Para integrar cambios después de un fetch, se usa **git merge** manualmente.  
- **git push** es para subir tus cambios locales al remoto.

---

## 💻 Ejemplos

```bash
# Actualizar tu rama actual con los últimos cambios remotos
git pull origin main

# Subir tus commits locales a la rama main del remoto
git push origin main

# Descargar actualizaciones del remoto sin fusionar
git fetch origin

# Fusionar la rama remota descargada con tu rama local
git merge origin/main
```

# 🐞 Issues y 💬 Discussions en GitHub

| Concepto       | Descripción                                    | Uso común                                   |
|----------------|------------------------------------------------|---------------------------------------------|
| **Issues**     | Espacio para reportar bugs, pedir mejoras o tareas concretas. | Registrar y seguir problemas o solicitudes específicas del proyecto. |
| **Discussions**| Foro para debates más abiertos, preguntas o intercambio de ideas. | Conversaciones generales que no necesariamente son problemas o tareas. |

---

# 📋 Plantillas de Issues

Las **plantillas de issues** ayudan a estandarizar la información que los colaboradores deben proporcionar al crear un nuevo issue, facilitando su gestión y resolución.

## ¿Cómo funcionan?

- Se crean archivos `.md` dentro de la carpeta `.github/ISSUE_TEMPLATE/` en el repositorio.  
- Al abrir un nuevo issue, GitHub mostrará estas plantillas para que el usuario elija y complete.  

## Ejemplo básico de plantilla para reporte de bugs:

```markdown
---
name: Reporte de Bug
about: Reporta un problema que encontraste
title: "[Bug]"
labels: bug
assignees: ''

---

**Describe el problema**
Una descripción clara y concisa del bug.

**Pasos para reproducirlo**
1. Paso uno
2. Paso dos
3. ...

**Comportamiento esperado**
Qué esperabas que pasara.

**Capturas de pantalla**
Si aplica, añade imágenes para ayudar a explicar el problema.

**Información adicional**
Otros detalles o contexto.
```

# 🔀 Pull Requests (PR)

Un **Pull Request** es una solicitud para que los cambios realizados en una rama (branch) sean revisados y eventualmente fusionados (merge) a otra rama, típicamente la rama principal (`main` o `master`). Los pull requests son muy útiles en equipos porque permiten revisar código, discutir cambios y mantener la calidad antes de integrar nuevas funcionalidades.

| Concepto        | Descripción                                                                                  |
|-----------------|----------------------------------------------------------------------------------------------|
| ¿Qué es?        | Solicitud para fusionar cambios de una rama a otra.                                         |
| ¿Para qué?      | Revisar, discutir y aprobar cambios antes de integrarlos al código principal.               |
| Flujo típico    | 1. Crear rama → 2. Hacer commits → 3. Abrir Pull Request → 4. Revisión y discusión → 5. Merge |
| Beneficios      | Facilita la colaboración, evita errores, mejora calidad y mantiene historial claro.         |
| Herramientas    | GitHub, GitLab, Bitbucket, etc., que ofrecen interfaces visuales para gestionar PRs.        |

---

## 📝 Otras notas útiles

- Puedes combinar `git add` y `git commit` con el comando:
  
  ```bash
  git commit -am "mensaje commit"

> Esto añade y comitea archivos que ya están siendo seguidos por Git (tracked).

Cuando borras una rama en GitHub, solo se elimina del repositorio remoto. La rama local sigue existiendo hasta que la eliminas manualmente en tu entorno local. Para borrar la rama local, usa:

```bash
git branch -d nombre-de-la-rama
```

---

## 📝 Documentación con GitHub

### 1. 🧾 Uso de Markdown para documentación

Markdown es un lenguaje de marcado ligero que permite escribir texto con formato de forma sencilla y legible. GitHub lo utiliza para mostrar archivos `.md` como páginas bien formateadas, lo que lo hace ideal para documentación de proyectos.

**✨ Ventajas de usar Markdown:**
- ✅ Es fácil de escribir y leer en texto plano.
- ✅ Permite estructurar contenido con títulos, listas, tablas, enlaces, imágenes, código, etc.
- ✅ Se renderiza automáticamente en GitHub.

**📌 Ejemplo básico de Markdown:**

```markdown
# Título grande
## Título mediano
### Título pequeño

**Texto en negrita**  
*Texto en cursiva*

- Lista
- Con
- Viñetas

[Enlace a GitHub](https://github.com)

```python
# Bloque de código
print("Hola mundo")
```


---

### 2. 📚 Uso de Wikis

GitHub Wikis permiten crear documentación más extensa y estructurada fuera del `README.md`, en forma de páginas interconectadas. Es útil cuando necesitas una guía del proyecto, manual de usuario o especificaciones técnicas más detalladas.

**📖 Ventajas de usar Wikis:**
- 🧩 Ideal para documentación extensa que se puede organizar en secciones.
- 🛠️ Se edita con Markdown (o también con un editor visual).
- 🕓 Cada página del Wiki tiene su propio historial de cambios.

**📂 Ejemplo de estructura de Wiki:**

Inicio

├── Introducción

├── Instalación

├── Uso

└── Preguntas frecuentes (FAQ)


**🛎️ Para activar el Wiki:**  
En tu repositorio, ve a la pestaña "Wiki" y haz clic en "Create the first page".

---

### 3. 📄 Uso de GitHub Gist

GitHub Gist es una herramienta para compartir fragmentos de código, notas o archivos de manera rápida. Puede ser público o privado, y cada Gist tiene su propia URL.

**🔍 Usos comunes:**
- 🧪 Compartir código con otros sin crear un repositorio completo.
- 💾 Guardar configuraciones o comandos que se usan frecuentemente.
- 📤 Crear ejemplos reproducibles para foros o tutoriales.

**🚀 Ventajas de los Gists:**
- 📝 Soportan Markdown y resaltado de sintaxis para muchos lenguajes.
- 📁 Pueden tener múltiples archivos.
- 🔁 Puedes clonarlos como repositorios de Git.

**💡 Ejemplo de Gist en Markdown:**
```markdown
### Comando útil de Git

```bash
git log --oneline --graph --all
```

Este comando muestra un historial visual de commits en forma de árbol.


🔗 Puedes crear un Gist desde: [https://gist.github.com](https://gist.github.com)

---


# 🌐 GitHub Codespaces

**GitHub Codespaces** es una herramienta que permite crear entornos de desarrollo en la nube, directamente integrados con GitHub.

### 🚀 Ventajas principales

| Ventaja           | Descripción                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| ⚙️ Configuración rápida | Puedes crear entornos listos para usar con un solo clic. Ahorra mucho tiempo.  |
| 🌍 Accesibilidad       | Accede a tu entorno desde cualquier dispositivo con internet.              |
| 🤝 Colaboración        | Trabaja en equipo en tiempo real, ideal para proyectos compartidos.       |
| 🔗 Integración         | Funciona muy bien con otras herramientas de GitHub (pull requests, issues).|
| 🎨 Personalización     | Puedes instalar extensiones y adaptar el entorno a tu gusto.              |

GitHub Codespaces mejora la **productividad** y simplifica el **flujo de trabajo**, permitiéndote enfocarte más en programar y menos en configurar.

## 👥 Programación Colaborativa con Live Share

**Live Share** es una extensión de Visual Studio Code que permite colaborar en tiempo real con otros desarrolladores, como si estuvieran en la misma computadora.

### 🔧 ¿Qué permite hacer Live Share?

| Función                   | Descripción                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| ✍️ Edición colaborativa   | Todos los participantes pueden escribir y editar el mismo código en tiempo real. |
| 🧭 Navegación independiente | Cada persona puede moverse por el proyecto sin afectar a los demás.         |
| 🛠️ Compartir terminal     | Puedes compartir la terminal para ejecutar comandos y ver resultados juntos. |
| 🐞 Depuración conjunta     | Permite depurar el código colaborativamente, viendo los puntos de interrupción y valores. |
| 🔒 Acceso controlado       | Puedes decidir qué archivos o funciones compartir, manteniendo el control.  |

### ✅ Ventajas principales

- No necesitas clonar el repositorio: el anfitrión comparte su entorno.
- Facilita revisiones de código, mentorías o pair programming.
- Ahorra tiempo y mejora la comunicación entre el equipo.

Con **Live Share**, trabajar en equipo es más fácil y dinámico. Es como estar programando lado a lado, sin importar en qué parte del mundo estés.


## ✏️ Uso del Editor Web de GitHub para Edición Rápida de Archivos

GitHub permite editar archivos directamente desde el navegador, sin necesidad de clonar el repositorio ni usar herramientas externas.

### ⚡ ¿Cómo acceder al editor web?

- Estando en un repositorio, presiona la tecla `.` (punto) en tu teclado.
- O cambia la URL de `github.com` a `github.dev`.

👉 Esto abrirá una versión web de **Visual Studio Code** en tu navegador.

### 🔧 ¿Qué se puede hacer?

| Acción                    | Descripción                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| 📝 Editar archivos        | Puedes hacer cambios rápidos en cualquier archivo del repositorio.          |
| ➕ Crear/Eliminar archivos | Agrega nuevos archivos o elimina los que ya no necesitas.                   |
| 🔄 Commit directo         | Guarda los cambios con un mensaje de commit, sin salir del navegador.       |
| 📂 Navegar el proyecto    | Explora carpetas y archivos fácilmente como en un editor de escritorio.     |
| 🔌 Instalar extensiones   | Puedes añadir extensiones básicas compatibles con el editor web.            |

### ✅ Ventajas

- Ideal para hacer **cambios rápidos** sin configurar nada.
- Funciona en cualquier lugar con acceso a internet.
- Útil para correcciones pequeñas, edición de documentación o revisión de código.

El **editor web de GitHub** es una forma rápida y sencilla de modificar tu código sin salir del navegador. Perfecto para tareas ligeras o ediciones rápidas.


## 🆚 Diferencias entre GitHub Codespaces y el Editor Web

| Característica       | GitHub Codespaces                        | Editor Web de GitHub (`github.dev`)       |
|----------------------|------------------------------------------|--------------------------------------------|
| 💻 Potencia           | Entorno completo con backend (como VS Code en la nube) | Editor ligero solo para cambios rápidos     |
| ⚙️ Personalización    | Soporta extensiones, terminal, depuración, configuraciones personalizadas | Limitado a ediciones básicas               |
| 📦 Dependencias       | Puede instalar y ejecutar dependencias del proyecto | No ejecuta código ni instala paquetes       |
| 🧪 Terminal y Debug   | Sí, como un entorno local                 | No disponible                               |
| 🕐 Uso recomendado    | Desarrollo completo, proyectos grandes    | Ediciones rápidas, documentación, hotfixes |

### 💡 En resumen

- **Codespaces** = editor completo y potente.
- **Editor Web** = editor rápido y liviano para cambios simples.

## 🔐 Gestión de GitHub Tokens para Acceso Seguro a Repositorios

GitHub usa **tokens personales de acceso (PAT)** en lugar de contraseñas para acceder a tu cuenta o repositorios de forma segura desde herramientas externas (como Git, VS Code o GitHub CLI).

### 🧩 ¿Qué es un Personal Access Token (PAT)?

Un **token** es como una contraseña temporal y controlada que puedes generar para:

- Clonar repositorios privados
- Hacer push/pull desde Git
- Usar la GitHub CLI o integraciones

### 🛠️ ¿Cómo se crea un token?

1. Ve a: `Settings` > `Developer settings` > `Personal access tokens`.
2. Haz clic en **"Generate new token"**.
3. Selecciona los **permisos necesarios** (repos, workflow, etc.).
4. Copia el token y guárdalo en un lugar seguro (¡solo se muestra una vez!).

### 🔐 Buenas prácticas

| Práctica                      | Por qué es importante                        |
|-------------------------------|----------------------------------------------|
| ✅ Dar solo permisos necesarios | Menos riesgo si se filtra el token           |
| 📆 Establecer expiración       | Mejora la seguridad con tokens temporales    |
| 🔑 Usar tokens diferentes      | Un token por herramienta o proyecto          |
| ❌ Revocar tokens no usados    | Elimina tokens antiguos o sin uso            |

### 💡 En resumen

Los tokens hacen más **seguro** el acceso a tus repos desde otras herramientas. Son fáciles de generar y debes usarlos en lugar de tu contraseña personal.

## 🛡️ Mitigación de Brechas de Seguridad en Repositorios GitHub

GitHub ofrece varias herramientas y buenas prácticas para **proteger el código y evitar filtraciones** o ataques.

### 🔧 Herramientas y funciones de seguridad

| Función                      | ¿Para qué sirve?                                                           |
|------------------------------|-----------------------------------------------------------------------------|
| 🧪 GitHub Actions: Secret Scanning | Detecta si subiste accidentalmente claves o tokens al repo                |
| 🔍 Dependabot Alerts          | Te avisa si tus dependencias tienen vulnerabilidades                       |
| 🧬 Code Scanning              | Analiza tu código en busca de errores de seguridad                         |
| 🔐 Branch Protection Rules    | Evita cambios directos a ramas importantes (como `main`) sin revisión      |
| 📜 Audit Log                  | Registro de actividades para detectar comportamientos sospechosos          |

### ✅ Buenas prácticas para evitar brechas

- **Nunca subas claves o contraseñas** al repositorio.
- Usa **.gitignore** para evitar subir archivos sensibles.
- Revisa y acepta los **pull requests** antes de fusionarlos.
- Configura **2FA (doble factor de autenticación)** en tu cuenta.
- Usa **GitHub Secrets** para almacenar tokens y claves en GitHub Actions.

### 💡 En resumen

Proteger un repositorio no solo depende del código, sino también de usar las herramientas correctas y mantener buenas prácticas de seguridad en el equipo.

## 📦 Gestión de Seguridad de Paquetes con Dependabot en Proyectos .NET

**Dependabot** es una herramienta integrada en GitHub que ayuda a mantener actualizadas las dependencias de tu proyecto, especialmente para prevenir vulnerabilidades.

### 🔄 ¿Qué hace Dependabot?

| Función                      | Descripción                                                                 |
|------------------------------|-----------------------------------------------------------------------------|
| 🔔 Alertas de seguridad      | Te avisa cuando una dependencia tiene vulnerabilidades conocidas.           |
| 📬 Pull requests automáticas | Crea PRs para actualizar paquetes a versiones seguras.                      |
| 🔍 Monitoreo constante       | Revisa los archivos como `*.csproj` o `packages.config` en proyectos .NET. |

### ⚙️ Cómo activar Dependabot en un proyecto .NET

1. Asegúrate de tener un archivo `.github/dependabot.yml`.
2. Configura el archivo para que revise tus dependencias `.NET`:
```yaml
version: 2
updates:
  - package-ecosystem: "nuget"
    directory: "/"
    schedule:
      interval: "weekly"
```

3. GitHub comenzará a escanear y sugerir actualizaciones automáticamente.

### ✅ Ventajas para proyectos .NET
- Evita usar librerías obsoletas o inseguras.
- Ahorra tiempo al automatizar actualizaciones.
- Mantiene tu proyecto más estable y seguro con poco esfuerzo.

### 💡 En resumen

Dependabot es una herramienta esencial para mantener tus proyectos .NET seguros y actualizados, sin necesidad de hacerlo manualmente.

## 🔒 Configuración de Repositorios Privados en GitHub (y uso de `.gitignore`)

### 🔐 ¿Qué es un repositorio privado?

Un **repositorio privado** es un proyecto en GitHub que **solo tú y tus colaboradores autorizados pueden ver y modificar**. Ideal para proyectos personales, comerciales o que aún no están listos para hacerse públicos.

### ⚙️ ¿Cómo hacerlo privado?

1. Al crear el repositorio, selecciona la opción **"Private"**.
2. Si ya existe, ve a:  
   `Settings > Danger Zone > Change repository visibility`.
3. Solo tú o quienes invites podrán acceder.

### 👥 Control de acceso

- Puedes **invitar colaboradores** específicos desde la pestaña `Settings > Collaborators`.
- También puedes crear equipos y usar **GitHub Organizations** para una gestión más avanzada.

---

## 📄 Uso de `.gitignore`

El archivo `.gitignore` le dice a Git **qué archivos o carpetas no debe rastrear** (ni subir al repositorio).

### 🧱 Ejemplos comunes para proyectos .NET:

```gitignore
bin/
obj/
*.user
*.suo
*.vs/
.env
```

## ✅ ¿Por qué usar .gitignore?

| Motivo                          | Beneficio                                                               |
| ------------------------------- | ----------------------------------------------------------------------- |
| 🚫 Evitar archivos innecesarios | No subes archivos de compilación, temporales o personales.              |
| 🔐 Proteger información         | Evita subir archivos con claves, contraseñas o configuraciones locales. |
| 🧹 Mantener limpio el repo      | Facilita el trabajo en equipo con un historial más claro y limpio.      |


## 💡 En resumen
- Los repos privados protegen tu código de miradas externas.
- El archivo .gitignore te ayuda a mantener tu repo limpio, seguro y profesional.

