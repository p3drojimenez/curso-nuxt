# 📗 Clase 7: Instalación Nuxtjs

Primeramente debemos asegurarnos de tener instalado **Nodejs**. Usaremos ***npx***, que nos va a permitir instalar librerias y dependencias sin tener que instalar de forma global las mismas. Viene incluido en cualquier instalación de nodejs ( *npm > 5.2.0* ). Si tenemos nodejs instalado, podemos simplemente ejecutar el comando:

`npx create-nuxt-app <nombre-del-proyecto>`

Si prefieres hacer la instalación usando el gestor de paquetes [yarn](https://yarnpkg.com/en/):

`yarn create nuxt-app <nombre-del-proyecto>`

Durante el proceso de instalación o creación del proyecto, la herramienta nos permite seleccionar algunas configuraciones por defecto:

**Antes de empezar...**
```
* Para selecciónar cualquier opción usa la barra de espacio.
* Para continuar pulsa la tecla intro.
```

- Paso 0: 
Nos preguntara el nombre del proyecto, el autor y una pequeña descripción del mismo.

- Paso 1: 
Si queremos integrar **Nuxtjs** con algún otro framework. (Express, Koa, Micro, etc..). Para nuestro proyecto, no sera necesario.

- Paso 2:
Si queremos integrar **Nuxtjs** con algún otro framework UI, como por ejemplo:

  - [Bootstrap](https://getbootstrap.com/)
  - [Vuetify](https://vuetifyjs.com)
  - [Bulma](http://bulma.io)

En nuestro proyecto, usaremos **Bulma**, pero realizaremos la instalación y configuración de forma manual en una clase posterior.

- Paso 3:

**Nuxtjs** nos permite configurar una herramienta de testing para testear nuestros componentes, métodos y funciones. En el curso, tenemos una sección dedicada exclusibamente al testing, por lo que te recomiendo que selecciones **Jest**, ya que será la herramienta que usaremos.

- Paso 4:

Nuestro proyecto sera SSR, por lo que debemos pre-configurar como *Seleccionar Universal* (**Server Side Rendering**).

- Paso 5: 

Usaremos **AXIOS** como libreria para realizar peticiones HTTP, pero lo instalaremos posteriormente al igual que hicimos con Bulma CSS.

- Paso 6:

*EsLint* nos permite que nuestro código sea más limpio y siga unos patrones y estructuras estandares. En nuestro proyecto, no lo configuraremos, auque es una buena práctica acostumbrarse a ello.

- Paso 7:

Al igual que Eslint, *Prettier* hará que nuestro código más legible a otros programadores.

- Paso 8: 

El último paso, si utilizas el editor de código Visual Studio Code, te recomiendo que selecciones crear el fichero *jsconfig.json* ya que nos incluirá ayudas para acceder de una manera más rápida a nuestros componentes. 

![Instalación Nuxtjs](https://github.com/p3drojimenez/cursoOpenWebinars/blob/clase-7/assets/instalacion_nuxtjs.png)

## 📋 Probando la instalación:

Una vez finalizada la instalación, solo debemos entrar dentro del folder del proyecto y ejecutar un script de *npm*.

```
cd <nombre-del-proyecto
npm run dev
```

Si todo ha salido bien, `npm run dev` creará un servidor de **desarrollo** en tu ordenador donde podremos probar y ver los cambios en tiempo real.

Desde este momento, nuestro proyecto estará accesible desde la url:

[http://localhost:3000](http://localhost:3000)


### 📚 Referencias y ayudas:

- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Descargas de Nodejs](https://nodejs.org/es/download/)
- [EsLint](https://eslint.org/)
- [Prettier](https://prettier.io/)
- [Axios](https://github.com/axios/axios)