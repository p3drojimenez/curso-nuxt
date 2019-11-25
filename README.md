# 📗 Clase 23 Reto.


## Parte 1: Slots:

Deberás crear dos componentes `Banner.vue` y `Slogan.vue` para usar el Slot de Hero. Además deberas crear una propieda `banner` para renderizar un componente o el otro.

Usa un custom event, para modificar el valor de esa propiedad.


## Parte 2: Directivas

Deberás hacer uso de la diretiva `v-for` para renderizar todos los restaurantes del siguiente array y vincular sus propiedades al componente `RestaurantCard.vue`

```js
restaurants: [
  {
    name: 'Restaurant La Cúpula',
    description: 'Platos mediterráneos y coches antiguos',
    slug: 'la-cupula',
    category: 'Mediterráneos',
    likes:0
  },
  {
    name: 'Restaurant Singular',
    description: 'Brunch, desayunos y comidas con variada carta mediterránea en un luminoso café de moderno diseño minimalista.',
    slug: 'Singular',
    category: 'Brunch',
    likes:0
  },
  {
    name: 'Oporto Restaurante',
    description: 'Bacalao, francesinhas y otras recetas de la gastronomía lusa en un coqueto bar decorado con cajas de oporto.',
    slug: 'oporto',
    category: 'Mediterráneos',
    likes:0
  }
]
```

Te encontrarás una dificultad a la hora de actualizar los likes de cada restaurante. Vuejs necesita un valor único para diferenciar cada elemento de la lista / bucle.

Una manera de hacerlo es ayudandonos del **index** del mismo bucle, por ejemplo:

`v-for="(restaurant, index) in restaurants" :key="index"`

Ahora, podemos usar ese index, para conocer que posición del array es el que se ha pulsado el botón para sumar likes:

`v-on:onLikeButton="sumRestaurantLikes(index)"`

Para poder acceder a una posición especifica del array, podemos accerlo de la siguiente manera: `this.restaurants[index]`.


[Atributo **Key**](https://vuejs.org/v2/guide/list.html)


### 📚 Referencias y ayudas

- [Atributo Key](https://vuejs.org/v2/guide/list.html)
- [Arrays en Javascript](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array)
- [Bulma io](https://bulma.io/)
- [Single File Components](https://vuejs.org/v2/guide/single-file-components.html)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)