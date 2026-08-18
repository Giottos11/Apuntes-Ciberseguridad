# Git

**Git** es un sistema de **control de versiones distribuido**. Permite registrar los cambios realizados en un proyecto, consultar su historial, crear diferentes líneas de desarrollo y recuperar versiones anteriores.

Es una herramienta fundamental para trabajar con código, especialmente cuando un proyecto tiene muchos cambios o participan varias personas.

---

## 1. Configurar Git

La primera vez que utilizamos Git, debemos configurar nuestro nombre y correo electrónico. Esta información se asociará a los commits que realicemos.

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

Podemos comprobar la configuración actual con:

```bash
git config --list
```

---

## 2. Crear un repositorio

Para empezar a utilizar Git en una carpeta, primero nos situamos dentro de ella:

```bash
cd mi-proyecto
```

Después inicializamos el repositorio:

```bash
git init
```

Git creará una carpeta oculta llamada `.git`. Esta carpeta contiene toda la información necesaria para gestionar el historial del proyecto.

A partir de este momento, Git comenzará a controlar los cambios realizados en esa carpeta.

---

## 3. Comprobar el estado del repositorio

Uno de los comandos más importantes es:

```bash
git status
```

Muestra información sobre el estado actual del repositorio, por ejemplo:

* Archivos nuevos.
* Archivos modificados.
* Archivos preparados para un commit.
* La rama en la que estamos trabajando.

Es recomendable utilizar `git status` con frecuencia para saber qué está ocurriendo en nuestro repositorio.

---

## 4. Añadir archivos

Cuando modificamos o creamos archivos, Git detecta esos cambios, pero todavía no los incluye en el próximo commit.

Para preparar un archivo:

```bash
git add archivo.txt
```

También podemos preparar todos los archivos modificados:

```bash
git add .
```

Los archivos preparados pasan a la **staging area**, también llamada **área de preparación**.

Podemos imaginar el proceso de esta manera:

```text
Archivos modificados
        ↓
   git add
        ↓
  Staging area
        ↓
   git commit
        ↓
     Historial
```

---

## 5. Crear un commit

Un **commit** es una captura del estado del proyecto en un momento determinado.

Para crear uno:

```bash
git commit -m "Descripción de los cambios"
```

Por ejemplo:

```bash
git commit -m "Añadida función de autenticación"
```

Los mensajes de los commits deberían ser claros y describir brevemente qué hemos cambiado.

Podemos comprobar que el commit se ha creado utilizando:

```bash
git log
```

---

## 6. Consultar el historial

Para mostrar el historial completo:

```bash
git log
```

Puede resultar bastante largo, por lo que también podemos utilizar:

```bash
git log --oneline
```

Esto muestra cada commit en una sola línea:

```text
a1b2c3d Añadida autenticación
e4f5g6h Corregido error de validación
i7j8k9l Creado proyecto
```

La primera parte es el **identificador del commit**, conocido como hash o SHA.

---

## 7. Crear un alias para el historial

Git permite crear **alias**, que son nombres personalizados para comandos que utilizamos frecuentemente.

Podemos crear un alias llamado `tree`:

```bash
git config --global alias.tree "log --graph --decorate --all --oneline"
```

A partir de entonces podemos utilizar:

```bash
git tree
```

En lugar de escribir:

```bash
git log --graph --decorate --all --oneline
```

### ¿Qué significa cada opción?

```text
--graph
```

Muestra un **gráfico ASCII** que representa las diferentes ramas y sus relaciones.

```text
--decorate
```

Muestra información adicional asociada a los commits, como los nombres de las ramas y etiquetas.

```text
--all
```

Muestra los commits pertenecientes a **todas las ramas**, no solamente los de la rama actual.

```text
--oneline
```

Muestra cada commit en una sola línea para que el historial sea más fácil de leer.

Por ejemplo:

```text
* a1b2c3d Añadida autenticación
|\
| * e4f5g6h Corregido error
|/
* i7j8k9l Creado proyecto
```

Este comando es especialmente útil para obtener una **visión rápida de la evolución del proyecto**.

---

## 8. Crear ramas

Una **rama (branch)** permite trabajar en una línea de desarrollo independiente.

Para crear una rama:

```bash
git branch nueva-rama
```

Para ver las ramas existentes:

```bash
git branch
```

La rama actual aparecerá marcada con `*`.

Para cambiar de rama:

```bash
git switch nueva-rama
```

También podemos crear una rama y cambiar a ella directamente:

```bash
git switch -c nueva-rama
```

Por ejemplo:

```bash
git switch -c feature-login
```

Esto crea la rama `feature-login` y nos coloca automáticamente en ella.

---

## 9. Trabajar con ramas

Las ramas permiten desarrollar diferentes funcionalidades sin modificar directamente otra línea de desarrollo.

Por ejemplo:

```text
             feature-login
                   |
                   ↓
main ─────●────────●────────●
           \
            \
             ●────●
             feature-api
```

Podemos tener una rama principal:

```text
main
```

y crear otras ramas para funcionalidades concretas:

```text
feature-login
feature-api
fix-error
```

Cada rama puede avanzar de forma independiente.

---

## 10. Unir ramas con `merge`

Cuando terminamos el trabajo de una rama, podemos incorporar sus cambios a otra mediante `merge`.

