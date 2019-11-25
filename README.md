# 📗 Clase 32 Solución del reto:

## Todos los restaurantes de una categoria en concreto


```js
 async asyncData({ params }) {
    try {
      /* petición getRestaurantsByCategory() */
        const payload = {
          category: params.category
        }
        const { data } = await api.getRestaurantsByCategory(payload)
        return { restaurants: data }
    } catch (error) {
      console.log({ statusCode: 404, message: 'Category not found' })
    }
  }
```

El código es muy parecido al que teniamos en `index.vue` solo que ahora hacemos la petición a `getRestaurantsByCategory()` y le pasamos el payload con la categoria.

Si ahora vamos a nuestro fichero **api.js** y escribimos la petición
`getRestaurantsByCategory()` estaremos retornando todos los restaurantes de la categoria que le pasemos.

```js
api.getRestaurantsByCategory = ({category}) => {
  return apiGet('restaurants?category=' + category)
}
```

Como ves, estamos usando una forma más limpia de ver el código y de obtener propiedades de un objeto de una manera más limpia. Cuando vemos que entre corchetes una propiedad, quiere decir que estamos recuperando una propiedad especifica, en este caso, category y creando una variable con el mismo nombre. Otra forma de escribirlo, seria asi:

```js
const category = payload.category
```

## Retornando un restaurnate concreto.

Vamos a escribir el código necesario para realizar la petición GET, pero en este caso usaremos el parametro `_slug`.

```js
async asyncData({ params }) {
  try {
    const payload = {
      slug: params.slug
    }
    const { data } = await api.getOneRestaurant(payload)
      return { restaurant: data.shift() }
  } catch (error) {
    console.log({ statusCode: 404, message: 'Restaurant not found' })
  }
}
```

De la misma manera, creamos un objeto payload, con una propiedad llamada slug, que inicializamos con el paramero slug que recibe el componente. Y hacemos una peticion get de nuestro servicio api.

Si nos vamos a nuestro fichero **api.js** y escribimos la funcion `getOneRestaurant()`, tendremos el detalle del restaurante.


```js
api.getOneRestaurant = ({ slug }) => {
  return apiGet('restaurants?slug=' + slug)
}
```
