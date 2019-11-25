# 📗 Clase 8: Estructura de directorios en NUXJS

### ASSETS:

Este directorio contiene los ficheros no compilados de SASS, imagenes o fuentes.

### LAYOUTS

Contiene los layouts o templates de nuestra aplicación. ( Sidebars, Headers, Footers...)

### Middleware

Contiene funciones personalizadas que pueden ser ejecutadas **ANTES** de cada pagína o grupos de páginas. Buen sitio para escribir una función que valide, por ejemplo si un usuario esta logeado y tiene permisos para acceder a una url en concreto.

### Pages

Contiene ficheros **.vue** que Nuxtjs renderiza como páginas generando las rutas correspondientes de forma automática.

### Plugins

Confiente funciones que se instancian junto con la instancia principal de Vuejs. Es un buen sitio para definir funciones o constantes. En nuestro proyecto definiremos aqui la configuración de firebase o el plugin de Google Analytics.

### Static

El directorio static es directamente accesible desde el servidor como una ruta o directorio, por ejemplo es el sitio donde se deben poner los ficheros robots.txt, sitemap.xml o el favico.

### Store

Este directorio contiene los ficheros que manejan el estado de la aplicación.

### nuxt.config.js

El fichero `nuxt.config.js` es el fichero de configuración de nuxtjs.

### package.json

Fichero que contiene todas las dependencias y scrips.
### 📚 Referencias y ayudas

- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)
- [Crear cuenta Github](https://help.github.com/es/articles/adding-a-new-ssh-key-to-your-github-account)
- [Generar claves ssh](https://help.github.com/es/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)