# 📗 Clase 16 Layouts

**Resumen**
~~~
En esta clase aprenderás a crear Layouts para hacer que tus páginas sean más escalables y que todas mantengan los mismos estilos.
~~~

Un layout es un componente de vuejs que podemos usar para crear un theme de nuestro proyecto y aplicar a todas las páginas o solo a un grupo de ellas.

Para crear un Layout debes hacerlo en el directorio **layouts**.

Cada layout debe incuir el componente de nuxtjs `<nuxt/>`que sera el encargado de renderizar las páginas, en definitiva, nuxtjs sustituira ese componente por el corresponiente dentro del direcotio de *pages*

## Header

Vamos a crear un componente `header.vue` para que se pueda ver desde todas las páginas la misma cabecera.

*NOTA*: Recuerda importar `logo.png` en el directorio **static** para no tener problemas o errores.

**layouts/header.vue**
```html
<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand logo">
      <img src="@/static/logo.png" alt="FoodAdvisor logo" />
    </div>
    <div class="navbar-end">
      <div class="navbar-item">
        <div class="buttons">
          <a href="/login" class="button is-light">
            Log in
          </a>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {}
</script>
<style scoped>
.logo {
  width: 100px;
  margin: 0 20px;
}
</style>
```

Si modificamos el layout por defecto:

**layouts/default.vue**

```html
<template>
  <div>
    <Header />
    <nuxt />
  </div>
</template>

<script>
import Header from "~/layouts/header"

export default {
  components: {
    Header
  }
}
</script>
```

Ahora veremos una cabecera en todas las páginas.

![resultado header](assets/capturas/clase16/resultado.png)


## Layout Login.vue 


Vamos a crear un layout especifico para las páginas que no nos interesa mostrar la cabecera. Para ello creamos un nuevo layout llamado `login.vue`.

**layouts/login.vue**

```html
<template>
  <div>
    <nuxt />
  </div>
</template>
```
**NOTA**: Recuerda siempre incluir el componente <nuxt/>

En este componente, por el momento no vamos a usar nada de javascript ni estilos, por lo que no es necesario incluir las etiquetas.

Ahora, vamos a crear una página `login.vue` y mediante la propiedad `layout` le indicaremos que ese componente (página) use el layout que acabamos de crear.

```html
<template>
  <div class="box column is-4 is-offset-4 box-login">
    <div class="columns">
      <div class="column has-text-centered">
        <img src="@/static/logo.png" />
      </div>
    </div>
    <div class="columns">
      <div class="column has-text-left">
        <input class="input" type="text" placeholder="email" />
      </div>
    </div>
    <div class="columns">
      <div class="column has-text-left">
        <input class="input" type="text" placeholder="contraseña" />
      </div>
    </div>
    <div class="columns">
      <div class="column has-text-centered">
        <nuxt-link to="/" class="button is-danger">Cancelar</nuxt-link>
        <nuxt-link to="/admin" class="button is-primary">Login</nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  layout: 'login'
}
</script>

<style>
.box-login {
  margin-top: 30px;
}
</style>
```


### ⚒️ RECOMENDACIÓN:

### 📚 Referencias y ayudas

- [Vuejs Router](https://router.vuejs.org/guide/essentials/dynamic-matching.html)
- [Nuxtjs Rutas dinámicas](https://nuxtjs.org/guide/routing/)
- [Bulma io](https://bulma.io/)
- [Single File Components](https://vuejs.org/v2/guide/single-file-components.html)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)