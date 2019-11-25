# 📗 Clase 30

## asyncData():

El método `asyncData` realiza la petición en la parte del servidor, lo que ayuda a mejorar el posicionamiento web (SEO) y libera de carga al cliente.

```js
async asyncData() {
  try {
    const { data } = await api.getRestaurants()
    return { restaurants: data }
  } catch (error) {
    error({ statusCode: 404, message: 'Restaurant not found' })
  }
}
```

### 📚 Referencias y ayudas
- [AXIOS](https://es.vuejs.org/v2/cookbook/using-axios-to-consume-apis.html)
- [Async & await](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/funcion_asincrona)
- [Async-Data()](https://nuxtjs.org/guide/async-data/)
- [Template Strings](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/template_strings)
- [Estados de respuesta HTTP](https://developer.mozilla.org/es/docs/Web/HTTP/Status)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)