Primero cambiamos a la rama que recibirá los cambios:

```bash
git switch main
```

Después ejecutamos:

```bash
git merge feature-login
```

Git intentará integrar los cambios de `feature-login` dentro de `main`.

El historial podría quedar así:

```text
*   abc1234 Merge branch 'feature-login'
|\
| * def5678 Añadido formulario de login
| * 123abcd Añadida validación
|/
* 456efgh Creado proyecto
```

---

## 11. Conflictos

A veces Git no puede combinar automáticamente los cambios de dos ramas. Esto ocurre cuando diferentes cambios afectan a las mismas partes de un archivo.

Git marcará entonces un **conflicto**.

Por ejemplo:

```text
<<<<<<< HEAD
print("Hola")
=======
print("Hello")
>>>>>>> feature
```

Tenemos que decidir qué versión queremos conservar y eliminar las marcas del conflicto.

Después:

```bash
git add archivo.py
```

y finalmente:

```bash
git commit
```

Los conflictos son una parte normal del trabajo con Git cuando diferentes líneas de desarrollo modifican las mismas partes del proyecto.

---

## 12. Deshacer cambios

Git permite recuperar o deshacer diferentes tipos de cambios.

### Descartar modificaciones de un archivo

Si hemos modificado un archivo pero todavía no hemos hecho `git add`:

```bash
git restore archivo.txt
```

Esto recupera la versión del archivo correspondiente al último commit.

### Quitar un archivo de la staging area

Si hemos utilizado:

```bash
git add archivo.txt
```

pero queremos quitarlo de la staging area:

```bash
git restore --staged archivo.txt
```

El archivo seguirá teniendo sus modificaciones, pero dejará de estar preparado para el commit.

---

## 13. Revertir un commit

Si queremos deshacer los efectos de un commit, podemos utilizar:

```bash
git revert ID_DEL_COMMIT
```

Por ejemplo:

```bash
git revert a1b2c3d
```

`git revert` crea un **nuevo commit** que invierte los cambios realizados por el commit indicado.

Esto es diferente de borrar el historial: el commit original continúa existiendo.

---

## 14. Comparar cambios

Git también permite comprobar exactamente qué ha cambiado.

Para ver modificaciones que todavía no hemos añadido a la staging area:

```bash
git diff
```

Para ver cambios que ya están en la staging area:

```bash
git diff --staged
```

Esto resulta muy útil antes de crear un commit para comprobar exactamente qué estamos a punto de guardar.

---

## 15. Ver información de un commit

Podemos consultar los detalles de un commit concreto:

```bash
git show ID_DEL_COMMIT
```

Por ejemplo:

```bash
git show a1b2c3d
```

Esto permite ver información del commit y los cambios que introdujo.

---

## 16. Etiquetas (`tag`)

Git permite crear **etiquetas** para identificar puntos importantes del historial.

Por ejemplo:

```bash
git tag v1.0
```

Podemos consultar las etiquetas existentes:

```bash
git tag
```

Las etiquetas son especialmente útiles para marcar versiones importantes del proyecto:

```text
v1.0
v1.1
v2.0
```

---

# Flujo básico de Git

Un flujo habitual cuando trabajamos con Git es:

```text
        Modificar archivos
                ↓
          git status
                ↓
             git add
                ↓
           git commit
                ↓
           git log/tree
```

Por ejemplo:

```bash
git status
git add .
git commit -m "Actualizados los archivos"
git tree
```

Si trabajamos con ramas:

```text
Crear rama
    ↓
Trabajar en ella
    ↓
Crear commits
    ↓
Volver a main
    ↓
Hacer merge
```

Por ejemplo:

```bash
git switch -c nueva-funcionalidad

# Trabajamos y modificamos archivos

git add .
git commit -m "Añadida nueva funcionalidad"

git switch main
git merge nueva-funcionalidad
```

---

# Comandos fundamentales

Como referencia rápida:

| Comando       | Función                                                        |
| ------------- | -------------------------------------------------------------- |
| `git init`    | Crear un repositorio                                           |
| `git status`  | Consultar el estado                                            |
| `git add`     | Añadir cambios a la staging area                               |
| `git commit`  | Guardar cambios en el historial                                |
| `git log`     | Ver el historial                                               |
| `git diff`    | Ver diferencias                                                |
| `git show`    | Ver los cambios de un commit                                   |
| `git branch`  | Gestionar ramas                                                |
| `git switch`  | Cambiar de rama                                                |
| `git merge`   | Unir ramas                                                     |
| `git restore` | Restaurar cambios                                              |
| `git revert`  | Crear un commit que deshace otro                               |
| `git tag`     | Crear etiquetas                                                |
| `git tree`    | Mostrar el historial de forma gráfica mediante el alias creado |

### Idea clave

Git se puede entender como un sistema que permite **guardar la evolución de un proyecto mediante commits**, organizar el trabajo mediante **ramas**, consultar las modificaciones y recuperar o revertir cambios cuando sea necesario.

El ciclo fundamental es:

```text
MODIFICAR
    ↓
git add
    ↓
STAGING AREA
    ↓
git commit
    ↓
HISTORIAL
    ↓
git log / git tree
```

**Git no solo sirve para guardar versiones: permite entender cómo ha evolucionado un proyecto y trabajar de forma organizada sobre diferentes líneas de desarrollo.**

