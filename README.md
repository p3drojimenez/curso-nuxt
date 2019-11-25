# 📗 Clase 42 Autentificación con Firebase

### Configuración Auth en nuestro proyecto:

Una vez hemos realizado toda la configuración en firebase, pasamos a configurar nuestro proyecto.

El sistema de autentificación de firebase se basa basicamente en tres funciones: 

- `firebase.auth().signInWithEmailAndPassword(email, password)`:
  
  Hacemos login de un usuario mediante el método de email y contraseña.

- `firebase.auth().onAuthStateChanged()`:

  Validamos si el usuario sigue loguado en firebase o no, por lo tanto sera un buen método para comprobar si tiene acceso el usuario a ciertas rutas.

- `firebase.auth().signOut()`:

  Realiza la acción de logout de un usuario.

> Nota: Antes de nada, debemos añadir a nuestro fichero de configuración de fireabse, la libreria **auth**.

**plugins/firebase**
```js
import 'firebase/firebase-auth'
```
También debemos exportar la aplicación Firebase para que pueda ser importada por otras páginas.

```js
import firebase from 'firebase/app'
import 'firebase/firestore'
import 'firebase/firebase-auth'

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
export { db, firebase }
```

### Middlewares:

Una de las cosas que hacen potentes a Nuxtjs son los middlewares. Estos nos perminten realizar ciertas acciones antes de que una ruta se carge. Por ejemplo, realizar validaciones en rutas o restringir el acceso a ciertas partes de nuestra aplicación, como es nuestro caso.

Para crear nuestro middleware de autentificación debemos crear un fichero dentro del directorio **middleware** y llamarlo `auth.vue`.

```js
import { firebase } from '~/plugins/firebase'

export default function({ redirect }) {
  firebase.auth().onAuthStateChanged(function(user) {
    if (!user) {
      return redirect('/login')
    } else {
      console.log(user)
    }
  })
}
```

Este middleware comprobara con cada ruta si el usuario ha cambiado de estado (siguie o no logeado), y en caso de que no exista el usuario logueado, redirigira a nuestra página "login".

### Restringiendo rutas

Nuestro **Middleware** comprobara cada ruta que nosotros le digamos, podemos hacerlo mediante una expresión regular en el mismo middelware y poniendolo por defecto en nuestro fichero de configuración `nuxt.config.js` o indicarle expresamente en que rutas queremos que se cumpla esa validación.

En nuestro caso, ya que son tres rutas las que nos interesa proteger, vamos a configurarlas de la siguiente manera:

```js
export default {
  middleware: 'auth',
  ....
```

Solo necesitamos añadir la propiedad `middleware: 'auth'` en cada página que queramos restringir el acceso (todas las páginas bajo el directorio **admin**).

### ⚒️ RECOMENDACIÓN:

Una buena práctica es crear dos layouts diferentes para cada uno de los entornos y aplicar ahi directamte el middleware.

### 📚 Referencias y ayudas
- [Firebase](https://firebase.google.com/docs/projects/learn-more?hl=es)
- [Middlewares](https://nuxtjs.org/api/pages-middleware/)
- [Guía Oficial de Nuxtjs](https://nuxtjs.org/guide)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)