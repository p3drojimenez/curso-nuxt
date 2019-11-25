# 📗 Clase 38 Listando datos en Firebase(firestore):

Para poder recuperar los datos de la base de datos, debemos realizar una petición a firebase sobre la colección `restaurants` y luego insertar cada documento en un array dentro de nuestro modelo de datos.

```js
created() {
  const data = db.collection('restaurants').get()
  data
    .then((snapshot) => {
      snapshot.forEach((doc) => {
        this.restaurans.push(doc.data())
      })
    })
    .catch((error) => {
      console.log(error)
    })
}
```

Por convención, Firebase llama `snapshot` a una "captura" del documento dentro de la colección, te recomiendo que lo llames de la misma manera, ya que toda la documentación oficial sigue ese patrón.

Después creamos en nuestro modelo de datos, el array restaurants, para después renderizarlo en la vista `{{ restaurants }}`

```js
  data() {
    return {
      restaurans: []
    }
  },
```

## Creando una tabla:

**admin/index.vue**

```html
<template>
  <div>
    <section class="section" >
      <div class="columns">
        <div class="column">
          <h2 class="title is-2">Resturantes</h2>
        </div>
      </div>
      <div class="table-container">
        <table class="table is-fullwidth is-bordered">
          <thead>
            <tr>
              <th>Id</th>
              <th>Restaurant name</th>
              <th>Actions</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(item, index) in restaurans" :key="index">
              <td>{{ item.id }}</td>
              <td>{{ item.name }}</td>
              <td>
                <nuxt-link class="button" :to="`admin/${item.id}`" >
                  Edit
                </nuxt-link>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </section>
  </div>
</template>
```

**admin/_id**

```html
<template>
  <div>
    {{ $route.params.id }}
    {{ restaurant }}
  </div>
</template>

<script>
import { db } from '~/plugins/firebase'
export default {
  data() {
    return {
      restaurant: null
    }
  },
  created() {
    const response = db.collection('restaurants').doc(this.$route.params.id).get()
    response.then(doc => {
      if(doc.exists) {
        this.restaurant = doc.data()
      }
    })
  }
}
</script>

<style scoped>

</style>
```

### ⚒️ RECOMENDACIÓN:


### 📚 Referencias y ayudas
- [Firebase](https://firebase.google.com/docs/projects/learn-more?hl=es)
- [Guía Oficial de Nuxtjs](https://nuxtjs.org/guide)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)