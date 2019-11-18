<template>
  <div class="container">
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
import RestaurantCard from "../components/RestaurantCard"
export default {
  components: {
    RestaurantCard
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
