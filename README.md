# 📗 Clase 26 Configurando servicios:

Los servicios, son una manera de abstraer nuestras peticiones HTTP del código. De esa manera, conseguiremos que nuestro código este bajamente acomplado a una dirección URL en concreto. 

Normalmente cuando consumimos una API pública o privada podemos encontrarnos diferentes versiones de la misma, es por eso que es recomendable que toda la aplicación y llamadas a la API desde los componentes sea totalmente agnostica a ella.

La API que vamos a usar en nuestro proyecto esta creada con un servicio gratuito que podréis encontrar en: [https://my-json-server.typicode.com](https://my-json-server.typicode.com). Este servicio, utiliza un repositorio publico creado por nosotros mismos para simular las peticiones `GET`, `POST`, `PUT` y `DELETE`.

Para el curso, he creado un repositorio en mi Github personal [@p3drojimenez](https://my-json-server.typicode.com/p3drojimenez/restaurants) el cual, podeis clonar y realizar peticiones `PULL REQUEST` (Buena práctica para aprender el flujo de trabajo con GIT)



### Creando nuestra constante de URL:

Primero de todo, vamos a configurar una URL que sera nuestra base de url para todas las peticiones.

Creamos un directorio `services` en nuestro proyecto y dentro creamos un fichero `apiConfig.js`

**services/apiConfig.js**

```js
const API_URL = 'https://my-json-server.typicode.com/p3drojimenez/restaurants/'
export default API_URL
```

Ahora, vamos a crear un fichero donde centralizaremos todas las peticiones **publicas** de nuestro proyecto.

**services/api.js**
```js
import axios from 'axios'
import API_URL from '~/services/apiConfig'

const api = {}

async function apiCall(url) {
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
  return apiCall('restaurants')
}

export default api
```

y por último, vamos a realizar la petición `GET` desde luestro `index.vue` para mostrar la lista de restaurantes que dispone la API.

Para ello, debemos importar el servicio que hemos creado en el paso anterior:

``import api from '~/services/api'```

Gracias a **ECMAScript 6** podemos incorporar peticiones `ASYNC / AWAIT` en nuestro componente de una manera muy sencilla y facilmente entendible.

Crearemos dentro del `hook created()`, tal como vimos en la clase de *ciclo de vida de un componente* es un buen lugar para realizar peticiones al servidor, la llamada asincrona a la api para que nos retorne los restaurantes. 

Una vez resulta la petición asignaremos los datos a nuestro modelo.

```js
async created() {
  const response = await api.getRestaurants()
  this.restaurants = response.data
}
```


**pages/index.vue**

```js
<script>

import api from '~/services/api'
export default {
  components: {
    RestaurantCard,
    HeroComponent,
    // SpoganComponent
    ImageComponent
  },
  async created() {
    const response = await api.getRestaurants()
    this.restaurants = response.data
  },
  data() {
    return {
      restaurants: []
    }
  },
  methods: {
    sumLikes(index) {
      this.restaurants[index].likes++
    }
  }
}
</script>
```

### 📚 Referencias y ayudas
- [AXIOS](https://es.vuejs.org/v2/cookbook/using-axios-to-consume-apis.html)
- [Async & await](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/funcion_asincrona)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)