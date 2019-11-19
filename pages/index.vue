<template>
  <div>
    <Hero @onShowBanner="changeShowBanneValue">
      <Banner slot="header" style="width: 790px" v-if="showBanner" />
      <Slogan slot="header" style="width: 790px" v-else/>
    </Hero>
    <div class="container">
      <section class="section">
        <div class="columns is-multiline">
          <RestaurantCard
            :name="restaurant.name"
            :description="restaurant.description"
            :category="restaurant.category"
            :slug="restaurant.slug"
            :likes="restaurant.likes"
            :image="restaurant.image"
            v-on:onLikeButton="sumLikes(restaurant)"
            v-for="(restaurant, index) in restaurants"
            :key="index"
            class="restaurant-card"
           
          />
        </div>
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
  async asyncData() {
    try {
      const { data } = await api.getRestaurants()
      return { restaurants: data }
    } catch {
      return { restaurants: [] }
    }
  },
  // async created(){
  //   const response = await api.getRestaurants()
  //   if(response.status == 200) {
  //     this.restaurants = response.data
  //   }
  // },
  data() {
    return {
      likes: 0,
      showBanner: true,
      restaurants: []
    }
  },
  methods: {
    async sumLikes(restaurant) {
      const payload = {
        id: restaurant.id,
        data: {
          likes: restaurant.likes + 1
        }
      }
      const response = await api.putSumRestaurantLikes(payload)
      console.log(response)
      if(response.status == 200) {
        restaurant.likes++
      }
    },
    changeShowBanneValue() {
      this.showBanner = !this.showBanner
    }
  }
}
</script>

<style>
.restaurant-card {
  margin: 10px 10px;
  max-width: 300px;
}
</style>
