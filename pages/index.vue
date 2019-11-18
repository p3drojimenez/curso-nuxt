<template>
  <div>
    <Hero @onShowBanner="changeShowBanneValue">
      <Banner slot="header" style="width: 790px" v-if="showBanner" />
      <Slogan slot="header" style="width: 790px" v-else/>
    </Hero>
    <div class="container">
      <section class="section">
        <RestaurantCard
          :name="restaurant.name"
          :description="restaurant.description"
          :category="restaurant.category"
          :slug="restaurant.slug"
          :likes="restaurant.likes"
          v-on:onLikeButton="sumLikes(index)"
          v-for="(restaurant, index) in restaurants"
          :key="index"
        />
      </section>
    </div>
  </div>
</template>

<script>
import RestaurantCard from "~/components/RestaurantCard"
import Hero from "~/components/Hero"
import Banner from "~/components/banner"
import Slogan from "~/components/Slogan"
import api from '~/services/api'

export default {
  components: {
    RestaurantCard,
    Hero,
    Banner,
    Slogan
  },
  async created(){
    const response = await api.getRestaurants()
    if(response.status == 200) {
      this.restaurants = response.data
    }
  },
  data() {
    return {
      likes: 0,
      showBanner: true,
      restaurants: []
    }
  },
  methods: {
    sumLikes(index) {
      this.restaurants[index].likes = this.restaurants[index].likes + 1
    },
    changeShowBanneValue() {
      this.showBanner = !this.showBanner
    }
  }
}
</script>

<style>
</style>
