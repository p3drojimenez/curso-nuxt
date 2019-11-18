<template>
  <div class="container">
    <Hero>
      <div slot="header">
        <p>Soy el slot desde el padre index.vue</p>
      </div>
    </Hero>
    <section class="section">
      <RestaurantCard
        name="Bar Paco"
        description="Descripción del restaurante"
        category="burger"
        slug="bar-paco"
        :likes="likes"
        v-on:onLikeButton="sumLikes"
      />
    </section>
  </div>
</template>

<script>
import RestaurantCard from "~/components/RestaurantCard"
import Hero from "~/components/Hero"

export default {
  components: {
    RestaurantCard,
    Hero
  },
  data() {
    return {
      likes: 0
    }
  },
  methods: {
    sumLikes() {
      this.likes++
    }
  }
}
</script>

<style>
</style>
