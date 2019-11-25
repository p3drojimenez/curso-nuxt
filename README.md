# 📗 Clase 24 Solución del reto.

**Resumen**
~~~
En esta clase aprenderás a solucionar el reto propuesto en la clase anterior.
~~~

## Parte 1: Slots:

Paso 1: Crear los dos componentes:

**components/banner.vue**

```html
<template>
  <div class="banner">
    <h2 class="title is-2">Restaurante Mediterraneo</h2>
    <div>
      <p> Entregas a domincio</p>
      <h3 class="title is-3">821 821 812</h3>
    </div>
  </div>
</template>

<style scoped>
 .banner {
  background-image: url('../assets/images/banner.jpg');
  background-size: cover;
  height: 150px;
  width: 790px;
  padding: 2px 15px;
} 
</style>
```

**components/Slogan.vue**

```html
<template>
  <div>
    <h2 class="title is-2">FoodAdvisor, tu web de restaurantes</h2>
    <div class="subcribe">
      <input type="text" class="input email" placeholder="email..."/>
      <button class="button is-info">Suscribirse</button>
    </div>
  </div>
</template>

<style scoped>
.subcribe{
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.email {
 width: 80%;
}
</style>
```

Paso 2: Importando componentes en `index.vue``

```js
import Slogan from '~/components/Slogan'
import Banner from '~/components/Banner'

export default {
  components: {
    RestaurantCard,
    Hero,
    Banner,
    Slogan
  },
  .....
```

Paso 3: Incorporando los componentes dentro del Slot:

```html
 <Hero>
  <Banner slot="header" style="width: 790px" />
  <Slogan slot="header" style="width: 790px" />
</Hero>
```

Paso 4: Crear propiedad **banner** en el componente *index.vue*

```js
data() {
  return {
    likes: 0,
    banner: false
  }
}
```

Paso 5: Añadiendo directivas `v-if` y `v-else`:

```html
<Banner slot="header" style="width: 790px" v-if="banner"/>
<Slogan slot="header" style="width: 790px" v-else/>
```

Paso 6: Modificar el componente `Hero.vue` añadiendo un custom event: 

```html{3}
<template>
  <section class="hero is-primary">
    <div class="hero-body">
      <button class="button is-info" @click="$emit('onChangeBanner')">Cambiar banner</button>
      <slot name="header">
      </slot>
    </div>
  </section>
</template>

<style scoped>
.container-slot {
  background-color: red;
}
</style>
```

Paso 7: Modificando `index.vue` para que el componente `<Hero>` reconozca el evento.

```html{0}
 <Hero @onChangeBanner="changeBanner">
  <Banner slot="header" style="width: 790px" v-if="banner"/>
  <Slogan slot="header" style="width: 790px" v-else/>
</Hero>
```

Pso 8: Creando método para cambiar el valor de la propiedad `banner`.

```js
methods: {
  changeBanner() {
    this.banner = !this.banner
  }
}
```

## Parte 2: Directivas

Paso 1: Añadir array al modelo de datos:

```js
data() {
  return {
    likes: 0,
    banner: false,
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
  }
}
```

Paso 2: Escribiendo bucle `v-for` y bindeado de propiedades:

```html
<RestaurantCard
  :name="restaurant.name"
  :description="restaurant.description"
  :slug="restaurant.slug"
  :category="restaurant.category"
  :likes="restaurant.likes"
  v-on:onLikeButton="sumRestaurantLikes"
  v-for="(restaurant, index) in restaurants" :key="index" 
/>
```

Paso 3: Escribiendo método sumRestauranteLikes

```js
  sumRestaurantLikes(index) {
    this.restaurants[index].likes = this.restaurants[index].likes + 1
  },
```

Paso 4: Actualizando componente `RestaurantCard` con el evento onLikeButton.

```html
<RestaurantCard
  :name="restaurant.name"
  :description="restaurant.description"
  :slug="restaurant.slug"
  :category="restaurant.category"
  :likes="restaurant.likes"
  v-on:onLikeButton="sumRestaurantLikes(index)"
  class="restaurant-card"
  v-for="(restaurant, index) in restaurants" :key="index" 
/>
```

Paso 5: Haciendo responsive el componente:

```html
<template>
  <div>
    <Hero @onChangeBanner="changeBanner">
      <Banner slot="header" style="width: 790px" v-if="banner"/>
      <Slogan slot="header" style="width: 790px" v-else/>
    </Hero>
    <div class="container">
      <section class="section">
        <div class="columns">
          <RestaurantCard
            :name="restaurant.name"
            :description="restaurant.description"
            :slug="restaurant.slug"
            :category="restaurant.category"
            :likes="restaurant.likes"
            v-on:onLikeButton="sumRestaurantLikes(index)"
            class="restaurant-card"
            v-for="(restaurant, index) in restaurants" :key="index"
          />
        </div>
      </section>
    </div>
  </div>
</template>
.....
<style>
.restaurant-card {
  margin: 10px 20px;
  min-width: 300px;
}
</style>
```

### 📚 Referencias y ayudas

- [Atributo Key](https://vuejs.org/v2/guide/list.html)
- [Arrays en Javascript](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array)
- [Bulma io](https://bulma.io/)
- [Single File Components](https://vuejs.org/v2/guide/single-file-components.html)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)