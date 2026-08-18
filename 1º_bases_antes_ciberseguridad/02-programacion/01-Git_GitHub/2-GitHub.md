# GitHub

**GitHub** es una plataforma basada en Git que permite **almacenar repositorios en Internet, colaborar con otras personas y gestionar proyectos de software**.

Una diferencia importante es:

* **Git** → herramienta de control de versiones que utilizamos en nuestro ordenador.
* **GitHub** → plataforma online que permite alojar repositorios Git y trabajar con ellos de forma colaborativa.

Por ejemplo:

```text
              GIT
       ┌─────────────────┐
       │ Repositorio     │
       │ local           │
       └────────┬────────┘
                │
             push/pull
                │
                ↓
       ┌─────────────────┐
       │    GitHub       │
       │ Repositorio     │
       │ remoto          │
       └─────────────────┘
```

---

## 1. Crear un repositorio en GitHub

Para empezar, creamos un repositorio desde GitHub.

Un repositorio puede contener:

* Código fuente.
* Archivos de configuración.
* Documentación.
* Un archivo `README`.
* Historial de cambios.
* Ramas.
* Issues.
* Pull requests.

Al crear el repositorio podemos darle un nombre, por ejemplo:

```text
mi-proyecto
```

Después tendremos un repositorio remoto asociado a nuestro proyecto.

---

## 2. Conectar Git con GitHub

Si ya tenemos un repositorio Git en nuestro ordenador, podemos conectarlo con el repositorio de GitHub.

Primero añadimos el repositorio remoto:

```bash
git remote add origin URL_DEL_REPOSITORIO
```

Podemos comprobar que se ha añadido correctamente:

```bash
git remote -v
```

Normalmente veremos algo parecido a:

```text
origin  URL_DEL_REPOSITORIO (fetch)
origin  URL_DEL_REPOSITORIO (push)
```

### ¿Qué significa `origin`?

`origin` es simplemente el **nombre que Git utiliza habitualmente para identificar el repositorio remoto principal**.

No es obligatorio llamarlo `origin`, pero es la convención más utilizada.

---

## 3. Subir cambios con `git push`

Una vez que tenemos commits en nuestro repositorio local, podemos enviarlos al repositorio remoto:

```bash
git push origin main
```

Aquí:

```text
git push
```

significa **enviar cambios al repositorio remoto**.

```text
origin
```

indica el repositorio remoto.

```text
main
```

indica la rama que queremos enviar.

El flujo sería:

```text
Ordenador
    │
    │ git push
    ↓
 GitHub
```

---

## 4. Descargar cambios con `git pull`

Si el repositorio de GitHub contiene cambios que todavía no tenemos localmente, podemos descargarlos con:

```bash
git pull
```

Este comando obtiene los cambios del repositorio remoto y los integra en nuestra rama actual.

El flujo sería:

```text
GitHub
   │
   │ git pull
   ↓
Ordenador
```

---

## 5. `git fetch`

También podemos utilizar:

```bash
git fetch
```

La diferencia importante es que `fetch` **descarga la información del repositorio remoto pero no integra automáticamente los cambios en nuestra rama actual**.

Por ejemplo:

```text
git fetch
    ↓
Descarga información
    ↓
No modifica directamente
nuestra rama actual
```

Después podemos revisar los cambios y decidir cómo integrarlos.

Una forma sencilla de recordar la diferencia:

```text
git fetch → "dime qué hay en remoto"

git pull  → "descarga e integra los cambios"
```

---

# 6. Clonar un repositorio

Si queremos obtener un repositorio de GitHub en nuestro ordenador, podemos clonarlo:

```bash
git clone URL_DEL_REPOSITORIO
```

Por ejemplo:

```bash
git clone URL_DEL_REPOSITORIO
```

Esto crea una copia local del repositorio.

El flujo es:

```text
GitHub
   │
   │ git clone
   ↓
Ordenador
```

