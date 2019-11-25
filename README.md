# 📗 Clase 29 Peticiones PUT:

**api.js**

Creamos la funcion asincrona que realizara la petición usando el método PUT. 

```js
async function apiPut(url, payload) {
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
    const response = await axios.put(urlCall, config)
    console.log(response)
    return response
  } catch (error) {
    console.log(error)
  }
}
```

La función `putSumRestaurantLikes()` forma una url usando la propiedad **id** del objeto payload. Para crear esa URL, hemos usado los *Template Strings*, de esta manera, se entiende mejor la concatenación de strings y variables.

```js
api.putSumRestaurantLikes = payload => {
  const restaurantId = payload.id
  const url = `restaurants/${restaurantId}`
  return apiPut(url, payload.data)
}
```

**index.vue**

Se modifica tambien el método `sumRestaurantLikes()` el cual recive por parametro el objeto **restaurant**.

```js
async sumRestaurantLikes(restaurant) {
    const payload = {
      id: restaurant.id,
      data: {
        likes: restaurant.likes + 1
      }
    }
    const response = await api.putSumRestaurantLikes(payload)
    if(response.status == 200) {
      restaurant.likes++
    }
  },
```

### ⚒️ RECOMENDACIÓN:

Te recomiendo que leas sobre async y await y que entiendas el funcionamiendo sobre las peticiones asincronas en Javascript. Te resultara mas facil comprender todo el proceso de peticiones HTTP.

### 📚 Referencias y ayudas
- [AXIOS](https://es.vuejs.org/v2/cookbook/using-axios-to-consume-apis.html)
- [Async & await](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/funcion_asincrona)
- [Template Strings](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/template_strings)
- [Estados de respuesta HTTP](https://developer.mozilla.org/es/docs/Web/HTTP/Status)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)