# 📗 Clase 36 Plugins-Configurando Firebase:

Los plugins nos van a permitir utilizar nuestras librerias o librerias de terceros, como firebase cada vez que lo necesitemos. 

Se inicializa siempre antes de de iniciar la instancia de Vuejs, por lo que estará siempre disponible.

Es un buen sitio para escribir nuestros helpers o como veremos más adelante el *script de google analytics*.

### Configurando FoodAdvisor con firebase

Primero debemos instalar la libreria de firebase:

```shell
npm install firebase --save
```

Podemos comprobar que se ha instalado correctamente en nuestro fichero `package.json` 

```js
"dependencies": {
  ...
  "firebase": "^7.2.2",
  ...
}
```

En nuestro proyecto hemos utilizado la última versión `7.2.2`.

Ahora crearemos un fichero `firebase.js` dentro del directorio **plugins**

**plugins/firebase.js**

```js
import firebase from 'firebase/app'
import 'firebase/firestore'

if (!firebase.apps.length) {
  const firebaseConfig = {
    apiKey: '',
    authDomain: '',
    databaseURL: '',
    projectId: '',
    storageBucket: '',
    messagingSenderId: '',
    appId: ''
  }
  // Initialize Firebase
  firebase.initializeApp(firebaseConfig)
}
const db = firebase.firestore()
export { db }
```

Sustituye los valores de las propiedades de `firebaseConfig` por los tuyos propios.

### Probando que todo funciona.

Una manera rápida es realizar un `console.log()` de la instancia de firebase que acabamos de crear.

Para ello, en vamos a crear una nueva página  **pages/admin/index.vue** vamos a importar nuestro *plugin* y llamarlo desde el método `created()`.

 **pages/admin/index.vue**
```html
<template>
  <div>
    <div class="columns">
      <div class="column has-text-centered">
        <p>Esta es la página privada</p>
        <nuxt-link to="/" class="button is-info">
          Home
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
import { db } from '~/plugins/firebase'
export default {
  created() {
    console.log(db)
  }
}
</script>
```

Si todo va bien, veremos por consola algo parecido a esto:

![imagen firestore](assets/capturas/clase36/firestore.png)

### ⚒️ RECOMENDACIÓN:

### 📚 Referencias y ayudas
- [Fireabase](https://firebase.google.com/docs/projects/learn-more?hl=es)
- [Guía Oficial de Nuxtjs](https://nuxtjs.org/guide)