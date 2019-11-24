# 📗 Clase 17 Propiedades Computadas:


## Computed Properties

Las computed properties son sencillamente funciones que se comportan dentro de un componente como una propiedad. Esta caracteristica nos ayuda a generar datos reactivos sin tener que estar llamando a funciones o realizando calculos antes de renderizar las propiedades en html.

Para crear una propiedad computada debemos hacerlo usando la propiedad **computed**. En nuestro ejemplo hemos escrito una función que retorna el valor de la propiedad **message** pero invertido:

```js
computed: {
  messageResersed() {
    return this.message.split('').reverse().join('')
  }
}
```


Dentro de nuestro código HTML, podemos renderizar esta propiedad mediante una expresión al igual que las propiedades del modelo del componente:

```html
<p>Mensaje invertido: {{ messageResersed }}</p>
```

## Watchers

Son observadores que se activan cuando el valor de una propiedad de modifica. Para crear un watcher debemos hacerlo mediante la propiedad **watcher** de vuejs y dentro escribir el observador con el mismo nombre de la propiedad que queremos que escuche. En nuestro caso, hemos usado la propiedad **name** 

```js
watch: {
  name() {
    if(this.name.length > 5) {
      this.error = "Nombre demasiado largo"
    } else {
      this.error = ''
    }
  }
}
```

Desde este momento, cuando la propiedad `name` tenga más de 5 caracteres, saltara un error que se renderizada.

```html
 <p v-if="error != '' " class="tag is-warning">{{ error }} </p>
```

**No olvides crear la propiedad `error: ''` en el modelo.**

```js
data() {
    return {
      ....
      name: '',
      error: ''
    }
  },
```

### ⚒️ RECOMENDACIÓN:

### 📚 Referencias y ayudas
- [Computed Properties](https://vuejs.org/v2/guide/computed.html)
- [Bulma io](https://bulma.io/)
- [Single File Components](https://vuejs.org/v2/guide/single-file-components.html)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)