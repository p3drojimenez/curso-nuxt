# Clase 8: Crear repositorio en Github

### 💻️ Pasos para crear un repositorio:

- Paso 1: 
  Registrarse como usuario en Github.
- Paso 2:
  Pulsar sobre el botón **+** o **New Repository**
- Paso 3:
  Rellenar el formulario.(Seleccionar **Privado** o **Público**)
- Paso 4:
  Guardar la información del repositorio para después poder enlazarlo con nuestro proyecto en NuxtJS
  ![Datos del repositorio](https://github.com/p3drojimenez/cursoOpenWebinars/blob/clase-6/assets/datos-repositorio.png)

### HTTPs o SSL

Para poder enviar los cambios al repositio, es recomendable hacerlo siempre por SSL, por lo que debemos configurar la clase SSH de nuestro equipo con nuestra cuenta en GitHub:

Para generar una clave SSH en nuestro equipo (MAC y Linux):

https://www.siteground.es/kb/generar-clave-ssh-linux/

Y después añadir la clave pública a nuestra cuenta github

https://github.com/settings/ssh/new

En la clase 8 Se ve en detalle este proceso.


### ⚙️Comandos Útiles de Github:

- ``git help`` : Muestra la ayuda de Git.
- ``git init`` : Inicializa un nuevo repositorio en **Local**.
- ``git clone <repo>`` : Clonamos un repositio remoto a un directorio local.
- ``git add <fichero>`` : Añade al **state** de git *un único fichero*.
- ``git add .`` : Añade al **state** del repositorio *todos los ficheros*.
- ``git commit -m "mensaje"`` : Guardamos un mensaje / información junto con los ficheros que se encuentran en el **state** de nuestro repositorio.
- ``git branch``: Lista las ramas existentes en el repositorio.
- ``git checkout nombreRama``: Cambiamos la rama actual por **nombreRama**.
- ``git checkout -b nombreRama``: Cambiamos la rama actual por **nombreRama**, pero si no existe, crea una nueva.
- ``git branch -D nombreRama``: Borramos la rama *nombreRama*.
- ``git status`` : Nos muestra el **state** del repositorio, es decir, qué ficheros han sido modificados y aún no se ha realizado el `commit`.
- ``git push`` : Enviamos al repositio remoto los cambios.
- ``git pull`` : Recuperamos del repositorio remoto los ficheros.
- ``git merge nombreRama`` : Realiza un merge (fusión de ficheros) de la rama **nombreRama** con la rama actual, es decir, recupera los ficheros de la rama **nombreRama** y los fusiona con la rama actual.


### 📚Referencias y ayudas:

- [Github](github.com)
- [Crear un repositorio en Github](https://help.github.com/en/articles/create-a-repo)
- [Más comandos git](https://www.hostinger.es/tutoriales/comandos-de-git)
- [Guía rápida de Git](https://rogerdudler.github.io/git-guide/index.es.html)
