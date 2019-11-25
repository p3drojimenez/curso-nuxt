# 📗 Clase 43 Autentificación con Firebase Usuario

### Login de usuario:

En esta clase vamos a modificar el formulario de inidio de sesión que preparamos en las clases anteriores para que podamos realizar login con el servicio de autentificación de Google.

Primero abrimos el fichero de `Login.vue`.

Creamos dos propiedades:

```js
data() {
  return {
    email: '',
    password: ''
  }
},
```

Modificamos el botón de **Login**

```html
<button @click="onLogin" class="button is-primary">
  Login
</button>
```

Y creamos el método `onLogin()`:

```js
methods: {
  onLogin() {
    console.log("Login!!")
    const response = firebase.auth().signInWithEmailAndPassword(this.email, this.password)
    response.then(data => {
      this.$router.push('admin')
    })
  }
}
```

Para solucionar el problema de logout de un usuario sin usar Store (Vuex), modificaremos el método created() para forzar el logout siempre que se carge este componente.

```js
created() {
  firebase.auth().signOut()
},
```

### 📚 Referencias y ayudas
- [Firebase](https://firebase.google.com/docs/projects/learn-more?hl=es)
- [Middlewares](https://nuxtjs.org/api/pages-middleware/)
- [Guía Oficial de Nuxtjs](https://nuxtjs.org/guide)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)