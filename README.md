# 📗 Clase 28 Peticiones POST:

Para poder realizar una petición **POST** debemos crear una nueva función dentro del fichero `api.js` que sea la encargada mediante **AXIOS** de realizarla.

AXIOS acepta una propiedad llamada **body** que serán los datos que se enviaran a la API. En nuestro caso, asociaremos esa propiedad **body** con el objeto **payload**


**api.js**

```js
async function apiPost(url, payload) {
  const config = {
    method: 'get',
    mode: 'cors',
    headers: {
      'Access-Control-Allow-Origin': '*'
    },
    body: payload
  }
  const urlCall = API_URL + url
  try {
    const response = await axios.post(urlCall, config)
    return response
  } catch (error) {
    console.log(error)
  }
}
```

El método `api.postSubcribeUser()` recive por parametro el payload (los datos que enviamos) que a su vez, usa la función *apiPost* para que realice la petición. Este método retorna directamente la respuesta en forma de promesa.

```js
api.postSubcribeUser = payload => {
  return apiPost('users', payload)
}
```

### Objeto Payload 

Usar un objeto en vez de propiedades directamente, hace que nuestra función no este acoplada a los datos y podamos reutilizar esa funcion para todas las peticiones **POST**.


### Modificando `Slogan.vue`

**components/slogan.vue**
```html
<template>
  <div>
    <h2 class="title is-2">FoodAdvisor, tu web de restaurantes</h2>
    <div class="subcribe" v-if="!is_subscribe">
      <input type="text" v-model="email" class="input email" placeholder="email..."/>
      <button class="button is-info" @click="subscribe">Suscribirse</button>
    </div>
    <div v-else>
      <p>Gracias! Ahora encontrás cada semana una recomendación en tu email.</p>
    </div>
  </div>
</template>

<style scoped>
.subcribe{
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.email {
 width: 80%;
}
</style>

<script>
import api from '~/services/api'
export default {
  data() {
    return {
      email: '',
      is_subscribe: false
    }
  },
  methods: {
    async subscribe() {
      const payload = {
        email: this.email
      }
      const response = await api.postSubcribeUser(payload)
      if(response.status == 201) { // 201 : Created
        this.is_subscribe = true
      }
    }
  }
}
</script>
```

### ⚒️ RECOMENDACIÓN:

Te recomiendo que leas sobre async y await y que entiendas el funcionamiendo sobre las peticiones asincronas en Javascript. Te resultara mas facil comprender todo el proceso de peticiones HTTP.

### 📚 Referencias y ayudas
- [AXIOS](https://es.vuejs.org/v2/cookbook/using-axios-to-consume-apis.html)
- [Async & await](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/funcion_asincrona)
- [Estados de respuesta HTTP](https://developer.mozilla.org/es/docs/Web/HTTP/Status)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)