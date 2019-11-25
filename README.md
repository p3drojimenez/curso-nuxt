# 📗 Clase 37 Insertando datos en Firebase(firestore):

## Creando un formulario:

He diseñado un formulario muy sencillo, por lo que antes de empezar te recomiendo que copiescódigo del formulario que se encuentra al final de las notas y lo pegues en tu componente `create.vue`

Una vez tengas el formulario y analices un poco el código, veras algunas cosas interesantes.

- Hemos creado un objeto `restaurant` para guardar todas las propiedades del restaurante.
- La propiedad `slug`, es una propiedad computada y se autogenera dependiendo del nombre, esto es una práctica común y una buena forma de usar la ventaja de la **computed properties**

Primero, creamos la propiedad *slug* y le aplicamos una transformación para quitar los espacios en blanco y sustituirlos por `-`. Después hemos creado un watcher sobre la misma propiedad computada, de forma que cuando cambie la asigne a nuestro modelo de datos `restaurant.slug`.

```js
 watch: {
    slug() {
      this.restaurant.slug = this.slug
    }
  },
  computed: {
    slug() {
      if (this.restaurant.name) {
        return this.restaurant.name.replace(/ /g, '-')
      } else {
        return null
      }
    }
  },
```

- `Selects`:

Vuejs maneja perfectamente los cambios en los `selects`, por lo que solo debemos asignar la directiva v-model a nuestro modelo.

```js
<select v-model="restaurant.category">
  <option>Select dropdown</option>
  <option value="Brunch">Brunch</option>
  <option value="Burgers">Burgers</option>
  <option value="Mediterranean">Mediterranean</option>
  <option value="Italian">Italian</option>
</select>
```

- `$router.back()` o `this.$router.back()`: Podemos lanzar un evento `back()` de forma programática y regresar a la página de la que venia el usuario.

  Dependiendo de donde llamemos a `$router.back()` debemos usar el contexto `this` o no.

### Insertando datos en Firebase:

La parte realemnte interesante es la siguiente:

```js
import { db } from '~/plugins/firebase'
...
...
methods: {
  onSubmitButton() {
    const response = db.collection('restaurants').add(this.restaurant)
    response.then(() => {
      this.$router.back()
    })
  }
}
```

Firebase se intergra tan bien con Nuxtjs que con una simple linea podemos realizar un `insert` y crear un nuevo documento.

```js
const response = db.collection('restaurants').add(this.restaurant)
```

El método **add**, retorna una promesa que podemos gestionar como nosotros queramos, en nuestro ejemplo, una vez resuelta, realizamos `this.$router.back()` para volver al listado.


**Formulario**

```html
<template>
  <div class="section">
    <div class="columns">
      <div class="column is-6 is-offset-3">
        <div class="columns">
          <div class="column">
            <h2 class="title is-2">New Restaurant</h2>
          </div>
        </div>
        <div class="columns box">
          <div class="column">
            <div class="field">
              <label class="label">Name</label>
              <div class="control">
                <input
                  class="input"
                  type="text"
                  v-model="restaurant.name"
                  placeholder="restaurant name"
                />
              </div>
            </div>
            <div class="field">
              <label class="label">Slug</label>
              <div class="control">
                <input class="input" type="text" :placeholder="slug" disabled />
              </div>
            </div>
            <div class="field">
              <label class="label">Image</label>
              <div class="control">
                <input
                  v-model="restaurant.image"
                  class="input"
                  type="text"
                  placeholder="https://...."
                />
              </div>
            </div>
            <div class="field">
              <label class="label">Description</label>
              <div class="control">
                <input
                  v-model="restaurant.description"
                  class="input"
                  type="text"
                  placeholder="description"
                />
              </div>
            </div>
            <div class="field">
              <label class="label">Address</label>
              <div class="control">
                <input
                  v-model="restaurant.address"
                  class="input"
                  type="text"
                  placeholder="address"
                />
              </div>
            </div>
            <div class="field">
              <label class="label">Cities</label>
              <div class="control">
                <div class="select">
                  <select v-model="restaurant.city">
                    <option>Select dropdown</option>
                    <option value="Madrid">Madrid</option>
                    <option value="Barcelona">Barcelona</option>
                    <option value="Valencia">Valencia</option>
                  </select>
                </div>
              </div>
            </div>
            <div class="field">
              <label class="label">Category</label>
              <div class="control">
                <div class="select">
                  <select v-model="restaurant.category">
                    <option>Select dropdown</option>
                    <option value="Brunch">Brunch</option>
                    <option value="Burgers">Burgers</option>
                    <option value="Mediterranean">Mediterranean</option>
                    <option value="Italian">Italian</option>
                  </select>
                </div>
              </div>
            </div>
            <div class="field">
              <label class="label">Text</label>
              <div class="control">
                <textarea
                  v-model="restaurant.text"
                  class="textarea"
                  type="textarea"
                  rows="10"
                  placeholder="text"
                />
              </div>
            </div>
            <div class="field">
              <div class="control has-text-centered">
                <button
                  class="button is-danger"
                  type="button"
                  @click="$router.back()"
                >
                  Cancel
                </button>
                <button
                  class="button is-link"
                  type="button"
                  @click.prevent="onSubmitButton"
                >
                  Save
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { db } from '~/plugins/firebase'
export default {
  data() {
    return {
      restaurant: {
        name: null,
        description: null,
        image: null,
        text: null,
        slug: null,
        address: null,
        city: null,
        category: null
      }
    }
  },
  watch: {
    slug() {
      this.restaurant.slug = this.slug
    }
  },
  computed: {
    slug() {
      if (this.restaurant.name) {
        return this.restaurant.name.replace(/ /g, '-')
      } else {
        return null
      }
    }
  },
  methods: {
    onSubmitButton() {
      // console.log(db)
    }
  }
}
</script>

<style lang="scss" scoped></style>
```

### 📚 Referencias y ayudas
- [Firebase](https://firebase.google.com/docs/projects/learn-more?hl=es)
- [Guía Oficial de Nuxtjs](https://nuxtjs.org/guide)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)