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
                <a :href="category">
                  {{ category }}
                </a>
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
        <a v-bind:href="category +'/'+ slug">more info</a>.
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      defaul: ''
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
    sumLikes() {
      this.$emit('onLikeButton')
      // this.likes = this.likes + 1
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