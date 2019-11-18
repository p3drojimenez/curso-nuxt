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
            Restaurant Name
          </p>
          <div class="columns">
            <div class="column">
              <span class="is-category tag">Category</span>
            </div>
            <div class="column has-text-right">
              <button class="button is-info">0</button>
            </div>
          </div>
        </div>
      </div>
      <div class="content">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit.Phasellus nec
        iaculis mauris.<a href="">more info</a>.
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style scoped>
.restaurant-name {
  font-size: 30px;
  color: #8ae6ff;
}
</style>