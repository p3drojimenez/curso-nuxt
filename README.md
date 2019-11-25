# 📗 Clase 10: Contexto de nuxtjs

## ¿Qué es el contexto de nuxtjs?

El **contexto** en una aplicación de nuxtjs son objetos(con sus métodos) y parametros que extienden la instancia de vuejs.

Podemos encontrar métodos como por ejemplo:

- asyncData()
- fetch()

Podemos escribir **plugins** o **middlewares**.

```js
function (context) {
  // Universal keys
  const {
    app,
    store,
    route,
    params,
    query,
    env,
    isDev,
    isHMR,
    redirect,
    error
  } = context
  // Server-side
  if (process.server) {
    const { req, res, beforeNuxtRender } = context
  }
  // Client-side
  if (process.client) {
    const { from, nuxtState } = context
  }
}
```

Puedes consultar más información en la documentación oficial de Nuxtjs.

[The context](https://nuxtjs.org/api/context/)

### 📚 Referencias y ayudas

- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)