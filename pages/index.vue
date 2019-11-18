<template>
  <div class="container">
    <section class="section">
      <RestaurantCard
        name="Bar Paco"
        description="Descripción del restaurante"
        category="burger"
        slug="bar-paco"
      />
    </section>
  </div>
</template>

<script>
import RestaurantCard from "../components/RestaurantCard"
export default {
  components: {
    RestaurantCard
  }
}
</script>

<style>
</style>
