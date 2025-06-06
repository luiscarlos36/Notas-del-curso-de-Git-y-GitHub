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
