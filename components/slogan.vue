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