Después podemos entrar en la carpeta:

```bash
cd mi-proyecto
```

Y trabajar normalmente con Git:

```bash
git status
git add .
git commit -m "Descripción"
```

---

# 7. Flujo completo con GitHub

Un flujo típico podría ser:

```text
Crear/modificar archivos
          ↓
      git status
          ↓
        git add
          ↓
      git commit
          ↓
       git push
          ↓
        GitHub
```

Por ejemplo:

```bash
git status
git add .
git commit -m "Añadida nueva funcionalidad"
git push origin main
```

De esta forma, los commits que tenemos localmente se envían al repositorio de GitHub.

---

# 8. Trabajar con ramas

GitHub permite trabajar con diferentes ramas.

Por ejemplo:

```text
main
 │
 ├── feature-login
 │
 ├── feature-api
 │
 └── fix-error
```

Podemos crear una rama utilizando Git:

```bash
git switch -c feature-login
```

Después hacemos nuestros cambios y creamos un commit:

```bash
git add .
git commit -m "Añadido sistema de login"
```

Finalmente podemos subir esa rama a GitHub:

```bash
git push -u origin feature-login
```

La opción:

```text
-u
```

establece la relación entre nuestra rama local y la rama remota. Esto permite que posteriormente podamos utilizar simplemente:

```bash
git push
```

y:

```bash
git pull
```

---

# 9. Pull Requests

Una de las funcionalidades más importantes de GitHub son las **Pull Requests (PR)**.

Una Pull Request permite proponer que los cambios de una rama se incorporen a otra.

Por ejemplo:

```text
main
 │
 └── feature-login
          │
          │ Pull Request
          ↓
         main
```

El proceso habitual es:

1. Crear una rama.
2. Realizar cambios.
3. Crear commits.
4. Subir la rama a GitHub.
5. Crear una Pull Request.
6. Revisar los cambios.
7. Corregir posibles problemas.
8. Integrar la rama en `main`.

Las Pull Requests son especialmente importantes en proyectos colaborativos porque permiten **revisar el código antes de incorporarlo a la rama principal**.

---

# 10. Code Review

Las Pull Requests permiten realizar **Code Review**.

Otros desarrolladores pueden revisar el código y realizar comentarios sobre líneas concretas.

Por ejemplo:

```text
Pull Request
      ↓
Revisión del código
      ↓
Comentarios
      ↓
Correcciones
      ↓
Nueva revisión
      ↓
Merge
```

Esto ayuda a detectar:

* Errores.
* Problemas de seguridad.
* Código innecesariamente complejo.
* Problemas de diseño.
* Posibles mejoras.

---

# 11. Issues

GitHub también proporciona **Issues**, que permiten registrar y organizar tareas, errores o problemas.

Por ejemplo:

```text
Issue #15
"El formulario de login permite contraseñas vacías"
```

Una Issue puede utilizarse para:

* Informar de un bug.
* Crear una tarea.
* Proponer una mejora.
* Organizar trabajo.
* Registrar problemas del proyecto.

Podemos relacionar una Pull Request con una Issue para mantener un seguimiento del trabajo.

---

# 12. README

Un archivo muy importante en muchos repositorios es:

```text
README.md
```

Normalmente contiene información sobre el proyecto, como:

* Qué hace.
* Cómo instalarlo.
* Cómo utilizarlo.
* Requisitos.
* Ejemplos.
* Estructura del proyecto.

Por ejemplo:

```text
mi-proyecto/
│
├── README.md
├── src/
├── tests/
├── requirements.txt
└── .gitignore
```

El README suele ser lo primero que consulta una persona cuando entra en un repositorio.

---

# 13. `.gitignore`

El archivo `.gitignore` permite indicar a Git qué archivos **no queremos subir al repositorio**.

Por ejemplo:

```text
.env
__pycache__/
node_modules/
*.log
```

Esto es especialmente importante para evitar subir archivos que:

