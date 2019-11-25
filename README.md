# 📗 Clase 30 Reto:

En este reto deberas completar las páginas de categorias y detalle de un restaurante realizando las peticiones asincronas necesarias. Antes de empezar, copi pega los nuevos templates en sus correspondientes ficheros:

**_category/index.vue**

```html
<template>
  <div class="container">
    <section class="section">
      <h1 class="title is-1">{{ $route.params.category }}</h1>
      <nav class="breadcrumb" aria-label="breadcrumbs">
        <ul>
          <li>
            <nuxt-link to="/">
              Home
            </nuxt-link>
          </li>
          <li class="is-active">
            <a href="#" aria-current="page">{{ $route.params.category }}</a>
          </li>
        </ul>
      </nav>
      <div class="container">
        <section class="section">
          <div class="columns">
            <RestaurantCard
              :name="restaurant.name"
              :description="restaurant.description"
              :slug="restaurant.slug"
              :category="restaurant.category"
              :likes="restaurant.likes"
              :image="restaurant.image"
              class="restaurant-card"
              v-for="(restaurant, index) in restaurants" :key="index" 
            />
          </div>
        </section>
      </div>
    </section>
  </div>
</template>

<script>
import RestaurantCard from '~/components/RestaurantCard'
import api from '~/services/api'

export default {
  components: {
    RestaurantCard,
  },
  async asyncData({ params }) {
    try {
      /* petición getRestaurantsByCategory() */

    } catch (error) {
      console.log({ statusCode: 404, message: 'Category not found' })
    }
  }
}
</script>
<style>
.restaurant-card {
  margin: 10px 20px;
  min-width: 300px;
}
</style>
```


**_category/_slug.vue**

```html
<template>
<div>
  <div class="container">
    <section class="section">
      <h1 class="title is-1">{{ restaurant.name }}</h1>
      <nav class="breadcrumb" aria-label="breadcrumbs">
        <ul>
          <li>
            <nuxt-link to="/">
              Home
            </nuxt-link>
          </li>
          <li>
            <nuxt-link :to="`/${$route.params.category}`" aria-current="page">
              {{ $route.params.category }}
            </nuxt-link>
          </li>
          <li class="is-active">
            <a href="#" aria-current="page">{{ restaurant.name }}</a>
          </li>
        </ul>
      </nav>
      <div class="columns">
        <div class="column box">
          <div class="columns">
            <div class="column">
              <img :src="restaurant.image" class="image" />
            </div>
          </div>
          <div class="columns">
            <div class="column">
              <p>{{ restaurant.description }}</p>
            </div>
            <div class="column has-text-right">
              <div class="button">
                <span>{{ restaurant.likes }}</span>
              </div>
            </div>
          </div>
          <div class="columns">
            <div class="column">
              <span class="tag">{{ restaurant.city }}</span>
            </div>
            <div class="column has-text-right">
              <span>{{ restaurant.address }}</span>
            </div>
          </div>
          <div class="columns">
            <div class="column">
              <p>Descripción:</p>
              <p>{{ restaurant.text }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</div>
</template>

<script>
import api from "~/services/api"
export default {
  async asyncData({ params }) {
    try {
        /* petición getOneRestaurant() */
    } catch (error) {
      console.log({ statusCode: 404, message: 'Restaurant not found' })
    }
  }
  }
</script>

<style scoped>
.image {
  width: 100%;
}
</style>
```


**RestaurantCard.vue**
```html
<template>
  <div class="card" style="width:400px;">
    <div class="card-image">
      <figure class="image">
        <img :src="image" alt="Pizza Restaurant" class="restaurant-image" />
      </figure>
    </div>
    <div class="card-content">
      <div class="media">
        <div class="media-content">
          <p class="title is-4 restaurant-name">
            {{ name }}
          </p>
          <div class="columns">
            <div class="column">
              <span class="is-category tag">
                <nuxt-link :to="category">
                  {{ category }}
                </nuxt-link>
              </span>
            </div>
            <div class="column has-text-right">
              <button
                class="button is-info"
                v-on:click="onLikeButton"
              >
                {{ likes }}
              </button>
            </div>
          </div>
        </div>
      </div>
      <div class="content">
        {{ description }}
        <a v-bind:href="`${category}/${slug}`">more info</a>.
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      default: ''
    },
    description: {
      type: String,
      default: ''
    },
    category: {
      type: String,
      default: ''
    },
    slug: {
      type: String,
      default: ''
    },
    likes: {
      type: Number,
      default: 0
    },
    image: {
      type: String,
      default: ''
    }
  },
  methods: {
    onLikeButton(){
      this.$emit('onLikeButton')
      // this.likes++
    }
  }
}
</script>

<style scoped>
.restaurant-name {
  font-size: 30px;
  color: #8ae6ff;
}
.restaurant-image {
  width: auto;
  height: 200px;
}
</style>
```

**index.vue**

Modifica el componente `RestaurantCard.vue`:

```html
<RestaurantCard
  :name="restaurant.name"
  :description="restaurant.description"
  :slug="restaurant.slug"
  :category="restaurant.category"
  :likes="restaurant.likes"
  :image="restaurant.image"
  v-on:onLikeButton="sumRestaurantLikes(restaurant)"
  class="restaurant-card"
  v-for="(restaurant, index) in restaurants" :key="index" 
/>
```

## Ejemplos de peticiones:


### Detalle de un restaurante:

```http
https://my-json-server.typicode.com/p3drojimenez/restaurants/restaurants?slug=tandoor-barcelona
```

### Restaurantes de la categoria Oriental
```http
https://my-json-server.typicode.com/p3drojimenez/restaurants/restaurants?category=Oriental
```

### ⚒️ RECOMENDACIÓN:

### 📚 Referencias y ayudas
- [AXIOS](https://es.vuejs.org/v2/cookbook/using-axios-to-consume-apis.html)
- [Async & await](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/funcion_asincrona)
- [Async-Data()](https://nuxtjs.org/guide/async-data/)
- [Template Strings](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/template_strings)
- [Estados de respuesta HTTP](https://developer.mozilla.org/es/docs/Web/HTTP/Status)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)