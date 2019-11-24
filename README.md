# 📗 Clase 12: Data Binging

## Qué es el data Binding:

El Data Binding es la forma que tenemos de unir nuestro modelo de datos con los atributos de los elementos del código HTML. Para ello, usamos la directiva `v-bind`:

Por ejemplo: 

```html
<a v-bind:href="restaurant.url">More info</a>
```

## Expresiones

Para poder renderizar una variable creada en nuestro modelo debemos usar el doble corchete ``{{ }}`` y dentro escribir el nombre de la propiedad definida en el modelo del componente.

``{{ message }}``

```js
data() {
  return {
    message: "hola OpenWebinar"
  }
}
```

Dentro de una expresión, podemos ejecutar algunas funciones que modifiquen el valor o el contenido de la variable, auque no es muy recomendable, ya que para situaciones como esta, existe otra herramienta de vuejs llamada **Computed Properties**. 

Un ejemplo sería:

``{{ message.toLowerCase() }}``

**pages/directivas.vue**

```html
<template>
  <div>
    <p>{{ message }}</p>
    <p>{{ saludo + despedida}}</p>
    {{ 1 + 3 }}
  </div>
</template>

<script>
  export default {
    data() {
      return {
        message: 'hola OpenWebinars',
        saludo: "hola",
        despedida: "adios"
      }
    }
  }
</script>
```

### ⚒️ RECOMENDACIÓN:

### 📚 Referencias y ayudas

- [Bulma io](https://bulma.io/)
- [Single File Components](https://vuejs.org/v2/guide/single-file-components.html)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)