# 📗 Clase 14 Modificando RestaurantCard:

**components/RestaurantCard.vue**

```html
<template>
  <div class="card" style="width:400px;">
    <div class="card-image">
      <figure class="image">
        <img src="~/assets/images/restaurant.jpg" alt="Pizza Restaurant" />
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
                {{ category }}
              </span>
            </div>
            <div class="column has-text-right">
              <button class="button is-info" v-on:click="sumLikes">
                {{ likes }}
              </button>
            </div>
          </div>
        </div>
      </div>
      <div class="content">
        {{ description}}
        <a v-bind:href="slug">more info</a>.
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: 'Bar Paco',
      description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.Phasellus neciaculis mauris.',
      likes: 0,
      category: 'burger',
      slug: 'restaurant-name'
    }
  },
  methods: {
    sumLikes() {
      // this.likes = this.likes + 1
      this.likes++
    }
  }
}
</script>

<style scoped>
.restaurant-name {
  font-size: 30px;
  color: #8ae6ff;
}
</style>
```


### 📚 Referencias y ayudas

- [Renderizado de listas v-for](https://es.vuejs.org/v2/guide/list.html)
- [Renderizado condicional](https://es.vuejs.org/v2/guide/conditional.html)
- [Directivas en vuejs](https://es.vuejs.org/v2/guide/syntax.html#Directivas)
- [Bulma io](https://bulma.io/)
- [Single File Components](https://vuejs.org/v2/guide/single-file-components.html)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [GitHub](https://github.com/)
