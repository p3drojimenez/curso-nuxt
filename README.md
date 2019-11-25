# 📗 Clase 47 Solución del reto

LLego el momento de pasar nuestro proyecto a un entorno productivo y que podamos subir nuestra web a un servidor. 

Durante todo el proyecto, hemos trabajado siempre pensando en crear una página web server side render, que como vimos en las primeras clases ayudaba y facilitaba la indexación de los buscadores y mejorar el seo entre otras cosas.

Para generar nuestro proyecto, antes de nada, vamos a asegurarnos de que tenemos selecionado el flag correspondiente en nuestra configuración. Nos vamos al fichero de nuxtjs y debemos tener el modo en tipo 'universal', si no es asi, es por que cuando habeis creado el proyecto de nuxtjs habeis seleccionado SPA (Single page aplication).

```js
  mode: 'universal',
```

Ahora vamos a crear una página 404, para que en el caso, de que la url no se encuentre, seamos capaces de mostrar algo de información al usuario.

**pages/404.vue**

```hml
<template>
  <div class="column is-4 is-offset-4">
    <div class="columns">
      <div class="column has-text-centered">
        <h1 class="title is-1">
          404
        </h1>
      </div>
    </div>
    <div class="columns">
      <div class="column has-text-centered">
        <p>Página no encontrada</p>
      </div>
    </div>
    <div class="columns">
      <div class="column has-text-centered">
        <a href="/">Volver</a>
      </div>
    </div>
  </div>
</template>
```

Antes de generar nuestras páginas, debemos decirle a nuxtjs cuales son las páginas que tenemos que generar y cuales seran sus rutas.

Dentro de nuestro fichero de configuración, debemos hacer uso de la propiedad que es un objeto que retornara un array con todas las rutas. En nuestro caso, tenemos rutas que son estaticas y otras rutas que son dinamicas.

```js
generate: {}
```

Para generar todas las rutas, podemos hacerlo de forma manual o podemos realizar una consulta a firebase, para que nos retorne todas las rutas que existen.

```js
generate: {
  async routes () {
    let routesList = []
    try {
      const data = await db.collection('restaurants').get()
      const docs = await data.docs
      docs.map(doc => {
        const category = '/' + doc.data().category
        routesList.push(category)
        const route = '/' + doc.data().category + '/' + doc.data().slug
        routesList.push(route)
      })
      return routesList
    } catch (error) {
      console.log(error)
      return []
    }
  }
}
```

No tenemos que olvidar, tambien importar nuestra aplicación de firebase. En este caso, y solo para el fichero de configuración, debemos ser explicitos con la dirección donde se encuentra el fichero, por lo que no podremos usar alias.

`import { db } from './plugins/firebase'`

Si es correcto, podemos lanzar el comando:

```shell
npm run generate
```

Este comando, generara todos los ficheros necesarios para ejecutar vuestra aplicacion en cualquier hosting, salvo por un pequeño inconveniente que hay que tener encuenta cuando trabajamos con SSR. Pero, eso lo explicaremos mejor en la siguiente clase, cuando hagamos el despliegue en netlify.


Si no teneis ningun problema, vereis que se ha generado un directorio llamado dist, ese directorio lo podeis copiar y llevar a cualquier servidor de hosting, subirlo por FTP y os funcionara sin problemas.