* Contengan credenciales.
* Contengan claves privadas.
* Sean archivos temporales.
* Sean generados automáticamente.
* No deban formar parte del proyecto.

Por ejemplo, nunca deberíamos subir directamente contraseñas o tokens en un repositorio.

---

# 14. Releases

GitHub permite crear **Releases** para publicar versiones concretas de un proyecto.

Por ejemplo:

```text
v1.0.0
v1.1.0
v2.0.0
```

Una release puede incluir:

* Número de versión.
* Descripción de los cambios.
* Notas de la versión.
* Archivos asociados.

Normalmente las releases se relacionan con **tags de Git**.

---

# 15. GitHub Actions

GitHub también permite automatizar tareas mediante **GitHub Actions**.

Por ejemplo, podemos configurar un proyecto para que automáticamente:

```text
Push
  ↓
GitHub Actions
  ↓
Ejecutar tests
  ↓
Comprobar código
  ↓
Construir proyecto
```

Esto permite automatizar procesos de **CI/CD** (*Continuous Integration / Continuous Delivery*).

Por ejemplo, cada vez que alguien crea una Pull Request, podemos ejecutar automáticamente los tests para comprobar que los cambios no han roto el proyecto.

---

# 16. Permisos y colaboración

GitHub permite trabajar con otras personas en un mismo repositorio.

Dependiendo de los permisos, los usuarios pueden tener diferentes capacidades para:

* Leer el repositorio.
* Crear ramas.
* Crear Issues.
* Crear Pull Requests.
* Revisar código.
* Realizar merges.
* Administrar el repositorio.

En proyectos grandes, es habitual establecer reglas para proteger determinadas ramas, especialmente `main`.

---

# 17. Git vs GitHub

Es importante no confundirlos:

| Git                                               | GitHub                                         |
| ------------------------------------------------- | ---------------------------------------------- |
| Sistema de control de versiones                   | Plataforma para alojar y colaborar             |
| Funciona localmente                               | Servicio online                                |
| Gestiona commits                                  | Aloja repositorios Git                         |
| Gestiona ramas                                    | Facilita la colaboración entre ramas           |
| Permite `merge`                                   | Permite Pull Requests                          |
| Permite consultar historial                       | Permite revisar el proyecto online             |
| No necesita Internet para las operaciones locales | Normalmente requiere conexión para sincronizar |

Una forma sencilla de entenderlo:

```text
              GIT
       Control de versiones
               │
               │ push / pull
               ↓
           GITHUB
       Repositorio remoto
               │
       ┌───────┼────────┐
       ↓       ↓        ↓
    Issues    PRs    Actions
```

---

# Flujo habitual Git + GitHub

En un proyecto real, un flujo bastante habitual sería:

```text
        GitHub
           │
           │ git clone
           ↓
     Repositorio local
           │
           ↓
      Crear rama
           │
           ↓
      Modificar código
           │
           ↓
        git add
           │
           ↓
       git commit
           │
           ↓
        git push
           │
           ↓
        GitHub
           │
           ↓
    Pull Request
           │
           ↓
     Code Review
           │
           ↓
         Merge
           │
           ↓
          main
```

### Comandos fundamentales

```bash
# Clonar un repositorio
git clone URL_DEL_REPOSITORIO

# Comprobar el estado
git status

# Añadir cambios
git add .

# Crear un commit
git commit -m "Descripción de los cambios"

# Subir cambios
git push

# Descargar e integrar cambios
git pull

# Descargar información sin integrarla
git fetch

# Crear una rama
git switch -c nueva-rama

# Subir una nueva rama
git push -u origin nueva-rama
```

### Idea clave

**Git** se encarga principalmente del **control de versiones**, mientras que **GitHub** proporciona una plataforma para **alojar esos repositorios y colaborar con otras personas**.

Una forma fácil de recordarlo es:

> **Git controla las versiones; GitHub permite compartirlas y colaborar sobre ellas.**
