# 📗 Clase 35 Testeando Slots:

`Hero.vue` permite mediante un slot renderizar código html o  poder incrustar nuestros componetes. 


**test/Hero.spec.js**

```js
import { mount } from '@vue/test-utils'
import HeroComponent from '~/components/HeroComponent'

describe('HeroComponent', () => {
  const SLOT_CONTENT = '<p>Titulo de pruebas</p>'
  const wrapper = mount(HeroComponent, {
    slots: {
      banner: SLOT_CONTENT
    }
  })
  test('is render inside slot', () => {
    expect(wrapper.html()).toContain(SLOT_CONTENT)
  })
})
```

Para poder probar el slot usaremos la propiedad `slot` que nos provee el método `mount()`. Creamos una constante llamada `SLOT_CONTENT` y comprobamos que realmente se renderiza en el código html el contenido.


### ⚒️ RECOMENDACIÓN:

Prueba a realizar tu mismo más test unitarios revisando la documentación de Vue-test. Los test es una de las partes más importantes en el desarrollo de software, nos ahorrara mucho tiempo corrigiendo bugs.


### 📚 Referencias y ayudas
- [Jest](https://jestjs.io/)
- [Desarrrolo guiado a pruebas](https://es.wikipedia.org/wiki/Desarrollo_guiado_por_pruebas)
- [vue-test](https://vue-test-utils.vuejs.org/guides/)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)