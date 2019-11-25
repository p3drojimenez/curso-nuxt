# 📗 Clase 34 Creando nuestro primer Test:

Vamos a escribir el primer test para el componente `RestaurantCard.vue`, ya que fue el primero que creamos.

Creamos un fichero llamado `RestaurantCard.spec.js` en el directorio **test** y escribimos un código parecido al que tenemos en `Logo.spec.js`. 

```js
import { mount } from '@vue/test-utils'
import RestaurantCard from '~/components/RestaurantCard'

describe('RestaurantCard', () => {
  test('is Mounted', () => {
    const wrapper = mount(RestaurantCard)
    expect(wrapper.isVisible()).toBe(true)
  })
})
```

Si ejecutamos ahora `npm test`, podemos ver que el test se completa y pasa sin problemas.

Ahora, vamos a comprobar que realmente, cuando le pasamos propiedades, el componente renderiza y se renderiza correctamente.Para ello, añadimos un poco más de lógica al test:

```js
import { mount } from '@vue/test-utils'
import RestaurantCard from '~/components/RestaurantCard'

describe('RestaurantCard', () => {
  const props = {
    id: 0,
    name: 'nombre',
    description: 'description',
    text: 'testo largo',
    slug: 'slug',
    category: 'categoria',
    city: 'ciudad',
    address: 'direccion',
    likes: 0,
    image: 'https://netlify.pedrojimenez.info/photosCursoOpenWebinar/restaurant08.jpg'
  }
  const wrapper = mount(RestaurantCard, { propsData: props })
  test('is Mounted', () => {
    expect(wrapper.isVueInstance()).toBe(true)
  })
  test('is rendering a restaurant', () => {
    expect(wrapper.props().name).toBe('nombre')
    expect(wrapper.props().description).toBe('description')
  })
})
```


Ahora veremos cosas nuevas:

- Hemos creado un objeto llamado *props* el cual tendrá las propiedades del componente `RestaurantCard.vue`.. 

- El componente lo inicializamos fuera de los test, de esta manera, es accesible desde cualquiera de ellos y no tenemos que estar repitiendo código. Además le pasamos por parametro las propiedades. `propsData` la forma que usa jest para inyectar esas propiedades al componente.

- Escribimos el test que comprobará si el componente, renderiza con las propiedades que le hemso pasado.

```js
test('is rendering a restaurant', () => {
  expect(wrapper.props().name).toBe('nombre')
  expect(wrapper.props().description).toBe('description')
})
```


### ⚒️ RECOMENDACIÓN:


### 📚 Referencias y ayudas
- [Jest](https://jestjs.io/)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)