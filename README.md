# 📗 Clase 39 Actualizando datos en Firebase(firestore)

## Realizando la petición del documento:

Primero, tenemos que crear una vista para poder mostrar el formulario con los campos del restaurante, para ello y como cada restaurante es único, vamos a crear un componente dentro de la carpera *admin* llamandolo `_id.vue`, de tal forma que podamos desde la lista de restaurantes ver cada restaurante en concreto filtrandolo por su *ID* en firebase.

**pages/admin/_id.vue**

Vamos a practicamente reutilizar el mismo formulario que usamos en `create.vue`, pero debemos hacer algunas modificaciones:

- **Slug**: El slug, ya no se puede modificar, por lo que debemos eliminar toda la lógica que generaba esa url. Ahora sera una simple propiedad del objeto `restaurant`.

  ```json
  <label class="label">Slug</label>
  <div class="control">
    <input
      class="input"
      type="text"
      :placeholder="restaurant.slug"
      disabled
    />
  </div>
  ```

- Debemos interceptar el parametro `id` que nos envia la ruta anterior, eso lo haremos en el `hook created()`.

  ```js
  created() {
      const id = this.$route.params.id
  }
  ```

- Cambiar el método `onSubmitButton` por `onUpdateButton`

  ```html
  <button
    class="button is-link"
    type="button"
    @click.prevent="onUpdateButton"
  >
    Update
  </button>
  ```

  - Debemos crear una referencia del documento para poder actualizarlo

  ```js
  data() {
      return {
        restaurant: {},
        ref: null
      }
    },
  ```

  - Crear referencia del documento que vamos a modificar (para después actualizarlo).
  
  `this.ref = db.collection('restaurants').doc(id)`
   
  - Realizar la consulta del documento, si existe, asocia el documento a nuestro modelo `restaurant` si no, mostrara un mensaje por consola.

  ```js
    this.ref = db.collection('restaurants').doc(this.$route.params.id)
    const response = this.ref.get()
    response.then(doc => {
      if(doc.exists) {
        this.restaurant = doc.data()
      }
    })
  ```

  - Una vez que tenemos el documento y el formulario, debemos crear la lógica para actualizar el documento:

  ```js
  onUpdateButton() {
    this.ref.update(this.restaurant).then(() => {
      this.$router.back()
    })
  }
  ```
  
  > Como hemos referenciado el documento en nuestro modelo no es necesario volver a realizar la consulta. Si todo va bien, una vez actualizado retornara a la lista de restaurantes con el valor modificado.



### 📚 Referencias y ayudas
- [Firebase](https://firebase.google.com/docs/projects/learn-more?hl=es)
- [Guía Oficial de Nuxtjs](https://nuxtjs.org/guide)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)