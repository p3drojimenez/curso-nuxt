# 📗 Clase 27 Peticiones GET:

Para poder realizar peticiones GET, debemos crera una función dentro de nuestro fichero **api.js**, que finalmente sera la encargada de realizar todas las peticiones por nosotros usando AXIOS.

Para las peticiones **GET** hemos escrito una función llamada `apiGet()` que recive por parametro la url del endPoint donde se encuentra el recurso. Al tener una constante API_URL donde anterior mente definimos ya base de la url del endpoint, solo debemos pasarle a la función la parte que necesitemos.

En este ejemplo queremos recuperar todos los restaurantes desde el endPoing:

```html
https://my-json-server.typicode.com/p3drojimenez/restaurants/restaurants
```

**api.js**

```js
import API_URL from './api.config'
import axios from 'axios'

const api = {}

async function apiGet(url) {
  const config = {
    method: 'get',
    mode: 'cors',
    headers: {
      'Access-Control-Allow-Origin': '*'
    }
  }
  const urlCall = API_URL + url
  try {
    const response = await axios.get(urlCall, config)
    return response
  } catch (error) {
    console.log(error)
  }
}

api.getRestaurants = () => {
  return apiGet('restaurants')
}

export default api
```


Modificamos nuestro componente `index.vue` usando el Hook created() para que realice una petición asincrona.

Una vez que se resuelve la llamada, si todo ha ido bien y el **status** de la respuesta es 200 (**[Todo ha salido ok](https://developer.mozilla.org/es/docs/Web/HTTP/Status)**), asignamos los datos con el array de restaurantes de nuestro modelo.

**index.vue**

```js
async created() {
  const response = await api.getRestaurants()
  if(response.status == 200) {
    this.restaurants = response.data
  }
},
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