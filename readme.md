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

