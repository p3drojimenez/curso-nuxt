# 📗 Clase 45 Solución del reto


**pages/index.vue**

- Importamos `import { db } from '~/plugins/firebase'`

- Modificamos el hook created() para que realice la llamada a firebase.

```js
import { db } from '~/plugins/firebase'
...
created() {
  const data = db.collection('restaurants').get()
  data
    .then((snapshot) => {
      snapshot.forEach((doc) => {
        const restaurant = {
          id: doc.id,
          ...doc.data()
        }
        this.restaurants.push(restaurant)
      })
    })
    .catch((error) => {
      console.log(error)
    })
}
```

**pages/_category/_slug.vue**

- Modificamos el método asyncData

```js
<script>
// import api from '~/services/api'
import { db } from '~/plugins/firebase'

export default {
  async asyncData({ params }) {
    const ref = db.collection('restaurants').where('slug', '==', params.slug)
    let snapshot
    try {
      snapshot = await ref.get()
    } catch (e) {
      return { restaurant: {} }
    }
    return { restaurant: snapshot.docs.shift().data() }
  }
}
</script>
```
**pages/_category/index.vue**

- Borramos el componente asycnData y creamos la llamada desde `hook created` de forma asincrona

```js
<script>
import RestaurantCard from '~/components/RestaurantCard'
// import api from '~/services/api'
import { db } from '~/plugins/firebase'

export default {
  components: {
    RestaurantCard
  },
  data() {
    return {
      restaurants: []
    }
  },
  async created() {
    await db
      .collection('restaurants')
      .where('category', '==', this.$route.params.category)
      .get()
      .then((querySnapshot) => {
        querySnapshot.forEach((doc) => {
          this.restaurants.push(doc.data())
        })
      })
  }
}
</script>
```

Además se modifica el componente `RestaurantCard.vue` para que accepte la propiedad **image**.


### 📚 Referencias y ayudas
- [Firebase](https://firebase.google.com/docs/projects/learn-more?hl=es)
- [Middlewares](https://nuxtjs.org/api/pages-middleware/)
- [Guía Oficial de Nuxtjs](https://nuxtjs.org/guide)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)