# 📗 Clase 21 Custom Events

Un componente hijo puede enviar información al componente padre mediante los custom events. Para ello, usaremos el método `emit()` al que enviaremos por parametro el nombre del evento.

**NOTA**: Debemos escribir el método $emit() con el simbolo del dolar, por que es un metodo que nos proporciona el propio framework de nuxt.

**components/RestaurantCard.vue**

Modificamos el método para que emita el evento `onLikeButton`.

```js
onLikeButton(){
  this.$emit('onLikeButton')
  // this.likes++
}
```
**pages/index.vue**

Debemos capturar ese evento del hijo desde el componente padre. Eso lo hacemos añadiendo la directiva `v-on:` al componente. Es importante que la directiva `v-on`este asociada con el mismo nombre del evento, si no, el componente *padre* no sera capaz de reconocer el evento.

```html
<RestaurantCard
  name="Restaurant Name"
  description="Description......"
  slug="restaurant-slug"
  category="Burguer"
  :likes="likes"
  v-on:onLikeButton="sumRestaurantLikes"
/>
```

`sumRestaurantLikes` es el método que se encargara de la lógica de sumar un like al restaurante.

```js
methods: {
  sumRestaurantLikes() {
    this.likes++
  }
}
```

### 📚 Referencias y ayudas

- [Vuejs Router](https://router.vuejs.org/guide/essentials/dynamic-matching.html)
- [Bulma io](https://bulma.io/)
- [Single File Components](https://vuejs.org/v2/guide/single-file-components.html)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)