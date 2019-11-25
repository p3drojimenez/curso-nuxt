# 📗 Clase 20 Comunicación de padres a hijos:

### Props:

Las propiedades con variables que podemos inyectar a nuestros componentes. De manera que el componente sea independiente del modelo de datos.

Primero, debemos adaptar nuetro componente `RestaurantCard.vue` para que reciva las propiedades de su componente **padre**, en este caso, nuestro componente `index.vue`.

### Modificando `RestaurantCard.vue`

Debemos añadir el objeto `props: {}` dentro de nuestro componente y dentro de el, definiremos que propiedades y de que tipo serán.

**RestauraCard.vue**
```js 
export default {
    props: {
    name: {
      type: String,
      default: ''
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
    }
  },
}
```

Ahora, podemos llamar a esas propiedades enviadas por el `componente padre` de la misma manera que haciamos antes con las propiedades del modelo.

Una buena práctica, es definir siempre el tipo de datos que va a recibir esa propiedad y asignar un valor por defecto. Asi, de esa manera nuestros componentes serán menos propensos a bugs y errores.

Vamos a modificar nuestro componente `RestaurantCard.vue` añadiendole alguna propuedad más.

Añadiendo las propiedades:

```js
export default {
  props: {
    name: {
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
    description: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      likes: 0
    }
  },
  methods: {
    onDetailBoton() {
      this.$router.push(this.slug)
    },
    onLikeButton() {
      this.likes = this.likes + 1
      // this.likes++
    }
  }
}
</script>
```

Y ahora, podemos enviar propiedades al componente:

```html
<RestaurantCard
  name="Restaurant Name"
  description="Description......"
  slug="restaurant-slug"
  category="Burguer"
/>
```

Añade el siguiente array **restaurants**, asi tendrás más datos que mostrar.

```js
data() {
  return {
    restaurants: [
      {
        name: 'Manairo',
        slug: 'manairo',
        category: 'Italian',
        description:
          'Lorem Ipsum is simply dummy text of the printing and typesetting industry.'
      },
      {
        name: 'Gorría Restaurant',
        slug: 'gorria-restaurant',
        category: 'Asian',
        description:
          'Lorem Ipsum is simply dummy text of the printing and typesetting industry.'
      },
      {
        name: 'Dans le Noir?',
        slug: 'dans-noir',
        category: 'Mediterranean',
        description:
          'Lorem Ipsum is simply dummy text of the printing and typesetting industry.'
      }
    ]
  }
}
```

Una vez que le hemos enviado propiedades al componente, podemos "casi" asegurar que ese componente es totalmente reutilizable en cualquier parte de nuestro proyecto, o incluso importarlo en otros proyectos. El objetivo principal de los componentes es que sean totalmente independientes y aislados de cualquier lógica o modelo de datos, de esa manera **testealos** y **reutilizarlos** será mucho más fácil.

### ⚒️ RECOMENDACIÓN:

Añade más elementos en el array de restaurantes y/o añade nuevas propiedades para mejorar componente.

### 📚 Referencias y ayudas

- [Ciclo de vida e Vuejs](https://vuejs.org/v2/guide/instance.html)
- [Single File Components](https://vuejs.org/v2/guide/single-file-components.html)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)