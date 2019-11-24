# 📗 Clase 15 Eventos y páginas dinámicas:

## Páginas Estáticas

Nuxtjs convierte automaticamente todos los componentes dentro del folder **pages** en vistas o páginas. Para todas las páginas que no comiencen por *_*, creara su correspondiente `*.html*` en el momento de generar la página estática.

## Páginas dinamicas

Las páginas dinamicas son aquellas que pueden tomar diferentes valores según los parametros que reciva por url. Un buen ejemplo de este tipo de rutas, son aquellas que visualizan el detalle de un restaurante, como nuestro proyecto.

Nuxtjs nos genera automanticamete una página con el parametro que se envia en la url, el cual podemos acceder a el del siguiente modo:

`this.$router.params.slug`

> ⚠️ Para que Nuxtjs interprete correctamente que es una ruta dinámica, el nombre del componente debe ir precedido de: **_**. En nuestro caso y para hacerlo más entendible hemos decidido llamar al componente `_slug.vue`, pero podríamos usar otras combinaciones.



### 📚 Referencias y ayudas

- [Vuejs Router](https://router.vuejs.org/guide/essentials/dynamic-matching.html)
- [Nuxtjs Rutas dinámicas](https://nuxtjs.org/guide/routing/)
- [Bulma io](https://bulma.io/)
- [Single File Components](https://vuejs.org/v2/guide/single-file-components.html)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)