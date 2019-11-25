# 📗 Clase 22 Slots:


Los Slots nos perminten inyectar código HTML dentro de un componente o podrer injectar un componente dentro de otro componente sin tener que importarlo desde el componente hijo.

Son muy usados por ejemplo, para crear un tipo de botón, con unos estilos determinados y queramos por ejemplo en un momento dato, renderizar solo un texto, como por ejemplo, "Registrate" y en otras ocasiones, un texto y un icono, y en otras un texto un icono y una imagen.

Si no usaramos los slots, deberiamos hacer estas validaciones con las propiedades y hacer un renderizado condicional con directivas `v-if`. 

Para verlo más claro, vamos a escribir un componente y asi seguro que se ven más claras sus ventajas.

Creamos un componente llamado `Hero.vue` con una estructura sencilla.

```html
<template>
  <div>
    Hero
  </div>
</template>

<script>
  export default {
    
  }
</script>

<style lang="scss" scoped>

</style>
```

Y vamos a importarlo desde nuestro`index.vue` para que podamos ver que es lo que va suceciendo.

Para poder crear esa parte en la cual inyectaremos el codigo desde el componente *padre* debemos modificar el componente `hero.vue`, creando un elemento llamado `slot` con el atributo **name** al que referenciaremos desde el componente padre.


```html
<slot name="header"></slot>
```

Ahora en el componente Padre, (*index.vue*), vamos a modifiar el codigo, añadiendo un elemento div, al que le pasaremos el atributo *slot* con el nombre que acabamos de asignar.

```html
<Hero >
  <div slot="header">
    <p>hola</p>
    <h1 class="title">TÍTULO</h1>
  </div>
</Hero>
```

Es importante que el componente no este cerrado en la misma linea, y que todo lo que metamos dentro de el, le corresponda un atributo slot, ya que de otra manera no se renderizara.

Ahora que vemos que funciona, voy a darle un poco de formato al componente, para que quede mejor con nuestro proyecto.

```html
<template>
  <section class="hero is-primary">
    <div class="hero-body">
      <slot class="container" name="header">
      </slot>
    </div>
  </section>
</template>
```

Tambien vamos a modificar el `index.vue` para que realmente el componente que acabamos tenga el estilo apropiado:


```html
<template>
  <div>
    <Hero >
      <div slot="header">
        <p>hola</p>
        <h1 class="title">TÍTULO</h1>
      </div>
    </Hero>
    <div class="container">
      <section class="section">
        <RestaurantCard
          name="Restaurant Name"
          description="Description......"
          slug="restaurant-slug"
          category="Burguer"
          :likes="likes"
          v-on:onLikeButton="sumRestaurantLikes"
        />
      </section>
    </div>
  </div>
</template>

<script>
import RestaurantCard from '~/components/RestaurantCard'
import Hero from '~/components/Hero'

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
    sumRestaurantLikes() {
      this.likes++
    }
  }
}
</script>
<style></style>
```

### ⚒️ RECOMENDACIÓN:

Trabajar con `slots` nos facilita mucho la reutilización de componentes y código. Si tienes que usar dos veces un mismo botón o componente, piensa si existe alguna manera de reutilizar el código creando un componente "plantilla" y puedas inyectar el código o componente que más te interese. Un buen uso, son botones, cards, tags...

### 📚 Referencias y ayudas
- [Slots en vuejs](https://es.vuejs.org/v2/guide/components-slots.html)
- [Bulma CSS Hero](https://bulma.io/documentation/layout/hero/)
- [Single File Components](https://vuejs.org/v2/guide/single-file-components.html)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)